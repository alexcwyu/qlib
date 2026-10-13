# qlib: portable verification records

<!-- current-documentation-provenance -->
Documentation reviewed: 2026-10-13 · Git source base: `2d1a897ae444ba6f30be4b867efb56faea83e2e6` · [Current architecture and feature guide](../ayu-develop.md).
Historical execution commands/results below retain their original dates and scope; this metadata update is not a new application test run.
<!-- /current-documentation-provenance -->


Full raw logs are retained in the workspace maintenance evidence, not distributed here. Hashes identify those original logs. A successful build or selected test subset does not imply a full test-suite pass. Commands containing <workspace> describe the original execution environment.

[Machine-readable records](verification.json) · [Repository validation summary](../validation.md)

## Executed commands

| Check | Exit | Duration | Command | Outcomes |
| --- | ---: | ---: | --- | --- |
| build | 0 | unrecordeds | `uv build` | Successfully built dist/pyqlib-0.9.9.dev0.tar.gz<br>Successfully built dist/pyqlib-0.9.9.dev0-cp314-cp314-macosx_12_0_arm64.whl |
| build-ci-compatible-final | 0 | unrecordeds | `uv build` | Successfully built dist/pyqlib-0.9.9.dev0.tar.gz<br>Successfully built dist/pyqlib-0.9.9.dev0-cp314-cp314-macosx_11_0_arm64.whl |
| build-compatible-final | 0 | unrecordeds | `uv build` | Successfully built dist/pyqlib-0.9.9.dev0.tar.gz<br>Successfully built dist/pyqlib-0.9.9.dev0-cp314-cp314-macosx_11_0_arm64.whl |
| build-final | 0 | unrecordeds | `uv build` | Successfully built dist/pyqlib-0.9.9.dev0.tar.gz<br>Successfully built dist/pyqlib-0.9.9.dev0-cp314-cp314-macosx_11_0_arm64.whl |
| build-policy-info-final | 0 | unrecordeds | `uv build` | Successfully built dist/pyqlib-0.9.9.dev0.tar.gz<br>Successfully built dist/pyqlib-0.9.9.dev0-cp314-cp314-macosx_11_0_arm64.whl |
| ci-rl-data-download | 0 | unrecordeds | `uv run --no-sync python scripts/get_data.py download_data --file_name rl_data.zip --target_dir tests/.data/rl --delete_old False` | See exit status; no test-count assertion. |
| compileall-ci-current-final | 0 | unrecordeds | `uv run --no-sync python -m compileall -q qlib` | See exit status; no test-count assertion. |
| compileall-policy-fixtures-final | 0 | unrecordeds | `uv run --no-sync python -m compileall -q qlib tests` | See exit status; no test-count assertion. |
| compileall-python313 | 0 | unrecordeds | `uv run --no-sync python -m compileall -q qlib` | See exit status; no test-count assertion. |
| dataset-ci-download | 0 | unrecordeds | `uv run --no-sync python scripts/get_data.py download_data --file_name v2/qlib_data_simple_cn_1d_latest.zip --target_dir /Users/alex/.qlib/qlib_data/cn_data --delete_old False` | See exit status; no test-count assertion. |
| handler-array-public-aliases | 1 | unrecordeds | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py -x` | ========================= 1 failed, 64 passed in 5.90s ========================= |
| handler-arrow-reconstruct | 1 | unrecordeds | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py -x` | See exit status; no test-count assertion. |
| handler-arrow-string | 1 | unrecordeds | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py -x` | See exit status; no test-count assertion. |
| handler-current-data | 1 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py -x` | See exit status; no test-count assertion. |
| handler-pandas-public-aliases | 1 | unrecordeds | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py -x` | See exit status; no test-count assertion. |
| lock-ci-modern-compatible | 0 | unrecordeds | `uv lock --upgrade` | See exit status; no test-count assertion. |
| python-final-compatible-sync | 0 | unrecordeds | `uv sync --all-groups --all-extras --python 3.14.8` | See exit status; no test-count assertion. |
| python-pandas-compatible-sync | 0 | unrecordeds | `uv sync --all-groups --all-extras --python 3.14.8` | See exit status; no test-count assertion. |
| python-pandas-compatible-upgrade | 0 | unrecordeds | `uv lock --upgrade --python 3.14.8` | See exit status; no test-count assertion. |
| python-pandas-final-sync | 0 | unrecordeds | `uv sync --all-groups --all-extras --python 3.14.8` | See exit status; no test-count assertion. |
| python-pandas-final-upgrade | 0 | unrecordeds | `uv lock --upgrade --python 3.14.8` | See exit status; no test-count assertion. |
| python-shimmy-sync | 0 | unrecordeds | `uv sync --all-groups --all-extras --python 3.14.8` | See exit status; no test-count assertion. |
| python-shimmy-upgrade | 0 | unrecordeds | `uv lock --upgrade --python 3.14.8` | See exit status; no test-count assertion. |
| python-tianshou-compatible | 0 | unrecordeds | `uv lock --upgrade --python 3.14.8` | See exit status; no test-count assertion. |
| python313-fallback-sync | 0 | unrecordeds | `uv sync --all-groups --all-extras --python 3.13.16` | See exit status; no test-count assertion. |
| python3148-sync | 0 | unrecordeds | `uv sync --all-groups --all-extras --python 3.14.8` | See exit status; no test-count assertion. |
| python315-lock | 0 | unrecordeds | `uv lock --upgrade --python 3.15` | See exit status; no test-count assertion. |
| python315-sync | 2 | unrecordeds | `uv sync --python 3.15 --all-groups --all-extras` | See exit status; no test-count assertion. |
| queue-manager-spawn | 1 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_data_queue.py` | =================== 3 failed, 1 passed, 3 warnings in 14.60s =================== |
| rl-diagnostic | 1 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_trainer.py -x` | See exit status; no test-count assertion. |
| rl-latest-compatible | 1 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_trainer.py tests/rl/test_data_queue.py -x` | ============== 1 failed, 1 passed, 1 warning in 68.90s (0:01:08) =============== |
| rl-manager-spawn | 1 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_trainer.py -x` | See exit status; no test-count assertion. |
| rl-spawn-compatible | 1 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_trainer.py tests/rl/test_data_queue.py` | =================== 4 failed, 4 passed, 3 warnings in 35.96s =================== |
| rl-worker-owned-state | 0 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests/rl/test_trainer.py tests/rl/test_data_queue.py` | =================== 8 passed, 1 warning in 113.71s (0:01:53) =================== |
| security-pandas2-compatible | 0 | unrecordeds | `uv run --no-sync --with pandas<3 pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py` | ======================= 139 passed, 4 warnings in 9.27s ======================== |
| security-pandas3-aliases | 1 | unrecordeds | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py` | ======================== 14 failed, 125 passed in 3.69s ======================== |
| security-public-scalars | 1 | unrecordeds | `uv run --no-sync pytest tests/data_mid_layer_tests/test_handler.py tests/security/test_pickle_utils.py` | ======================== 4 failed, 135 passed in 3.19s ========================= |
| sync-ci-modern-compatible | 0 | unrecordeds | `uv sync --all-groups --all-extras --frozen --python 3.14.8` | See exit status; no test-count assertion. |
| sync-restored314-ci-data | 0 | unrecordeds | `uv sync --all-groups --all-extras --python 3.14.8` | See exit status; no test-count assertion. |
| tests | 124 | unrecordeds | `uv run --no-sync pytest tests` | See exit status; no test-count assertion. |
| tests-ci-modern-policy | 1 | unrecordeds | `uv run --no-sync python -m pytest -v --tb=short tests/test_ci_configuration.py` | =============== 6 failed, 15 passed, 77 subtests passed in 0.15s =============== |
| tests-ddgda-single-native-owner | 0 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest tests/rolling_tests/test_ddgda.py --tb=short` | ================ 17 passed, 10799 warnings in 77.67s (0:01:17) ================= |
| tests-final-compatible | 139 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ENABLE_FILE_SYSTEM_STORE=true uv run --no-sync pytest` | See exit status; no test-count assertion. |
| tests-full314-all-native-fixtures | 1 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest --tb=short` | ==== 13 failed, 697 passed, 1 skipped, 72740 warnings in 1959.88s (0:32:39) ==== |
| tests-full314-final-compatibility | 0 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest --tb=short` | ========= 705 passed, 1 skipped, 73442 warnings in 1401.09s (0:23:21) ========== |
| tests-full314-native-owners | 139 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest --tb=short` | See exit status; no test-count assertion. |
| tests-full314-policy-online-final | 143 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest --tb=short` | See exit status; no test-count assertion. |
| tests-last-failures | 1 | unrecordeds | `uv run --no-sync pytest tests --lf -x` | ============= 1 failed, 4 passed, 1 skipped, 4 warnings in 35.74s ============== |
| tests-online-native-owner | 0 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest tests/rolling_tests/test_update_pred.py --tb=short` | ================= 2 passed, 3309 warnings in 289.05s (0:04:49) ================= |
| tests-pipeline-fixture-owners | 0 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest tests/test_contrib_workflow.py tests/test_all_pipeline.py --tb=short` | ================ 5 passed, 15754 warnings in 384.54s (0:06:24) ================= |
| tests-python313-ci-data | 139 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync --python 3.13.16 pytest --tb=short` | See exit status; no test-count assertion. |
| tests-rl-data-mlflow-diagnosis | 1 | unrecordeds | `env MLFLOW_ENABLE_FILE_SYSTEM_STORE=true uv run --no-sync pytest tests/dependency_tests/test_mlflow.py tests/rl/test_qlib_simulator.py tests/rl/test_saoe_simple.py --tb=short` | See exit status; no test-count assertion. |
| tests-saoe-current-api | 1 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest tests/rl/test_saoe_simple.py --tb=short` | ============ 1 failed, 11 passed, 136 warnings in 95.99s (0:01:35) ============= |
| tests-saoe-wrapper-info-final | 0 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest tests/rl/test_saoe_simple.py --tb=short` | ================= 12 passed, 138 warnings in 117.77s (0:01:57) ================= |
| tests-security-ci-final-compatible | 139 | unrecordeds | `env MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest -v --tb=short tests/security/test_artifact_reader_trust.py tests/security/test_eval_registries.py tests/test_ci_configuration.py` | See exit status; no test-count assertion. |
| tests-security-ci-final-native-pool | 0 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 MLFLOW_ALLOW_FILE_STORE=true uv run --no-sync python -m pytest -v --tb=short tests/security/test_artifact_reader_trust.py tests/security/test_eval_registries.py tests/test_ci_configuration.py` | ============= 51 passed, 573 warnings, 82 subtests passed in 7.29s ============= |
| tests-with-ci-data | 139 | unrecordeds | `env OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 VECLIB_MAXIMUM_THREADS=1 uv run --no-sync pytest tests` | See exit status; no test-count assertion. |
