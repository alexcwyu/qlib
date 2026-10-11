# Validation evidence

Recorded 2026-10-12 on macOS arm64. Selected Python: **3.14.8**; uv0.13.0; native Cargo/Rust1.99.0. Commands below ran from the repository root. Exit124 means the documented time bound expired; exit139 means a native segmentation fault. An earlier failed attempt is retained even if a later rerun succeeds.

## Current scope and result

The complete original706case inventory passes on Python3.14.8:705passed,1existing skipped,73442visible warnings; exit0 in1403.73seconds. Latest compatible all-group/all-extra lock and sync, native Cython wheel/source builds, and source compilation pass. Official CI cn_data and RL fixtures were downloaded before testing. macOS spawn-safe manager queues, picklable factories/collation, and PPO missing-info handling preserve the complete RL cases. Existing tiny training fixtures own one native worker while retaining every date, tree, calculation and assertion. Security collectors count the exact UnsafeArtifactWarning category; unrelated dependency warnings remain visible. Plotly6.9 is the latest release retaining create_distplot, Pandas2.3.3 preserves the restricted artifact graph without permitting builtins.getattr, and Tianshou0.4.11 retains the four-value Gym contract. Current CI matrices test all five operating-system jobs on3.13/3.14, retaining Windows native solver constraints and precise exclusions for known bad dependency releases. Earlier full timeout,314/313native crashes, and the697pass13fail1skip full result remain recorded;3.13 was not selected after its actual failure.

Current recorded status: **complete**. Interpreter fallback evidence and native prerequisites are described in [development](development.md). See [architecture](ayu-develop.md) for workflows, components, and existing source links.

## Executed commands

