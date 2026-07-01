# Computational Control 2026 Rocket Lander Project

A Box2D Gymnasium environment which simulates a Falcon 9 ocean barge landing. Various disturbances can occur: wind, moving barge, thruster failure, reduction of the nozzle angle range and mass mismatch.

The control problem is solved by using MPC + Disturbance Estimation (Luenberger Observer) + Nested LQR - whose main focus is to keep the rocket upright.

Modified by Dylan Vogel, Gerasimos Maltezos, and Benjamin Stadler for the 2023 and 2026 Computation Control course at ETH Zurich  
Original environment created by Reuben Ferrante (https://github.com/arex18/rocket-lander).

## Installation Guide

This project uses **Python 3.13** and **Poetry** for dependency management and requires a few **system-level dependencies**.

This guide walks you through the installation step-by-step for **Linux** using **Ubuntu/Debian**.


### 1. Install System Dependencies

First, we install python 3.13 and further system dependencies via the Debian package manager `apt`.

```bash
sudo apt update
sudo apt install -y python3.13-venv ffmpeg xvfb swig pipx
```

Second, we install `poetry` using `pipx` to keep it isolated from system Python. Check if you have poetry already installed by running
```bash
poetry --version
```

If not, install `poetry` as below:

```bash
pipx install poetry
```


### 2. Install Python Dependencies

Ensure Poetry uses Python 3.13:

```bash
poetry env use python3.13
```

Install the dependencies into our virtual environment:

```bash
poetry install
```

_Note_ If it fails, try to pass the flag `--no-root`.

### 3. Setup MOSEK

As an efficient state of the art solver, [MOSEK](https://www.mosek.com/) is used.

1. Obtain personal academic license from [here](https://www.mosek.com/license/request/personal-academic/)
2. Move license to `~/mosek/` or set the environment variable `MOSEKLM_LICENSE_FILE` to point to your file.

## Running Jupyter Notebooks in VS Code

This project includes **Jupyter notebooks** that can be run in **VS Code**.

First, we install a new Jupyter Kernel:

```bash
poetry run python -m ipykernel install --user --name coco --display-name "Computational Control"
```

Ensure that you have following extensions installed:

* Python
* Jupyter

The open vscode and select the right python interpreter `.venv/bin/python`.

Open a notebook (`.ipynb` file) and select the same Kernel with the top right menu.
