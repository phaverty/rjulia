rjulia
===============

rjulia provides an interface between R and Julia. It allows a user to run a script in Julia from R, and maps objects between the two languages.

It currently supports use on Linux and Windows from the console, but build on Windows only for advance users.

Installing
-------------

1. Install julia v0.3x and R version >=3.1.0.
 
2. Add `<juliainstalldir>/bin` to your system PATH variable if needed.

3. Install the rjulia package. If you're using julia 0.4, use the "master" branch of rjulia.

    You can install rjulia on Linux using the devtools package:

    ```r
    install.packages("devtools") #if not already installed
    devtools::install_github("armgong/rjulia", ref="0.3")
    ```
    You can install rjulia on Windows using the Rtools and devtools package :

    ```r
    install.packages("devtools") #if not already installed
    devtools::install_github("armgong/rjulia", ref="0.3", args = "--no-multiarch")
    ```
    
4. If you want to be able to use R or Julia objects that contain NA values or factors or data frames, the Julia packages `DataArrays` and `DataFrames` must be installed.

Simple example 
-------------

```r
library(rjulia)
julia_init() #**(will auto find your julia home)**
julia_eval("1+1")
```

Demo
-------------

Please see the `*.R` files in the `demo/` directory, or use
```r
	demo(package = "rjulia")
```


Docs
-------------
Help files are now done, mostly with examples.


Know Problems
-------------
   * The Julia api rapidly changes between releases. Each time you upgrade or downgrade Julia, rjulia needs to be recompiled and reinstalled, e.g. with `devtools::install_github`. 

   * Due to https://github.com/JuliaLang/julia/issues/10085, the rjulia master branch may crash when running certain (testparallel etc.) Julia code on Julia 0.3.x. Most demos run ok.
   
   *Due to RStudio issue (https://github.com/armgong/rjulia/issues/16), when using rjulia on Windows 64bit, RStudio-0.98.1103 is recommended http://download1.rstudio.org/RStudio-0.98.1103.zip .