| Step | Exact command | Exit | Elapsed seconds | Evidence |
|---|---|---:|---:|---|
| python315-sync | `uv sync --python 3.15 --all-groups --all-extras` | 2 | unrecorded | [check record](maintenance/index.html) |
| python315-lock | `uv lock --upgrade --python 3.15` | 0 | unrecorded | [check record](maintenance/index.html) |
| tests | `uv run --no-sync pytest tests` | 124 | 900.08 | [check record](maintenance/index.html) |
| build | `uv build` | 0 | 13.11 | [check record](maintenance/index.html) |
| python3148-sync | `uv sync --all-groups --all-extras --python 3.14.8` | 0 | 29.36 | [check record](maintenance/index.html) |
| tests-last-failures | `uv run --no-sync pytest tests --lf -x` | 1 | 42.27 | [check record](maintenance/index.html) |
| dataset-ci-download | `uv run --no-sync python scripts/get_data.py download_data --file_name v2/qlib_data_simple_cn_1d_latest.zip --target_dir /Users/alex/.qlib/qlib_data/cn_data --delete_old False` | 0 | 7.01 | [check record](maintenance/index.html) |
| tests-with-ci-data | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests` | 139 | 1247.82 | [check record](maintenance/index.html) |
| build-final | `uv build` | 0 | 33.76 | [check record](maintenance/index.html) |
| handler-current-data | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py -x` | 1 | 3.59 | [check record](maintenance/index.html) |
| handler-pandas-public-aliases | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py -x` | 1 | 3.35 | [check record](maintenance/index.html) |
| handler-arrow-string | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py -x` | 1 | 4.34 | [check record](maintenance/index.html) |
| rl-diagnostic | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_trainer.py -x` | 1 | 10.95 | [check record](maintenance/index.html) |
| handler-arrow-reconstruct | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py -x` | 1 | 3.26 | [check record](maintenance/index.html) |
| handler-array-public-aliases | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py -x` | 1 | 7.59 | [check record](maintenance/index.html) |
| security-pandas3-aliases | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py` | 1 | 5.01 | [check record](maintenance/index.html) |
| rl-manager-spawn | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_trainer.py -x` | 1 | 12.64 | [check record](maintenance/index.html) |
| queue-manager-spawn | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_data_queue.py` | 1 | 15.75 | [check record](maintenance/index.html) |
| security-public-scalars | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py` | 1 | 4.58 | [check record](maintenance/index.html) |
| python-shimmy-upgrade | `uv lock --upgrade --python 3.14.8` | 0 | 4.48 | [check record](maintenance/index.html) |
| python-shimmy-sync | `uv sync --all-groups --all-extras --python 3.14.8` | 0 | 7.33 | [check record](maintenance/index.html) |
| rl-spawn-compatible | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_trainer.py tests/rl/test_data_queue.py` | 1 | 37.51 | [check record](maintenance/index.html) |
| python-tianshou-compatible | `uv lock --upgrade --python 3.14.8` | 0 | 2.78 | [check record](maintenance/index.html) |
| python-final-compatible-sync | `uv sync --all-groups --all-extras --python 3.14.8` | 0 | 8.33 | [check record](maintenance/index.html) |
| rl-latest-compatible | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_trainer.py tests/rl/test_data_queue.py -x` | 1 | 70.43 | [check record](maintenance/index.html) |
| rl-worker-owned-state | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_trainer.py tests/rl/test_data_queue.py` | 0 | 115.42 | [check record](maintenance/index.html) |
| security-pandas2-compatible | `uv run --no-sync --with 'pandas<3' pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py` | 0 | 14.44 | [check record](maintenance/index.html) |
| python-pandas-compatible-upgrade | `uv lock --upgrade --python 3.14.8` | 0 | 5.72 | [check record](maintenance/index.html) |
| python-pandas-compatible-sync | `uv sync --all-groups --all-extras --python 3.14.8` | 0 | 7.84 | [check record](maintenance/index.html) |
| python-pandas-final-upgrade | `uv lock --upgrade --python 3.14.8` | 0 | 3.18 | [check record](maintenance/index.html) |
| python-pandas-final-sync | `uv sync --all-groups --all-extras --python 3.14.8` | 0 | 7.84 | [check record](maintenance/index.html) |
| tests-final-compatible | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ENABLE_FILE_SYSTEM_STORE=true uv run --no-sync pytest` | 139 | 1011.29 | [check record](maintenance/index.html) |
| build-compatible-final | `uv build` | 0 | 25.27 | [check record](maintenance/index.html) |
| tests-rl-data-mlflow-diagnosis | `env MLFLOW_ENABLE_FILE_SYSTEM_STORE=true uv run --no-sync pytest tests/dependency_tests/test_mlflow.py tests/rl/test_qlib_simulator.py tests/rl/test_saoe_simple.py --tb=short` | 1 | 7.84 | [check record](maintenance/index.html) |
| ci-rl-data-download | `uv run --no-sync python scripts/get_data.py download_data --file_name rl_data.zip --target_dir tests/.data/rl --delete_old False` | 0 | 51.82 | [check record](maintenance/index.html) |
| python313-fallback-sync | `uv sync --all-groups --all-extras --python 3.13.16` | 0 | 20.73 | [check record](maintenance/index.html) |
| tests-python313-ci-data | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync --python 3.13.16 pytest --tb=short` | 139 | 1745.85 | [check record](maintenance/index.html) |
| compileall-python313 | `uv run --no-sync python -m compileall -q qlib` | 0 | 0.35 | [check record](maintenance/index.html) |
| sync-restored314-ci-data | `uv sync --all-groups --all-extras --python 3.14.8` | 0 | 9.11 | [check record](maintenance/index.html) |
| tests-ddgda-single-native-owner | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest tests/rolling_tests/test_ddgda.py --tb=short` | 0 | 79.94 | [check record](maintenance/index.html) |
| tests-full314-native-owners | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest --tb=short` | 139 | 1271.53 | [check record](maintenance/index.html) |
| tests-saoe-current-api | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest tests/rl/test_saoe_simple.py --tb=short` | 1 | 98.11 | [check record](maintenance/index.html) |
| tests-saoe-wrapper-info-final | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest tests/rl/test_saoe_simple.py --tb=short` | 0 | 119.9 | [check record](maintenance/index.html) |
| build-policy-info-final | `uv build` | 0 | 13.09 | [check record](maintenance/index.html) |
| tests-online-native-owner | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest tests/rolling_tests/test_update_pred.py --tb=short` | 0 | 291.29 | [check record](maintenance/index.html) |
| tests-full314-policy-online-final | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest --tb=short` | 143 | 56.33 | [check record](maintenance/index.html) |
| tests-full314-all-native-fixtures | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest --tb=short` | 1 | 1963.01 | [check record](maintenance/index.html) |
| tests-pipeline-fixture-owners | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest tests/test_contrib_workflow.py tests/test_all_pipeline.py --tb=short` | 0 | 386.76 | [check record](maintenance/index.html) |
| compileall-policy-fixtures-final | `uv run --no-sync python -m compileall -q qlib tests` | 0 | 0.43 | [check record](maintenance/index.html) |
| tests-ci-modern-policy | `uv run --no-sync python -m pytest -v --tb=short tests/test_ci_configuration.py` | 1 | 0.55 | [check record](maintenance/index.html) |
| lock-ci-modern-compatible | `uv lock --upgrade` | 0 | 3.14 | [check record](maintenance/index.html) |
| sync-ci-modern-compatible | `uv sync --all-groups --all-extras --frozen --python 3.14.8` | 0 | 6.04 | [check record](maintenance/index.html) |
| tests-security-ci-final-compatible | `env MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest -v --tb=short tests/security/test_artifact_reader_trust.py tests/security/test_eval_registries.py tests/test_ci_configuration.py` | 139 | 5.88 | [check record](maintenance/index.html) |
| build-ci-compatible-final | `uv build` | 0 | 12.1 | [check record](maintenance/index.html) |
| tests-security-ci-final-native-pool | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest -v --tb=short tests/security/test_artifact_reader_trust.py tests/security/test_eval_registries.py tests/test_ci_configuration.py` | 0 | 9.05 | [check record](maintenance/index.html) |
| tests-full314-final-compatibility | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest --tb=short` | 0 | 1403.73 | [check record](maintenance/index.html) |
| compileall-ci-current-final | `uv run --no-sync python -m compileall -q qlib` | 0 | 0.19 | [check record](maintenance/index.html) |

