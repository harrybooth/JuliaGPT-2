# JuliaTransformerLens

This code base is using the [Julia Language](https://julialang.org/) and
[DrWatson](https://juliadynamics.github.io/DrWatson.jl/stable/)
to make a reproducible scientific project named
> JuliaTransformerLens

It is authored by Harry Booth.

This is a replication of Neel Nanda's "Clean Transformer Demo" notebook in which I produce a first principles gpt2 implementation in the Julia progamming language. 

I believe the Julia programming language has a lot to offer mechanistic interpretability research. This is mainly because Julia aims to solve the two-language problem (https://scientificcoder.com/how-to-solve-the-two-language-problem). Julia has the speed of C++ but the readability of Python. One can take slow julia code hobbled together for an exploratory project and make it performant without having to re-write it. Most importantly, automatic differentiation is almost native to the Julia programming language. This means that we dont have to use AD libraries like pytorch - we can just write julia code and differentiate through it e.g. with Enzyme (https://enzyme.mit.edu/julia/stable/). 

Crucially, I believe this makes the internals of ML architectures built in julia very transparent. There are no "pytorch functions", just functions. And so I believe it forms a great tool for learning and mechanistic interpretability. 

I plan to explore this in more detail over the next year. For now, see below a julia implementation of GPT2 using the "lux" AD library (https://lux.csail.mit.edu/stable/manual/interface). There are some schematics which aim to provide a visual explanation of embedding, positional embedding and attention, which I believe are the most "uniquely transpormer" aspects of the architecture. I have built in interoperatability functions between the python TransformerLens package (https://github.com/TransformerLensOrg/TransformerLens) and this notebook so that we can check our implementation as we go along, and load the original model weights.

I would recommend reading through Neel Nandas excellent colab and video turtorial alongside this notebook : https://www.youtube.com/watch?v=dsjUDacBw8o&t=1236s

I will be adding to this to make it more comprehensive at some point in the future.

Many thanks!

To (locally) reproduce this project, do the following:

0. Download this code base. Notice that raw data are typically not included in the
   git-history and may need to be downloaded independently.
1. Open a Julia console and do:
   ```
   julia> using Pkg
   julia> Pkg.add("DrWatson") # install globally, for using `quickactivate`
   julia> Pkg.activate("path/to/this/project")
   julia> Pkg.instantiate()
   ```

This will install all necessary packages for you to be able to run the scripts and
everything should work out of the box, including correctly finding local paths.

You may notice that most scripts start with the commands:
```julia
using DrWatson
@quickactivate "JuliaTransformerLens"
```
which auto-activate the project and enable local path handling from DrWatson.
