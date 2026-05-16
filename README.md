# Universal Offline Python Package Downloader

Download Python packages directly from GitHub Actions and use them later without internet access.

Supports:

- Windows
- Linux
- macOS
- Heavy packages like:
  - PyTorch
  - Stable-Baselines3
  - TensorFlow
  - OpenCV
  - MetaTrader5
- Custom package indexes
- Offline installation
- GitHub Releases for huge package collections

---

# Features

- Download packages from PyPI automatically
- Download all dependencies
- Supports Windows, Linux, and macOS
- Works with AI/ML packages
- Supports custom pip indexes
- Saves packages into GitHub Releases
- Offline installation support
- No local setup required

---

# Supported Platforms

| Platform | Runner |
|---|---|
| Windows | `windows-2022` |
| Linux | `ubuntu-22.04` |
| macOS Intel | `macos-13` |
| macOS Apple Silicon / Newer | `macos-14` |

---

# How It Works

1. Fork this repository
2. Run GitHub Action
3. Enter package names
4. GitHub downloads all packages and dependencies
5. Packages are compressed automatically
6. Download archive from Releases
7. Install packages offline later

---

# Fork Repository

Click:

```text
Fork
````

on the top-right of GitHub.

---

# Run Downloader

Open:

```text
Actions
```

Select:

```text
Universal Python Package Downloader
```

Click:

```text
Run workflow
```

---

# Workflow Inputs

## Packages

Example:

```text
django pillow requests
```

AI example:

```text
stable-baselines3 torch torchvision torchaudio
```

Trading example:

```text
MetaTrader5 pandas numpy
```

Version example:

```text
django==5.2.1 pillow==11.2.1
```

---

## Python Version

Choose target Python version:

* 3.13
* 3.12
* 3.11
* 3.10

Always match the Python version of your offline system.

---

## OS

Choose target operating system:

* `windows-2022`
* `ubuntu-22.04`
* `macos-13`
* `macos-14`

---

## Index URL

Optional custom package index.

Example for PyTorch CPU:

```text
https://download.pytorch.org/whl/cpu
```

Leave empty for normal PyPI.

---

## Extra Pip Args

Optional additional pip arguments.

Example:

```text
--prefer-binary
```

---

## Output Mode

### release

Recommended for heavy packages.

Uploads compressed archive to GitHub Releases.

Best for:

* PyTorch
* TensorFlow
* CUDA wheels
* Large AI libraries

### commit

Commits downloaded files directly into repository.

Best for:

* Small packages
* Utilities
* Lightweight libraries

---

# Download Results

After workflow finishes:

Open:

```text
Releases
```

Download generated archive:

Example:

```text
packages-windows-2022-py3.11.tar.gz
```

---

# Extract Packages

Linux/macOS:

```bash
tar -xzf packages-windows-2022-py3.11.tar.gz
```

Windows:

Use:

* 7zip
* WinRAR
* Windows built-in extractor

---

# Offline Installation

## Linux/macOS

```bash
chmod +x install-offline.sh

./install-offline.sh packagehouse/windows-2022/py3.11
```

---

## Windows

```bat
install-offline.bat packagehouse\windows-2022\py3.11
```

---

# Manual Offline Installation

You can also install manually:

```bash
pip install \
  --no-index \
  --find-links=packagehouse/windows-2022/py3.11 \
  -r requirements.txt
```

---

# Examples

---

## Django Backend

### Packages

```text
django
djangorestframework
psycopg2-binary
pillow
celery
redis
gunicorn
```

### Recommended

| Setting | Value        |
| ------- | ------------ |
| Python  | 3.11         |
| OS      | ubuntu-22.04 |
| Output  | release      |

---

## AI / Reinforcement Learning

### Packages

```text
stable-baselines3
torch
torchvision
torchaudio
gymnasium
numpy
pandas
```

### Recommended

| Setting   | Value                                                                        |
| --------- | ---------------------------------------------------------------------------- |
| Python    | 3.11                                                                         |
| OS        | windows-2022                                                                 |
| Index URL | [https://download.pytorch.org/whl/cpu](https://download.pytorch.org/whl/cpu) |
| Output    | release                                                                      |

---

## MetaTrader5

### Packages

```text
MetaTrader5
numpy
pandas
```

### Recommended

| Setting | Value        |
| ------- | ------------ |
| Python  | 3.11         |
| OS      | windows-2022 |
| Output  | release      |

---

# Notes

---

## MetaTrader5

`MetaTrader5` is Windows-focused.

For Linux/macOS you may need:

* Wine
* mt5linux bridge
* remote MetaTrader server

---

## Large Package Support

Heavy packages like:

* PyTorch
* TensorFlow
* CUDA
* OpenCV

may exceed GitHub repository file limits.

This project uses GitHub Releases to avoid those limitations.

---

## macOS Notes

`macos-13` is recommended for older Intel Macs.

`macos-14` is recommended for newer macOS systems.

---

# Security Notice

Only install packages from trusted sources.

Always review package versions before production usage.

---

# License

MIT License

```
```