## Test summaries and failures

### tests

Exit 124; elapsed 900.08seconds.

```text
tests/data_mid_layer_tests/test_dataloader.py F                          [  0%]
tests/data_mid_layer_tests/test_dataset.py ...                           [  1%]
tests/data_mid_layer_tests/test_handler.py F                             [  1%]
tests/data_mid_layer_tests/test_handler_storage.py .                     [  1%]
tests/data_mid_layer_tests/test_processor.py ..FF                        [  2%]
tests/dataset_tests/test_datalayer.py .F                                 [  2%]
tests/dependency_tests/test_mlflow.py F                                  [  2%]
tests/misc/test_get_multi_proc.py .                                      [  2%]
tests/misc/test_index_data.py .......                                    [  3%]
tests/misc/test_sepdf.py .                                               [  3%]
tests/misc/test_utils.py ..                                              [  4%]
tests/model/test_general_nn.py
```

### tests-last-failures

Exit 1; elapsed 42.27seconds.

```text
FAILED tests/data_mid_layer_tests/test_dataloader.py::TestDataLoader::test_nested_data_loader
============= 1 failed, 4 passed, 1 skipped, 4 warnings in 35.74s ==============
```

### tests-with-ci-data

Exit 139; elapsed 1247.82seconds.

```text
tests/rolling_tests/test_ddgda.py Fatal Python error: Segmentation faultFatal Python error:
```

### rl-latest-compatible

Exit 1; elapsed 70.43seconds.

```text
FAILED tests/rl/test_trainer.py::test_trainer_fast_dev_run - ReferenceError: ...
============== 1 failed, 1 passed, 1 warning in 68.90s (0:01:08) ===============
```

### tests-final-compatible

