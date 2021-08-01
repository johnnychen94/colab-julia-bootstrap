# Bootstrap Julia kernel in google colab

Steps to run:

1. Open `julia.ipynb` file on your colab
2. install the Julia kernel by running the first block
3. refresh the page
4. start coding Julia in colab 🎉

What's behind, a step by step explaination:

1. jupyter notebook has predefined kernelspec information, this `julia.ipynb` file predefines `julia`. You can find it by checking [in raw format](https://raw.githubusercontent.com/johnnychen94/colab-julia-bootstrap/master/julia.ipynb)
2. when you start a new runtime in colab, it trys to open the julia kernel, because that's what `julia.ipynb` requires. But unfortunately this will fail, so colab falls back to using the Python kernel
3. install the Julia kernel by running the first block in python kernel (note the prefix `!`)
4. refresh the page, colab will then reload the notebook, again, it will tries to load the `julia` kernel. But since we have it installed in the current runtime, this time it will success.

Because the `julia` kernelspec is not available, you will need to install julia kernel for every runtime you've started in colab.
