## Reprod

### Install package
```shell
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install . # important : not using editable mode here !
```

### test with pytest 7.2
```shell
python -m pip install 'pytest==7.2.0' 
pytest
pytest --doctest-modules
```
(everything should be ok)

### test with pytest dev

```shell
python -m pip install git+https://github.com/pytest-dev/pytest@4797dea 
pytest # should be ok
pytest --doctest-modules # error !
```
```
============================================ test session starts =============================================
platform darwin -- Python 3.11.4, pytest-8.0.0.dev144+g4797deab, pluggy-1.2.0
rootdir: /Users/robcleme/dev/pytest_bug_reprod
collected 1 item / 1 error                                                                                   

=================================================== ERRORS ===================================================
______________________________________ ERROR collecting src/pkg/mod.py _______________________________________
.venv/lib/python3.11/site-packages/_pytest/runner.py:340: in from_call
    result: Optional[TResult] = func()
.venv/lib/python3.11/site-packages/_pytest/runner.py:371: in <lambda>
    call = CallInfo.from_call(lambda: list(collector.collect()), "collect")
.venv/lib/python3.11/site-packages/_pytest/doctest.py:547: in collect
    module = import_path(
.venv/lib/python3.11/site-packages/_pytest/pathlib.py:590: in import_path
    raise ImportPathMismatchError(module_name, module_file, path)
E   _pytest.pathlib.ImportPathMismatchError: ('pkg.mod', '/Users/robcleme/dev/pytest_bug_reprod/.venv/lib/python3.11/site-packages/pkg/mod.py', PosixPath('/Users/robcleme/dev/pytest_bug_reprod/src/pkg/mod.py'))
========================================== short test summary info ===========================================
ERROR src/pkg/mod.py - _pytest.pathlib.ImportPathMismatchError: ('pkg.mod', '/Users/robcleme/dev/pytest_bug_reprod/.venv/lib/pyt...
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! Interrupted: 1 error during collection !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
============================================== 1 error in 0.13s ==============================================
```
