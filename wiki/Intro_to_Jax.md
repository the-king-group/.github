This is brief tour of introductory materials for JAX, an automatic differentiation code base that also supports automatic vectorization, automatic parallelization, and just-in-time compiling. We also link introductory materials for JAX-MD, a molecular dynamics package that is built on top of JAX. It allows you to run fully differentiable molecular dynamics simulations.

**JAX Information:**
- [JAX documentation](https://jax.readthedocs.io/en/latest/notebooks/quickstart.html), which includes a tutorial
- [JAX Tutorial](https://colab.research.google.com/drive/1bp45JyWXzB1mBj_smlAmf8SHOE7ay7sR#scrollTo=b7tMzjTs9Tje), tutorial from Harvard University's Applied Math 216 course, which includes how to model physical ODE systems
    - [Updated JAX Tutorial](https://colab.research.google.com/drive/1AxAAvOzFupWhKZb7M50QgJmRg5qvMAgp?usp=sharing), tutorial with up-to-date syntax from Katherine Ellis in fall 2025


**JAX-MD Information:**
- [Jax-MD Documentation](https://jax-md.readthedocs.io/en/latest/)
- [Jax-MD Source Code](https://github.com/google/jax-md) This github page also contains links to several useful introductory colab notebooks
- [Jax-MD Cookbook](https://colab.research.google.com/github/google/jax-md/blob/master/notebooks/jax_md_cookbook.ipynb), a colab notebook that provides an introduction to JAX-MD

**Step-by-step Guide to Compile JAX and JAX-MD on an Apple M1 Chip Machine:**

Currently there is no pre-built wheel to install JAX on an M1 Chip Machine.  In fact, most python distributors haven't released an official package to install python on the native M1 build.  If you download Anaconda official release to install python and related packages, you will be installing using Rosetta2, which creates an emulated environment of the old Intel Chip architecture.  This is OK with most python packages, but you would run into problem if you want to have a local build of JAX and JAX-MD.  In order to properly install JAX and JAX-MD, we want to build a python environment with native M1 architecture, and then compile JAX and JAX-MD from source.

Installation steps:
1. Install python with [miniforge](https://github.com/conda-forge/miniforge#miniforge3) using the `Miniforge3-MacOSX-arm64` installer
2. Install `JAX` prerequisite `numpy` `scipy` `six` `wheel` `bazel` using `conda` (The `miniforge` installer should automatically install the M1 native build version for these packages) by writing `conda install numpy scipy six wheel bazel`
3. Download `JAX` source code

    ```
    git clone https://github.com/google/jax
    cd jax
    ```
4. Compile and install `jax-lib`

   ```
   python build/build.py
   pip install dist/*.whl  # installs jaxlib (includes XLA)
   ```
5. Install `jax`

   `pip install -e .  # installs jax`
   
6. Download and Install `JAX-MD` source code

   ```
   git clone https://github.com/google/jax-md
   pip install -e jax-md
   ```


Credit to Chrisy Xiyu Du for these introductory materials.
   
   
    