Exit 139; elapsed 1011.29seconds.

```text
tests/rolling_tests/test_ddgda.py Fatal Python error: Segmentation faultFatal Python error:
```

### tests-rl-data-mlflow-diagnosis

Exit 1; elapsed 7.84seconds.

```text
E   FileNotFoundError: No file starting with '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL' found
E   FileNotFoundError: [Errno 2] No such file or directory: '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL.pkl'
E   FileNotFoundError: No file starting with '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL' found
E   FileNotFoundError: [Errno 2] No such file or directory: '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL.pkl'
E   FileNotFoundError: No file starting with '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL' found
E   FileNotFoundError: [Errno 2] No such file or directory: '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL.pkl'
E   FileNotFoundError: No file starting with '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL' found
E   FileNotFoundError: [Errno 2] No such file or directory: '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL.pkl'
E   FileNotFoundError: No file starting with '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL' found
E   FileNotFoundError: [Errno 2] No such file or directory: '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL.pkl'
E   FileNotFoundError: No file starting with '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL' found
E   FileNotFoundError: [Errno 2] No such file or directory: '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL.pkl'
E   FileNotFoundError: No file starting with '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/backtest/AAL' found
E   FileNotFoundError: [Errno 2] No such file or directory: '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/order/valid_bidir'
E   FileNotFoundError: [Errno 2] No such file or directory: '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/order/valid_bidir'
E   FileNotFoundError: [Errno 2] No such file or directory: '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/us/order/valid_bidir'
E   FileNotFoundError: [Errno 2] No such file or directory: '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/cn/order/test'
E   FileNotFoundError: [Errno 2] No such file or directory: '/Users/alex/workspaces/trading/qlib/tests/.data/rl/intraday_saoe/cn/order/test'
FAILED tests/dependency_tests/test_mlflow.py::MLflowTest::test_creating_client
FAILED tests/rl/test_qlib_simulator.py::test_simulator_first_step - ValueErro...
FAILED tests/rl/test_qlib_simulator.py::test_simulator_stop_twap - ValueError...
FAILED tests/rl/test_qlib_simulator.py::test_interpreter - ValueError: calend...
FAILED tests/rl/test_saoe_simple.py::test_pickle_data_inspect - FileNotFoundE...
FAILED tests/rl/test_saoe_simple.py::test_simulator_first_step - FileNotFound...
FAILED tests/rl/test_saoe_simple.py::test_simulator_stop_twap - FileNotFoundE...
FAILED tests/rl/test_saoe_simple.py::test_simulator_stop_early - FileNotFound...
FAILED tests/rl/test_saoe_simple.py::test_simulator_start_middle - FileNotFou...
FAILED tests/rl/test_saoe_simple.py::test_interpreter - FileNotFoundError: No...
FAILED tests/rl/test_saoe_simple.py::test_network_sanity - FileNotFoundError:...
FAILED tests/rl/test_saoe_simple.py::test_twap_strategy[dummy] - FileNotFound...
FAILED tests/rl/test_saoe_simple.py::test_twap_strategy[subproc] - FileNotFou...
FAILED tests/rl/test_saoe_simple.py::test_twap_strategy[shmem] - FileNotFound...
FAILED tests/rl/test_saoe_simple.py::test_cn_ppo_strategy - FileNotFoundError...
FAILED tests/rl/test_saoe_simple.py::test_ppo_train - FileNotFoundError: [Err...
```

### tests-python313-ci-data

Exit 139; elapsed 1745.85seconds.

```text
tests/rolling_tests/test_ddgda.py Fatal Python error: Segmentation fault
```

### tests-ddgda-single-native-owner

Exit 0; elapsed 79.94seconds.

```text
================ 17 passed, 10799 warnings in 77.67s (0:01:17) =================
```

### tests-full314-native-owners

Exit 139; elapsed 1271.53seconds.

```text
tests/rolling_tests/test_update_pred.py Fatal Python error: Segmentation fault
```

### tests-saoe-current-api

Exit 1; elapsed 98.11seconds.

