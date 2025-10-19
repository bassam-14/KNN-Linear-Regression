# Installation Guide for KNN-Linear-Regression Project

## Problem

You're using Python 3.13.2, which is very new, and some packages may not have compatible versions yet.

## Solutions

### Option 1: Use Conda (Recommended)

If you have Anaconda or Miniconda installed:

```bash
conda create -n knn-regression python=3.11
conda activate knn-regression
conda install numpy pandas scikit-learn matplotlib
```

### Option 2: Use Python 3.11 or 3.12

Install a more stable Python version:

1. Download Python 3.11 or 3.12 from python.org
2. Install it alongside your current Python
3. Use the new version for this project

### Option 3: Try installing with specific versions

```bash
pip install numpy==1.24.3 pandas==2.0.3 scikit-learn==1.3.0 matplotlib==3.7.2
```

### Option 4: Use the current setup (No plotting)

The notebook now works without matplotlib. It will show:

- Text-based results of alpha tuning
- Top 10 best alpha values
- Instructions for enabling plotting later

## Current Status

✅ The notebook works without matplotlib
✅ Shows alpha tuning results in text format
✅ Ready to run the Lasso regression analysis

## To Enable Plotting Later

Once you have matplotlib installed, uncomment the plotting code in cell 4 of the notebook.
