# Qlib: workflow and architecture

Updated 2026-10-12. Source baseline: `54355232463878d2eebb91fe0ee5fa7fa1f5976c` on `feature/ayu_develop`. See [development commands](development.md) and [validation evidence](validation.md) for the tested environment and current limitations.

## Purpose and features

Provides a quantitative research platform that joins market-data access, feature processing, model training, experiment recording, and portfolio backtesting.

- Calendar and instrument-aware market-data providers
- Expression-based features and Cython rolling kernels
- Dataset handlers and processors
- Model training with recorded artifacts
- Strategies, executors, and risk/return evaluation

## Component architecture

Provider, handler, dataset, and model boundaries separate market storage from training code. Handlers distinguish learning and inference processing so label handling and fitted transformations can be controlled. Workflow recorders hold experiment outputs and allow evaluation to refer to a particular run. The backtest layer consumes strategy decisions and applies exchange/executor mechanics, avoiding an implicit equivalence between a predictive score and executable trading returns.

```mermaid
flowchart LR
    C0["Data providers and expressions"]
    C1["Handlers and processors"]
    C2["Dataset and model"]
    C3["Workflow recorder"]
    C4["Strategy and backtest executor"]
    C0 --> C1 --> C2 --> C3 --> C4
```

The diagram shows responsibility boundaries in the main research or execution path. Concrete entry points and implementation files are linked below.

## Core types

The types below belong to the public or native boundary described by the linked implementation. Arrows describe the dependency or ownership relationship used in the documented workflow. Listed Python methods are present in the linked source; native array types represent the binding boundary.

```mermaid
classDiagram
    class DataHandlerLP {
        +get_all_processors()
        +fit()
        +fit_process_data()
    }
    class DatasetH {
        +config()
        +setup_data()
        +prepare()
    }
    class Model {
        +fit()
        +predict()
    }
    class Recorder {
        +info()
        +set_recorder_name()
        +save_objects()
    }
    class BaseStrategy {
        +executor()
        +trade_calendar()
        +trade_position()
    }
    DatasetH --> DataHandlerLP : fetches segments
    Model --> DatasetH : fits and predicts
    Recorder --> Model : stores run artifacts
    BaseStrategy --> Model : consumes predictions
```

## End-to-end workflow

1. Initialize provider URI and market region.
2. Load and process feature and label expressions.
3. Fit the configured model on dataset segments.
4. Record predictions and model artifacts.
5. Run strategy decisions through the backtest executor.

```mermaid
flowchart TD
    W0["Initialize provider URI and market region"]
    W1["Load and process feature and label expressions"]
    W2["Fit the configured model on dataset segments"]
    W3["Record predictions and model artifacts"]
    W4["Run strategy decisions through the backtest executor"]
    W0 --> W1 --> W2 --> W3 --> W4
    W4 --> R{"Review evidence"}
    R -->|Revise configuration| W0
    R -->|Retain result| A["Store reproducible artifacts"]
```

## Interaction sequence

The sequence follows one unit of work. Results return across the same boundaries that accepted the configuration and data. External I/O and numerical execution have different failure modes and should retain separate evidence.

```mermaid
sequenceDiagram
    actor User as Researcher or operator
    participant C0 as Data providers and expressions
    participant C1 as Handlers and processors
    participant C2 as Dataset and model
    participant C3 as Workflow recorder
    participant C4 as Strategy and backtest executor
    User->>C0: Supply configuration and inputs
    C0->>C1: Load and process feature and label expressions
    C1->>C2: Fit the configured model on dataset segments
    C2->>C3: Record predictions and model artifacts
    C3->>C4: Run strategy decisions through the backtest executor
    C4-->>C3: Results and retained state
    C3-->>C2: Execution or evaluation evidence
    C2-->>C1: Computed outputs
    C1-->>C0: Research or runtime result
    C0-->>User: Inspect outputs and provenance
```

## Data and artifact lifecycle

```mermaid
flowchart LR
    Inputs["Configuration and source data"] --> Runtime["Validated runtime inputs"]
    Runtime --> Work["Dataset and model"]
    Work --> Outputs["Strategy and backtest executor"]
    Outputs --> Review["Metrics, logs, and retained artifacts"]
    Review --> Inputs
```

Inputs include explicit strategy or model settings, data selection, and execution assumptions. Retaining these with outputs makes a rerun reviewable. Temporary environments and caches remain development artifacts, while source-controlled configuration documents intended behavior.

## Execution and failure boundaries

Data fixtures and provider directories are required by integration tests. Redis, MongoDB task management, MLflow storage, and downloadable datasets remain optional service boundaries. Rolling and expanding calculations are compiled C++ extensions generated by Cython, so compiler and NumPy headers are native build requirements.

```mermaid
stateDiagram-v2
    [*] --> Configured
    Configured --> Prepared: Inputs and dependencies available
    Prepared --> Running: Start unit of work
    Running --> Completed: Retain result
    Running --> Failed: Record exception and inputs
    Failed --> Configured: Correct configuration or implementation
    Completed --> [*]
```

This state diagram describes the documented workflow, not a claim that these names are an implementation enum. Failure evidence should identify whether input preparation, external services, native compilation, or application execution failed.

## Development layout

The upstream qlib/ Python and Cython layout is retained. setup.py defines native extensions and pyproject.toml defines metadata and build isolation. Moving the package would also require relocating extension paths, so this maintenance updates uv configuration without mass-moving native sources.

## Source map

| Existing source | Responsibility evidence |
|---|---|
| [qlib/__init__.py](../qlib/__init__.py#L25) | Implementation and module/type documentation, beginning at line 25 |
| [qlib/data/data.py](../qlib/data/data.py#L42) | Implementation and module/type documentation, beginning at line 42 |
| [qlib/data/dataset/handler.py](../qlib/data/dataset/handler.py#L25) | Implementation and module/type documentation, beginning at line 25 |
| [qlib/data/dataset/processor.py](../qlib/data/dataset/processor.py#L18) | Implementation and module/type documentation, beginning at line 18 |
| [qlib/data/dataset/__init__.py](../qlib/data/dataset/__init__.py#L15) | Implementation and module/type documentation, beginning at line 15 |
| [qlib/data/_libs/rolling.pyx](../qlib/data/_libs/rolling.pyx#L193) | Implementation and module/type documentation, beginning at line 193 |
| [qlib/data/_libs/expanding.pyx](../qlib/data/_libs/expanding.pyx#L138) | Implementation and module/type documentation, beginning at line 138 |
| [qlib/model/base.py](../qlib/model/base.py#L10) | Implementation and module/type documentation, beginning at line 10 |
| [qlib/model/trainer.py](../qlib/model/trainer.py#L37) | Implementation and module/type documentation, beginning at line 37 |
| [qlib/workflow/recorder.py](../qlib/workflow/recorder.py#L30) | Implementation and module/type documentation, beginning at line 30 |
| [qlib/backtest/executor.py](../qlib/backtest/executor.py#L22) | Implementation and module/type documentation, beginning at line 22 |
| [qlib/strategy/base.py](../qlib/strategy/base.py#L23) | Implementation and module/type documentation, beginning at line 23 |

The links target files present in this checkout. Follow their imports and adjacent tests when changing a boundary. The validation document distinguishes successful builds, complete test runs, inherited skips, and unresolved prerequisites.