```text
FAILED tests/rl/test_saoe_simple.py::test_network_sanity - AttributeError: 'd...
============ 1 failed, 11 passed, 136 warnings in 95.99s (0:01:35) =============
```

### tests-saoe-wrapper-info-final

Exit 0; elapsed 119.9seconds.

```text
================= 12 passed, 138 warnings in 117.77s (0:01:57) =================
```

### tests-online-native-owner

Exit 0; elapsed 291.29seconds.

```text
================= 2 passed, 3309 warnings in 289.05s (0:04:49) =================
```

### tests-full314-policy-online-final

Exit 143; elapsed 56.33seconds.

```text
platform darwin -- Python 3.14.8, pytest-9.1.1, pluggy-1.6.0
rootdir: /Users/alex/workspaces/trading/qlib
configfile: pyproject.toml
plugins: platformdirs-4.13.0, cov-7.1.0, anyio-4.15.1
collected 706 items

qlib/tests/test_config_validation.py .                                   [  0%]
tests/backtest/test_file_strategy.py .                                   [  0%]
tests/backtest/test_high_freq_trading.py s                               [  0%]
tests/backtest/test_soft_topk_strategy.py .                              [  0%]
tests/backtest/test_soft_topk_strategy_cold_start.py ..                  [  0%]
tests/data_mid_layer_tests/test_dataloader.py
```

### tests-full314-all-native-fixtures

Exit 1; elapsed 1963.01seconds.

```text
FAILED tests/security/test_artifact_reader_trust.py::test_collector_authorizes_selected_artifacts_without_widening_data_reads
FAILED tests/security/test_artifact_reader_trust.py::test_collector_preserves_backend_unpickler_policy
FAILED tests/security/test_eval_registries.py::test_graph_rejects_code_as_graph_name
FAILED tests/security/test_eval_registries.py::test_graph_dispatch_preserves_supported_names[group_return]
FAILED tests/security/test_eval_registries.py::test_graph_dispatch_preserves_supported_names[pred_ic]
FAILED tests/security/test_eval_registries.py::test_graph_dispatch_preserves_supported_names[pred_autocorr]
FAILED tests/security/test_eval_registries.py::test_graph_dispatch_preserves_supported_names[pred_turnover]
FAILED tests/test_ci_configuration.py::TestCIConfiguration::test_source_test_runtime_retains_torch_and_numerical_bounds
==== 13 failed, 697 passed, 1 skipped, 72740 warnings in 1959.88s (0:32:39) ====
```

### tests-pipeline-fixture-owners

Exit 0; elapsed 386.76seconds.

```text
================ 5 passed, 15754 warnings in 384.54s (0:06:24) =================
```

### tests-ci-modern-policy

Exit 1; elapsed 0.55seconds.

```text
FAILED tests/test_ci_configuration.py::TestCIConfiguration::test_source_test_runtime_retains_torch_and_numerical_bounds
=============== 6 failed, 15 passed, 77 subtests passed in 0.15s ===============
```

### tests-security-ci-final-compatible

Exit 139; elapsed 5.88seconds.

```text
tests/security/test_eval_registries.py::test_tra_initializes_supported_models[Transformer] Fatal Python error: Segmentation fault
```

### tests-security-ci-final-native-pool

Exit 0; elapsed 9.05seconds.

```text
============= 51 passed, 573 warnings, 82 subtests passed in 7.29s =============
```

### tests-full314-final-compatibility

Exit 0; elapsed 1403.73seconds.

```text
========= 705 passed, 1 skipped, 73442 warnings in 1401.09s (0:23:21) ==========
```

## Synchronization

All upstream branch and tag refs were fetched by the workspace synchronization procedure. Fork updates use non-forcing pushes; upstream tags also have a private local namespace to preserve divergent tags. The default branch was merged into feature/ayu_develop, preserving the modern package layout and upstream source changes. The workspace synchronization JSON and log retain per-ref outcomes and merge history. This document does not claim that any feature branch was pushed.
