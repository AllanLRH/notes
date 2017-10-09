# Making Python simulation go faster

There's a lot of overhead in Python, and while it's fast enough for many applications, large simulations, especially those consisting of nested `for`-loops, can benefit greatly from using some libraries for making it go faster!

There's multiple ways of doing so, but _Cython_ and _Numba_ are two obvious choices.

Both of these are intended to be used for optimizing the _slow_ part of your code, rather than the entire codebase... use profiling to find the slow parts of your code.

## Profiling (finding the slow parts of the code aka the bottlenecks)

There's two good libraries I know of for profiling:

[Kernprof/lineprof](Kernprof/lineprof), which gives you a line-by-line performance report... this is a good choice for a detailed overview.

[cProfile](https://docs.python.org/3.6/library/profile.html) library, which reports on how much time you spend inside each function.

[timeit](https://docs.python.org/3.6/library/timeit.html#module-timeit), which can rerun a certaing function many times, and report on the time taken to run the function

[time.time()](https://docs.python.org/3/library/time.html) could also be used. The function returns the time in unix format.



*See a short tutorial for profiling [here](http://www.scipy-lectures.org/advanced/optimizing/index.html)!*



## Numba

Numba leverages the _LLVM_-jit compiler (Just In Time-compiler) to optimize a subset of your python code. It works with numpy arrays, but it can be diffucult to get good performance: Be careful to tun

- [A guide to both Numba and Cython](https://neurohackweek.github.io/cython-tutorial/04-numba/)
- [Numba documentation](http://numba.pydata.org/numba-doc/0.35.0/index.html)... disregard the CUDA stuff, unless you want to run your code on a graphics card, which is not possibly for all code, and generally quite difficult.
- A [presentation of numba on Youtube](https://www.youtube.com/watch?v=ncLemYw8LUs)... Only 4:44 long, but not the best video quality.



## Cython

Like Numba, Cython support a subset of Python (including Numpy), and are able to compile very Python-like code to C... kinda, since it's not entirely free from the Python runtime.

*Cython would be my go-to solution if I needed to speed things up... I might try Numba first, because trying Numba is miminal-effort, but I'd likely end up using Cython.*

The easiest way to learn to use Cython, is just to [search for Cython on Youtube](https://www.youtube.com/results?search_query=cython) and find a video which is not too old (Try to finc some which are at maximum two years old, but preferable newer, like [this video](https://www.youtube.com/watch?v=mXuEoqK4bEc)).

Another simple Cython tutorial is [this section](http://www.scipy-lectures.org/advanced/interfacing_with_c/interfacing_with_c.html#id10) of the Scipy Lecture Notes (whici is a _great_ resource).

The Cython Documentation also have some [tutorials](http://cython.readthedocs.io/en/latest/src/tutorial/).

Need help [deciding between Cython and Numba](https://eng.climate.com/2015/04/09/numba-vs-cython-how-to-choose/?utm_content=buffer222ae&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)?

