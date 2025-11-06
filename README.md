# CFFI-MemoryLeak

## Before launch

### Configure Python for debugging

1) Replace "NAME" before running

```bash
cd /tmp/
wget https://www.python.org/ftp/python/3.12.12/Python-3.12.12.tgz
tar xzf Python-3.12.12.tgz
cd Python-3.12.12

./configure --prefix=NAME --enable-pystats --without-pymalloc --with-pydebug --with-address-sanitizer --with-undefined-behavior-sanitizer
make -j $(nproc)
make altinstall
sudo rm /tmp/Python-3.12.12.tgz

NAME/bin/python3.12 -m pip install --upgrade pip setuptools wheel
```

2) Install CFFI

```bash
NAME/bin/python3.12 -m pip install cffi
```

### Clone the repository

```bash
git clone https://github.com/K0tB0ris/CFFI-MemoryLeak.git
cd CFFI-MemoryLeak
```

### Run experiments
1) Navigate to the `src` directory:

```bash
cd src
```

2) Select one of the CFFI usage modes suggested in the Overview and go to the corresponding directory.

3) First, run `build.py` if it exists, and then run `test.py`.

```bash
NAME/bin/python3.12 build.py
NAME/bin/python3.12 test.py
```

4) AddressSanitizer shows memory leaks for CFFI in all API modes.
