# Bootstrap Julia kernel in google colab

> Google Colab is great, Julia is great, we should have both.

Steps to run:

1. Open `julia.ipynb` file on your colab: [quick link](https://colab.research.google.com/drive/1_4Yz3FKO5_uuYvamEfHqwtFT9WpCuSbm?usp=sharing)
2. install the Julia kernel by running the first block
3. refresh the page
4. start coding Julia in colab 🎉

What's behind the scenes, a step by step explaination:

1. jupyter notebook has predefined kernelspec information, this `julia.ipynb` file predefines `"julia"` kernel. You can find this by checking [in raw format](https://raw.githubusercontent.com/johnnychen94/colab-julia-bootstrap/master/julia.ipynb)
2. when you start a new runtime in colab, it trys to open the julia kernel, because that's what `julia.ipynb` requires. But unfortunately this will fail, so colab falls back to using the Python kernel
3. install the Julia kernel by running the first block in python kernel (note the prefix `!`)
4. refresh the page, colab will then reload the notebook, again, it will tries to load the `julia` kernel. But since we have it installed in the current runtime, this time it will success.

Because the `julia` kernelspec is not available by default, you will need to install julia kernel everytime when you start a new colab runtime.
