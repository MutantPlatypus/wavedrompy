# Testing
There are several ways to test `wavedrompy` locally.  Note that these
tests require `cairosvg`, so `conda` (option 2.3) is highly
recommended for testing in a Windows environment.

## 1. With `pytest`
Ensure the environment has `git`, `node`, and `npm`.

Then, using any single Python runtime:
```sh
pip install pytest
pip install -e .[test]
pytest
```
## 2. With `tox`
For both flavors of `tox`, it is possible to do testing in a reduced
number of environments with the `-e` parameter.  For example, the
following command will reduce test time significantly by testing only
on Python 3.7:
```sh
tox -e p37
```

It is still recommended to locally test in as many environments as
possible before pushing a commit to GitHub for testing on the CI
service.

### 2.1 Vanilla `tox`
`tox` will use `virtualenv` to create test environments, and run on
any Python 

1. Ensure the environment has `git`, `node`, and `npm`.

2. Install `tox`
```sh
pip install tox
```

3. Run `tox`
```sh
tox -c ./tests/tox_no_conda.ini
```

## 2.2 With `tox-conda`
`tox` will use `conda` to create its own environment and all of the
Python test environments

1. Ensure your environment has Miniconda or Anaconda.
https://docs.conda.io/en/latest/miniconda.html

2. 
```sh
conda create -n wavedrompy-test -c conda-forge tox-conda
```

2. Run `tox`
```sh
tox
```