# Repository of code examples given in TXST CS 7313 - Fall 2025

## Getting started — Setting up your environment to run computer vision applications (VS Code version)

We will install the necessary software and set up an environment to run computer vision applications in Python on **Windows**. (macOS/Linux steps are similar.)

All the code and data for this course are on GitHub:  
https://github.com/cs-txst/cs7313-fall2025

The best way to download that code is by installing Git and cloning the repository to your computer.

> **Skip Git?** You can click the green **Code** button on the GitHub page and download a ZIP instead, then jump to **Step 3**.

---

## 1) Install Git

If you don’t have Git installed, follow the instructions here:  
[Git - Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

---

## 2) Clone the repository

Open a command prompt (Win+R → `cmd`) and `cd` to the folder where you want the local copy, e.g.:

```
cd C:\Users\johndoe\Documents\Temp
```

Then clone:

```
git clone https://github.com/cs-txst/cs7313-fall2025.git
```

You now have a local copy. In the future, pull updates by running inside that folder:

```
git pull
```

Git is a powerful source control system beyond cloning/pulling. For more, see *An Intro to Git and GitHub for Beginners*.

---

## 3) Install Miniconda and CV/ML libraries

**Miniconda** is a minimal version of Anaconda (a Python package/env manager).

1. Install Miniconda using default settings:  
  https://docs.conda.io/en/latest/miniconda.html
  
2. Open **Anaconda Prompt** (search “Anaconda Prompt” in the Start menu). You should see a prompt like:
  

```
(base) C:\Users\johndoe>
```

This indicates you’re in the base conda environment. We’ll create a dedicated environment named **ml** (computer vision) to avoid package conflicts between projects.

Run the following (one line at a time — this may take several minutes):

```
conda create --name ml python=3.11
conda activate ml
pip install tensorflow matplotlib numpy scipy scikit-learn scikit-image pandas pillow graphviz tqdm torch torchvision torchaudio mlxtend opencv-python ipykernel
```

> **Why `ipykernel`?** VS Code uses it behind the scenes to run Jupyter notebooks (`.ipynb`) inside the editor.

**Next time you work:** you do **not** re-create or re-install; just activate the environment first:

```
conda activate ml
```

After activating, your prompt should look like:

```
(ml) C:\Users\johndoe>
```

---

## 4) Run CV/ML applications in **Visual Studio Code**

We’ll use **VS Code** to develop and run Python code (scripts and notebooks).

### A) Install VS Code and extensions

1. Install **Visual Studio Code** (Windows).
  
2. Launch VS Code and install these extensions (from the Extensions panel):
  
  - **Python** (by Microsoft)
    
  - **Jupyter** (by Microsoft) — enables running `.ipynb` notebooks inside VS Code
    

### B) Open the course folder

- In VS Code: **File → Open Folder…** and select the cloned folder (e.g., `C:\Users\johndoe\Documents\Temp\cs7313-fall2025`).
  
- When prompted, click **Yes, I trust the authors**.
  

### C) Select the correct Python interpreter (your `ml` environment)

1. Press **Ctrl+Shift+P** → type **Python: Select Interpreter**.
  
2. Choose the interpreter that points to your **ml** conda environment.
  
  - If you don’t see it, first open **Terminal → New Terminal** in VS Code and run:
    
    ```
    conda activate ml
    python -m ipykernel install --user --name ml --display-name "Python (ml)"
    ```
    
    Then run **Python: Select Interpreter** again and pick **Python (ml)**.
    

### D) Run Python scripts (`.py`)

- Open any `.py` file from the repo.
  
- Ensure the status bar shows your `ml` interpreter.
  
- Click **► Run Python File** in the top-right of the editor, or press **F5** to debug.
  
- Alternatively, from **Terminal** in VS Code (with `ml` active), run:
  
  ```
  python path\to\script.py
  ```
  

### E) Run Jupyter notebooks (`.ipynb`) **inside** VS Code

- Open a `.ipynb` file in VS Code.
  
- In the top-right of the notebook, select the **Kernel** and choose **Python (ml)**.
  
- Click **Run All** or run cells individually.
  

> If the `ml` kernel isn’t listed, make sure the environment is active in the VS Code terminal and that you ran the `ipykernel` install command shown above.

### F) Quick sanity check (optional)

Create a new file `check_env.py` and run it:

```python
import sys, cv2
print("Python:", sys.version)
print("OpenCV:", cv2.__version__)
try:
    import tensorflow as tf
    print("TensorFlow:", tf.__version__)
except Exception as e:
    print("TensorFlow not available:", e)
```

You should see version numbers printed in the VS Code terminal/output.

---

You’re all set to develop and run computer vision & machine learning applications using **VS Code** and your `ml` conda environment.