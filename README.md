# Setup private repo instructions

## setup venv

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install poetry
```

## setup private repo

```bash
wget -P repository/pybind11 https://files.pythonhosted.org/packages/bb/f9/a526ea001ecadd48d90ed7a61038b5ba732136d76b60357d23dc37521c58/pybind11-2.10.4.tar.gz
wget -P repository/pybind11 https://files.pythonhosted.org/packages/52/ed/68e989fdac8f352cb6d506fac111ba1e1b74c0ef3660fadeeeeb765bc03c/pybind11-2.10.4-py3-none-any.whl
wget -P repository/setuptools https://files.pythonhosted.org/packages/19/20/d8dd9d8becaf3e2d6fdc17cc41870d5ada5ceda518996cf5968c2ca71bd8/setuptools-68.1.2.tar.gz
wget -P repository/wheel https://files.pythonhosted.org/packages/a4/99/78c4f3bd50619d772168bec6a0f34379b02c19c9cced0ed833ecd021fd0d/wheel-0.41.2.tar.gz
wget -P repository/poetry-core https://files.pythonhosted.org/packages/cb/1c/af7f886e723b2dfbaea9b8a739153f227b386dd856cf956f9fd0ed0a502b/poetry_core-1.7.0.tar.gz
python3 -m http.server 9000
```

## Disallow access to pypi

```bash
echo 127.0.0.1 pypi.org | sudo tee -a /etc/hosts
# later to remove: sudo sed -i '/pypi.org/d' /etc/hosts
```

## Try install package with poetry

```bash
export PIP_INDEX_URL=http://127.0.0.1:9000  # this doesn't have any effect due to poetry invoking pip with --isolate
poetry install -vvv
```

