# Bootstrap Julia kernel in google colab

> Google Colab is great, Julia is great, we should have both.

Steps to run:

1. Open `julia.ipynb` file on your colab. Here's the quick link for [CPU runtime](https://colab.research.google.com/drive/1_4Yz3FKO5_uuYvamEfHqwtFT9WpCuSbm?usp=sharing) and [GPU runtime](https://colab.research.google.com/drive/1nQ-KuSyICY80pLiBsAH_hyV46y2W67CE?usp=sharing)
2. install the Julia kernel by running the first block
3. refresh the page
4. start coding Julia in colab 🎉

What's behind the scenes, a step by step explanation:

1. jupyter notebook has predefined kernelspec information, this `julia.ipynb` file predefines `"julia"` kernel. You can find this by checking [in raw format](https://raw.githubusercontent.com/johnnychen94/colab-julia-bootstrap/master/julia.ipynb)
2. when you start a new runtime in colab, it tries to open the Julia kernel, because that's what `julia.ipynb` requires. But unfortunately this will fail, so colab falls back to using the Python kernel
3. install the Julia kernel by running the first block in python kernel (note the prefix `!`)
4. refresh the page, colab will then reload the notebook, again, it will try to load the `julia` kernel. But since we have it installed in the current runtime, this time it will succeed.

Because the `julia` kernelspec is not available by default, you will need to install Julia kernel everytime when you start a new colab runtime.

## For GPU runtime

### My GPU runtime switches back to CPU runtime

For GPU runtimes, it seems that when you refresh the page via "Ctrl-R" colab will redirect you to
the CPU runtimes and thus you lose the Julia kernel. I don't know the internal but this is perhaps a
colab strategy to save GPU resource. To fix it, instead of manually refreshing page via "Ctrl-R",
you can instead trigger kernel reloading by:

1. go to "view resources" -> "change runtime type"
2. ensure it is "Julia" and "GPU". Almost certainly you don't need to change anything here if you're already on GPU runtime.
3. click "save" to trigger the kernel reload.

This trick works when I write it up, I hope this still works in the future.

### It takes decades to install CUDA.jl everytime when I open a new notebook runtime

It's also worth noting that you can force CUDA.jl to use system-installed CUDA library by setting
environment variable `JULIA_CUDA_USE_BINARYBUILDER` to `false`. This saves a lot of downloading time.
