# Offline Python Package Downloader

Download and store Python packages directly in your GitHub repository using GitHub Actions, then install them later without internet access.

Perfect for:

* Restricted networks
* Offline servers
* Air-gapped environments
* Slow or unstable internet
* Building your own Python package archive

---

# Features

* Download packages directly from PyPI using GitHub Actions
* Save packages permanently in your repository
* Install packages later with `pip` completely offline
* Supports custom Python versions
* Automatically downloads dependencies
* No local setup required

---

# How It Works

1. Fork this repository
2. Run the GitHub Action
3. Enter package names
4. GitHub downloads all required wheels
5. Packages are saved into the `packages/` folder
6. Download the repo and install offline

---

# Fork This Repository

Click the **Fork** button on the top-right of this repository.

Or visit:

```text
https://github.com/YOUR_USERNAME/YOUR_REPO/fork
```

---

# How To Download Packages

## 1. Open Actions

Go to:

```text
Actions
```

Then select:

```text
Download Python Packages
```

---

## 2. Run Workflow

Click:

```text
Run workflow
```

You will see inputs:

### Packages

Example:

```text
django djangorestframework pillow celery redis
```

You can also specify versions:

```text
django==5.2.1 pillow==11.2.1
```

### Python Version

Choose your target Python version:

* 3.13
* 3.12
* 3.11
* 3.10

---

# Downloaded Files

After workflow finishes successfully, packages will be stored in:

```text
packages/
```

Example:

```text
packages/
├── Django-5.2.1-py3-none-any.whl
├── pillow-11.2.1-cp313-cp313-manylinux.whl
├── redis-6.0.0-py3-none-any.whl
└── ...
```

---

# How To Use Offline

## 1. Download Repository

Clone or download ZIP:

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
```

Or:

```text
Code → Download ZIP
```

---

## 2. Install Without Internet

Move the repository to your offline machine.

Then run:

```bash
pip install --no-index --find-links=packages -r requirements.txt
```

Or install a single package:

```bash
pip install --no-index --find-links=packages django
```

---

# Important Notes

## OS Compatibility

This workflow currently uses:

```text
ubuntu-latest
```

So downloaded wheels are usually Linux-compatible.

If you need:

* macOS packages
* Windows packages

Create separate workflows using:

```yaml
runs-on: macos-latest
```

or

```yaml
runs-on: windows-latest
```

---

## Python Version Compatibility

Always download packages using the same Python version as your offline machine.

Example:

If offline system uses:

```bash
Python 3.13
```

Then select:

```text
3.13
```

inside workflow inputs.

---

# Example Offline Installation

```bash
pip install \
  --no-index \
  --find-links=packages \
  django djangorestframework pillow
```

---

# Advanced Usage

## Download Using requirements.txt

You can modify workflow to use:

```text
requirements.txt
```

instead of manual input.

---

## Store Huge Package Collections

You can build your own offline mirror containing:

* AI libraries
* Django stack
* Data science tools
* DevOps packages
* Trading libraries
* CUDA-compatible wheels

---

# Example Collections

## Django Backend

```text
django
djangorestframework
psycopg2-binary
celery
redis
gunicorn
pillow
```

## AI / ML

```text
numpy
pandas
scikit-learn
torch
tensorflow
opencv-python
```

## Trading

```text
MetaTrader5
ccxt
ta
numpy
pandas
```

---

# Security Notice

Only download and install packages from trusted sources.

Always review package versions before deploying to production systems.

---

# License

MIT License
