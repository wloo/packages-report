---
title: "What they forgot to teach you about R"
author: "Pendulum, Therapeutics, Inc."
date: "01/27/2020"
output: 
  html_document: 
    toc: yes
    toc_depth: 3
    toc_float: true
    keep_md: yes
editor_options: 
  chunk_output_type: console
---




```r
library(tidyverse)
```

```
## ── Attaching packages ────────────────────────────────────────────────── tidyverse 1.2.1 ──
```

```
## ✔ ggplot2 3.2.1     ✔ purrr   0.3.2
## ✔ tibble  2.1.3     ✔ dplyr   0.8.3
## ✔ tidyr   1.0.0     ✔ stringr 1.4.0
## ✔ readr   1.3.1     ✔ forcats 0.4.0
```

```
## ── Conflicts ───────────────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
```

# Day 1
## Deep thoughts
Organization - work on it today - don't need to go back and re-organize old things. 
File organization - self-explanatory rather than a detailed Readme
"Good enough practices in scientific computing" paper by Wilson, Bryan, et al  <http://bit.ly/good-enuff>

## Exploring your R installation
Packages - by default live locally in `.Library`.

```r
.Library
```

```
## [1] "/Library/Frameworks/R.framework/Resources/library"
```

```r
.libPaths() # shows actual paths
```

```
## [1] "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
```

```r
installed.packages() # show all installed packages
```

```
##                      Package               
## abind                "abind"               
## ade4                 "ade4"                
## ape                  "ape"                 
## askpass              "askpass"             
## assertthat           "assertthat"          
## backports            "backports"           
## base                 "base"                
## base64enc            "base64enc"           
## beeswarm             "beeswarm"            
## BH                   "BH"                  
## bindr                "bindr"               
## bindrcpp             "bindrcpp"            
## Biobase              "Biobase"             
## BiocGenerics         "BiocGenerics"        
## BiocManager          "BiocManager"         
## BiocParallel         "BiocParallel"        
## BiocVersion          "BiocVersion"         
## biomformat           "biomformat"          
## Biostrings           "Biostrings"          
## bit                  "bit"                 
## bit64                "bit64"               
## bitops               "bitops"              
## bizarro              "bizarro"             
## boot                 "boot"                
## brew                 "brew"                
## broom                "broom"               
## callr                "callr"               
## car                  "car"                 
## carData              "carData"             
## caret                "caret"               
## caTools              "caTools"             
## cellranger           "cellranger"          
## class                "class"               
## cli                  "cli"                 
## cliapp               "cliapp"              
## clipr                "clipr"               
## clisymbols           "clisymbols"          
## cluster              "cluster"             
## codetools            "codetools"           
## colorspace           "colorspace"          
## commonmark           "commonmark"          
## compiler             "compiler"            
## conflicted           "conflicted"          
## corpcor              "corpcor"             
## covr                 "covr"                
## cowplot              "cowplot"             
## cranlogs             "cranlogs"            
## crayon               "crayon"              
## crosstalk            "crosstalk"           
## curl                 "curl"                
## cyclocomp            "cyclocomp"           
## cyl                  "cyl"                 
## dada2                "dada2"               
## data.table           "data.table"          
## datasets             "datasets"            
## DBI                  "DBI"                 
## dbplyr               "dbplyr"              
## decontam             "decontam"            
## DelayedArray         "DelayedArray"        
## DEoptimR             "DEoptimR"            
## desc                 "desc"                
## devtools             "devtools"            
## digest               "digest"              
## docopt               "docopt"              
## doParallel           "doParallel"          
## dotCall64            "dotCall64"           
## dplyr                "dplyr"               
## DT                   "DT"                  
## e1071                "e1071"               
## ellipsis             "ellipsis"            
## EMD                  "EMD"                 
## enc                  "enc"                 
## evaluate             "evaluate"            
## fansi                "fansi"               
## fastmap              "fastmap"             
## fastmatch            "fastmatch"           
## fields               "fields"              
## filelock             "filelock"            
## flexdashboard        "flexdashboard"       
## flowCore             "flowCore"            
## flowPeaks            "flowPeaks"           
## foofactor            "foofactor"           
## forcats              "forcats"             
## foreach              "foreach"             
## foreign              "foreign"             
## formatR              "formatR"             
## fs                   "fs"                  
## futile.logger        "futile.logger"       
## futile.options       "futile.options"      
## generics             "generics"            
## GenomeInfoDb         "GenomeInfoDb"        
## GenomeInfoDbData     "GenomeInfoDbData"    
## GenomicAlignments    "GenomicAlignments"   
## GenomicRanges        "GenomicRanges"       
## geometry             "geometry"            
## GGally               "GGally"              
## ggbeeswarm           "ggbeeswarm"          
## ggplot2              "ggplot2"             
## ggridges             "ggridges"            
## gh                   "gh"                  
## git2r                "git2r"               
## glue                 "glue"                
## googlesheets         "googlesheets"        
## gower                "gower"               
## graph                "graph"               
## graphics             "graphics"            
## grDevices            "grDevices"           
## grid                 "grid"                
## gridExtra            "gridExtra"           
## gtable               "gtable"              
## haven                "haven"               
## here                 "here"                
## hexbin               "hexbin"              
## highr                "highr"               
## hms                  "hms"                 
## htmltools            "htmltools"           
## htmlwidgets          "htmlwidgets"         
## httpuv               "httpuv"              
## httr                 "httr"                
## hwriter              "hwriter"             
## igraph               "igraph"              
## ini                  "ini"                 
## ipred                "ipred"               
## ips                  "ips"                 
## IRanges              "IRanges"             
## itdepends            "itdepends"           
## iterators            "iterators"           
## jsonlite             "jsonlite"            
## kernlab              "kernlab"             
## KernSmooth           "KernSmooth"          
## kmer                 "kmer"                
## knitr                "knitr"               
## labeling             "labeling"            
## labrador             "labrador"            
## labradorbase         "labradorbase"        
## lambda.r             "lambda.r"            
## later                "later"               
## lattice              "lattice"             
## latticeExtra         "latticeExtra"        
## lava                 "lava"                
## lazyeval             "lazyeval"            
## lifecycle            "lifecycle"           
## linprog              "linprog"             
## lintr                "lintr"               
## lme4                 "lme4"                
## lobstr               "lobstr"              
## locfit               "locfit"              
## lpSolve              "lpSolve"             
## lubridate            "lubridate"           
## magic                "magic"               
## magrittr             "magrittr"            
## manipulateWidget     "manipulateWidget"    
## maps                 "maps"                
## maptools             "maptools"            
## markdown             "markdown"            
## MASS                 "MASS"                
## Matrix               "Matrix"              
## MatrixModels         "MatrixModels"        
## matrixStats          "matrixStats"         
## mean2                "mean2"               
## memoise              "memoise"             
## methods              "methods"             
## mgcv                 "mgcv"                
## mime                 "mime"                
## miniUI               "miniUI"              
## minpack.lm           "minpack.lm"          
## minqa                "minqa"               
## ModelMetrics         "ModelMetrics"        
## modelr               "modelr"              
## MPN                  "MPN"                 
## multtest             "multtest"            
## munsell              "munsell"             
## mvtnorm              "mvtnorm"             
## new                  "new"                 
## nlme                 "nlme"                
## nloptr               "nloptr"              
## nnet                 "nnet"                
## numDeriv             "numDeriv"            
## openssl              "openssl"             
## openxlsx             "openxlsx"            
## parallel             "parallel"            
## pbkrtest             "pbkrtest"            
## pcaPP                "pcaPP"               
## permute              "permute"             
## phangorn             "phangorn"            
## phylogram            "phylogram"           
## phyloseq             "phyloseq"            
## pillar               "pillar"              
## pkgbuild             "pkgbuild"            
## pkgcache             "pkgcache"            
## pkgconfig            "pkgconfig"           
## pkgload              "pkgload"             
## plogr                "plogr"               
## plotly               "plotly"              
## plyr                 "plyr"                
## praise               "praise"              
## prettycode           "prettycode"          
## prettyunits          "prettyunits"         
## processx             "processx"            
## prodlim              "prodlim"             
## progress             "progress"            
## promises             "promises"            
## pryr                 "pryr"                
## ps                   "ps"                  
## pspline              "pspline"             
## purrr                "purrr"               
## qpcR                 "qpcR"                
## quadprog             "quadprog"            
## quantreg             "quantreg"            
## R6                   "R6"                  
## rappdirs             "rappdirs"            
## rcmdcheck            "rcmdcheck"           
## RColorBrewer         "RColorBrewer"        
## Rcpp                 "Rcpp"                
## RcppEigen            "RcppEigen"           
## RcppParallel         "RcppParallel"        
## RcppProgress         "RcppProgress"        
## RcppRoll             "RcppRoll"            
## RCurl                "RCurl"               
## readr                "readr"               
## readxl               "readxl"              
## recipes              "recipes"             
## rematch              "rematch"             
## rematch2             "rematch2"            
## remotes              "remotes"             
## reprex               "reprex"              
## requirements         "requirements"        
## reshape              "reshape"             
## reshape2             "reshape2"            
## rex                  "rex"                 
## rgl                  "rgl"                 
## rhdf5                "rhdf5"               
## Rhdf5lib             "Rhdf5lib"            
## rio                  "rio"                 
## rlang                "rlang"               
## rmarkdown            "rmarkdown"           
## robustbase           "robustbase"          
## roxygen2             "roxygen2"            
## roxygen2md           "roxygen2md"          
## rpart                "rpart"               
## rpivotTable          "rpivotTable"         
## rprojroot            "rprojroot"           
## rrcov                "rrcov"               
## Rsamtools            "Rsamtools"           
## rstudioapi           "rstudioapi"          
## rversions            "rversions"           
## rvest                "rvest"               
## S4Vectors            "S4Vectors"           
## scales               "scales"              
## segmented            "segmented"           
## selectr              "selectr"             
## seqinr               "seqinr"              
## sessioninfo          "sessioninfo"         
## sfsmisc              "sfsmisc"             
## shiny                "shiny"               
## ShortRead            "ShortRead"           
## sloop                "sloop"               
## snow                 "snow"                
## sourcetools          "sourcetools"         
## sp                   "sp"                  
## spam                 "spam"                
## SparseM              "SparseM"             
## spatial              "spatial"             
## splines              "splines"             
## SQUAREM              "SQUAREM"             
## stats                "stats"               
## stats4               "stats4"              
## stringdist           "stringdist"          
## stringi              "stringi"             
## stringr              "stringr"             
## SummarizedExperiment "SummarizedExperiment"
## survival             "survival"            
## sys                  "sys"                 
## tcltk                "tcltk"               
## testns               "testns"              
## testthat             "testthat"            
## tibble               "tibble"              
## tidyr                "tidyr"               
## tidyselect           "tidyselect"          
## tidyverse            "tidyverse"           
## timeDate             "timeDate"            
## tinytex              "tinytex"             
## tools                "tools"               
## UpSetR               "UpSetR"              
## usethis              "usethis"             
## utf8                 "utf8"                
## utils                "utils"               
## uuid                 "uuid"                
## vctrs                "vctrs"               
## vegan                "vegan"               
## vipor                "vipor"               
## viridisLite          "viridisLite"         
## wbr                  "wbr"                 
## wbrlims              "wbrlims"             
## webshot              "webshot"             
## whisker              "whisker"             
## withr                "withr"               
## xfun                 "xfun"                
## XML                  "XML"                 
## xml2                 "xml2"                
## xmlparsedata         "xmlparsedata"        
## xopen                "xopen"               
## xtable               "xtable"              
## XVector              "XVector"             
## yaml                 "yaml"                
## zeallot              "zeallot"             
## zip                  "zip"                 
## zlibbioc             "zlibbioc"            
## zoo                  "zoo"                 
##                      LibPath                                                         
## abind                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ade4                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ape                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## askpass              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## assertthat           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## backports            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## base                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## base64enc            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## beeswarm             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## BH                   "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## bindr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## bindrcpp             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## Biobase              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## BiocGenerics         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## BiocManager          "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## BiocParallel         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## BiocVersion          "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## biomformat           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## Biostrings           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## bit                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## bit64                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## bitops               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## bizarro              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## boot                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## brew                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## broom                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## callr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## car                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## carData              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## caret                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## caTools              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## cellranger           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## class                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## cli                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## cliapp               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## clipr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## clisymbols           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## cluster              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## codetools            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## colorspace           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## commonmark           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## compiler             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## conflicted           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## corpcor              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## covr                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## cowplot              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## cranlogs             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## crayon               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## crosstalk            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## curl                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## cyclocomp            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## cyl                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## dada2                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## data.table           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## datasets             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## DBI                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## dbplyr               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## decontam             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## DelayedArray         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## DEoptimR             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## desc                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## devtools             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## digest               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## docopt               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## doParallel           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## dotCall64            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## dplyr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## DT                   "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## e1071                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ellipsis             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## EMD                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## enc                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## evaluate             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## fansi                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## fastmap              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## fastmatch            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## fields               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## filelock             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## flexdashboard        "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## flowCore             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## flowPeaks            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## foofactor            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## forcats              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## foreach              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## foreign              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## formatR              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## fs                   "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## futile.logger        "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## futile.options       "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## generics             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## GenomeInfoDb         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## GenomeInfoDbData     "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## GenomicAlignments    "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## GenomicRanges        "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## geometry             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## GGally               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ggbeeswarm           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ggplot2              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ggridges             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## gh                   "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## git2r                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## glue                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## googlesheets         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## gower                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## graph                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## graphics             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## grDevices            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## grid                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## gridExtra            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## gtable               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## haven                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## here                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## hexbin               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## highr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## hms                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## htmltools            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## htmlwidgets          "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## httpuv               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## httr                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## hwriter              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## igraph               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ini                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ipred                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ips                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## IRanges              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## itdepends            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## iterators            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## jsonlite             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## kernlab              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## KernSmooth           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## kmer                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## knitr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## labeling             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## labrador             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## labradorbase         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## lambda.r             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## later                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## lattice              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## latticeExtra         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## lava                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## lazyeval             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## lifecycle            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## linprog              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## lintr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## lme4                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## lobstr               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## locfit               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## lpSolve              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## lubridate            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## magic                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## magrittr             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## manipulateWidget     "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## maps                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## maptools             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## markdown             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## MASS                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## Matrix               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## MatrixModels         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## matrixStats          "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## mean2                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## memoise              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## methods              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## mgcv                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## mime                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## miniUI               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## minpack.lm           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## minqa                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ModelMetrics         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## modelr               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## MPN                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## multtest             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## munsell              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## mvtnorm              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## new                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## nlme                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## nloptr               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## nnet                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## numDeriv             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## openssl              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## openxlsx             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## parallel             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## pbkrtest             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## pcaPP                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## permute              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## phangorn             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## phylogram            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## phyloseq             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## pillar               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## pkgbuild             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## pkgcache             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## pkgconfig            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## pkgload              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## plogr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## plotly               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## plyr                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## praise               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## prettycode           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## prettyunits          "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## processx             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## prodlim              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## progress             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## promises             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## pryr                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ps                   "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## pspline              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## purrr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## qpcR                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## quadprog             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## quantreg             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## R6                   "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rappdirs             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rcmdcheck            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## RColorBrewer         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## Rcpp                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## RcppEigen            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## RcppParallel         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## RcppProgress         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## RcppRoll             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## RCurl                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## readr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## readxl               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## recipes              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rematch              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rematch2             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## remotes              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## reprex               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## requirements         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## reshape              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## reshape2             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rex                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rgl                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rhdf5                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## Rhdf5lib             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rio                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rlang                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rmarkdown            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## robustbase           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## roxygen2             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## roxygen2md           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rpart                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rpivotTable          "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rprojroot            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rrcov                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## Rsamtools            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rstudioapi           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rversions            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## rvest                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## S4Vectors            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## scales               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## segmented            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## selectr              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## seqinr               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## sessioninfo          "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## sfsmisc              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## shiny                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## ShortRead            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## sloop                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## snow                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## sourcetools          "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## sp                   "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## spam                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## SparseM              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## spatial              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## splines              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## SQUAREM              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## stats                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## stats4               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## stringdist           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## stringi              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## stringr              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## SummarizedExperiment "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## survival             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## sys                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## tcltk                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## testns               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## testthat             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## tibble               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## tidyr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## tidyselect           "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## tidyverse            "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## timeDate             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## tinytex              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## tools                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## UpSetR               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## usethis              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## utf8                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## utils                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## uuid                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## vctrs                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## vegan                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## vipor                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## viridisLite          "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## wbr                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## wbrlims              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## webshot              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## whisker              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## withr                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## xfun                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## XML                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## xml2                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## xmlparsedata         "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## xopen                "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## xtable               "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## XVector              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## yaml                 "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## zeallot              "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## zip                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## zlibbioc             "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
## zoo                  "/Library/Frameworks/R.framework/Versions/3.6/Resources/library"
##                      Version      Priority     
## abind                "1.4-5"      NA           
## ade4                 "1.7-13"     NA           
## ape                  "5.3"        NA           
## askpass              "1.1"        NA           
## assertthat           "0.2.1"      NA           
## backports            "1.1.5"      NA           
## base                 "3.6.1"      "base"       
## base64enc            "0.1-3"      NA           
## beeswarm             "0.2.3"      NA           
## BH                   "1.69.0-1"   NA           
## bindr                "0.1.1"      NA           
## bindrcpp             "0.2.2"      NA           
## Biobase              "2.42.0"     NA           
## BiocGenerics         "0.28.0"     NA           
## BiocManager          "1.30.8"     NA           
## BiocParallel         "1.16.6"     NA           
## BiocVersion          "3.8.0"      NA           
## biomformat           "1.10.1"     NA           
## Biostrings           "2.50.2"     NA           
## bit                  "1.1-14"     NA           
## bit64                "0.9-7"      NA           
## bitops               "1.0-6"      NA           
## bizarro              "0.0.0.9000" NA           
## boot                 "1.3-23"     "recommended"
## brew                 "1.0-6"      NA           
## broom                "0.5.2"      NA           
## callr                "3.3.2"      NA           
## car                  "3.0-3"      NA           
## carData              "3.0-2"      NA           
## caret                "6.0-84"     NA           
## caTools              "1.17.1.2"   NA           
## cellranger           "1.1.0"      NA           
## class                "7.3-15"     "recommended"
## cli                  "1.1.0"      NA           
## cliapp               "0.1.0"      NA           
## clipr                "0.7.0"      NA           
## clisymbols           "1.2.0"      NA           
## cluster              "2.1.0"      "recommended"
## codetools            "0.2-16"     "recommended"
## colorspace           "1.4-1"      NA           
## commonmark           "1.7"        NA           
## compiler             "3.6.1"      "base"       
## conflicted           "1.0.4"      NA           
## corpcor              "1.6.9"      NA           
## covr                 "3.3.1"      NA           
## cowplot              "1.0.0"      NA           
## cranlogs             "2.1.1"      NA           
## crayon               "1.3.4"      NA           
## crosstalk            "1.0.0"      NA           
## curl                 "4.3"        NA           
## cyclocomp            "1.1.0"      NA           
## cyl                  "0.0.0.9000" NA           
## dada2                "1.10.1"     NA           
## data.table           "1.12.4"     NA           
## datasets             "3.6.1"      "base"       
## DBI                  "1.0.0"      NA           
## dbplyr               "1.4.2"      NA           
## decontam             "1.2.1"      NA           
## DelayedArray         "0.8.0"      NA           
## DEoptimR             "1.0-8"      NA           
## desc                 "1.2.0"      NA           
## devtools             "2.2.1"      NA           
## digest               "0.6.21"     NA           
## docopt               "0.6.1"      NA           
## doParallel           "1.0.15"     NA           
## dotCall64            "1.0-0"      NA           
## dplyr                "0.8.3"      NA           
## DT                   "0.9"        NA           
## e1071                "1.7-2"      NA           
## ellipsis             "0.3.0"      NA           
## EMD                  "1.5.8"      NA           
## enc                  "0.2.1"      NA           
## evaluate             "0.14"       NA           
## fansi                "0.4.0"      NA           
## fastmap              "1.0.1"      NA           
## fastmatch            "1.1-0"      NA           
## fields               "9.9"        NA           
## filelock             "1.0.2"      NA           
## flexdashboard        "0.5.1.1"    NA           
## flowCore             "1.48.1"     NA           
## flowPeaks            "1.28.1"     NA           
## foofactor            "0.0.0.9000" NA           
## forcats              "0.4.0"      NA           
## foreach              "1.4.7"      NA           
## foreign              "0.8-72"     "recommended"
## formatR              "1.7"        NA           
## fs                   "1.3.1"      NA           
## futile.logger        "1.4.3"      NA           
## futile.options       "1.0.1"      NA           
## generics             "0.0.2"      NA           
## GenomeInfoDb         "1.18.2"     NA           
## GenomeInfoDbData     "1.2.0"      NA           
## GenomicAlignments    "1.18.1"     NA           
## GenomicRanges        "1.34.0"     NA           
## geometry             "0.4.4"      NA           
## GGally               "1.4.0"      NA           
## ggbeeswarm           "0.6.0"      NA           
## ggplot2              "3.2.1"      NA           
## ggridges             "0.5.1"      NA           
## gh                   "1.0.1"      NA           
## git2r                "0.26.1"     NA           
## glue                 "1.3.1"      NA           
## googlesheets         "0.3.0"      NA           
## gower                "0.2.1"      NA           
## graph                "1.60.0"     NA           
## graphics             "3.6.1"      "base"       
## grDevices            "3.6.1"      "base"       
## grid                 "3.6.1"      "base"       
## gridExtra            "2.3"        NA           
## gtable               "0.3.0"      NA           
## haven                "2.1.1"      NA           
## here                 "0.1"        NA           
## hexbin               "1.27.3"     NA           
## highr                "0.8"        NA           
## hms                  "0.5.1"      NA           
## htmltools            "0.4.0"      NA           
## htmlwidgets          "1.5.1"      NA           
## httpuv               "1.5.2"      NA           
## httr                 "1.4.1"      NA           
## hwriter              "1.3.2"      NA           
## igraph               "1.2.4.1"    NA           
## ini                  "0.3.1"      NA           
## ipred                "0.9-9"      NA           
## ips                  "0.0.11"     NA           
## IRanges              "2.16.0"     NA           
## itdepends            "0.0.0.9000" NA           
## iterators            "1.0.12"     NA           
## jsonlite             "1.6"        NA           
## kernlab              "0.9-27"     NA           
## KernSmooth           "2.23-16"    "recommended"
## kmer                 "1.1.2"      NA           
## knitr                "1.25"       NA           
## labeling             "0.3"        NA           
## labrador             "0.41.1"     NA           
## labradorbase         "0.1.2"      NA           
## lambda.r             "1.2.4"      NA           
## later                "1.0.0"      NA           
## lattice              "0.20-38"    "recommended"
## latticeExtra         "0.6-28"     NA           
## lava                 "1.6.6"      NA           
## lazyeval             "0.2.2"      NA           
## lifecycle            "0.1.0"      NA           
## linprog              "0.9-2"      NA           
## lintr                "2.0.0"      NA           
## lme4                 "1.1-21"     NA           
## lobstr               "1.1.1"      NA           
## locfit               "1.5-9.1"    NA           
## lpSolve              "5.6.13.3"   NA           
## lubridate            "1.7.4"      NA           
## magic                "1.5-9"      NA           
## magrittr             "1.5"        NA           
## manipulateWidget     "0.10.0"     NA           
## maps                 "3.3.0"      NA           
## maptools             "0.9-8"      NA           
## markdown             "1.1"        NA           
## MASS                 "7.3-51.4"   "recommended"
## Matrix               "1.2-17"     "recommended"
## MatrixModels         "0.4-1"      NA           
## matrixStats          "0.55.0"     NA           
## mean2                "0.0.0.9000" NA           
## memoise              "1.1.0"      NA           
## methods              "3.6.1"      "base"       
## mgcv                 "1.8-29"     "recommended"
## mime                 "0.7"        NA           
## miniUI               "0.1.1.1"    NA           
## minpack.lm           "1.2-1"      NA           
## minqa                "1.2.4"      NA           
## ModelMetrics         "1.2.2"      NA           
## modelr               "0.1.5"      NA           
## MPN                  "0.3.0"      NA           
## multtest             "2.38.0"     NA           
## munsell              "0.5.0"      NA           
## mvtnorm              "1.0-11"     NA           
## new                  "0.0.0.9000" NA           
## nlme                 "3.1-141"    "recommended"
## nloptr               "1.2.1"      NA           
## nnet                 "7.3-12"     "recommended"
## numDeriv             "2016.8-1.1" NA           
## openssl              "1.4.1"      NA           
## openxlsx             "4.1.0.1"    NA           
## parallel             "3.6.1"      "base"       
## pbkrtest             "0.4-7"      NA           
## pcaPP                "1.9-73"     NA           
## permute              "0.9-5"      NA           
## phangorn             "2.5.5"      NA           
## phylogram            "2.1.0"      NA           
## phyloseq             "1.26.1"     NA           
## pillar               "1.4.2"      NA           
## pkgbuild             "1.0.6"      NA           
## pkgcache             "1.0.5"      NA           
## pkgconfig            "2.0.3"      NA           
## pkgload              "1.0.2"      NA           
## plogr                "0.2.0"      NA           
## plotly               "4.9.0"      NA           
## plyr                 "1.8.4"      NA           
## praise               "1.0.0"      NA           
## prettycode           "1.0.2"      NA           
## prettyunits          "1.0.2"      NA           
## processx             "3.4.1"      NA           
## prodlim              "2018.04.18" NA           
## progress             "1.2.2"      NA           
## promises             "1.1.0"      NA           
## pryr                 "0.1.4"      NA           
## ps                   "1.3.0"      NA           
## pspline              "1.0-18"     NA           
## purrr                "0.3.2"      NA           
## qpcR                 "1.4-1"      NA           
## quadprog             "1.5-7"      NA           
## quantreg             "5.51"       NA           
## R6                   "2.4.0"      NA           
## rappdirs             "0.3.1"      NA           
## rcmdcheck            "1.3.3"      NA           
## RColorBrewer         "1.1-2"      NA           
## Rcpp                 "1.0.2"      NA           
## RcppEigen            "0.3.3.5.0"  NA           
## RcppParallel         "4.4.4"      NA           
## RcppProgress         "0.4.1"      NA           
## RcppRoll             "0.3.0"      NA           
## RCurl                "1.95-4.12"  NA           
## readr                "1.3.1"      NA           
## readxl               "1.3.1"      NA           
## recipes              "0.1.7"      NA           
## rematch              "1.0.1"      NA           
## rematch2             "2.1.0"      NA           
## remotes              "2.1.0"      NA           
## reprex               "0.3.0"      NA           
## requirements         "0.0.0.9000" NA           
## reshape              "0.8.8"      NA           
## reshape2             "1.4.3"      NA           
## rex                  "1.1.2"      NA           
## rgl                  "0.100.30"   NA           
## rhdf5                "2.26.2"     NA           
## Rhdf5lib             "1.4.3"      NA           
## rio                  "0.5.16"     NA           
## rlang                "0.4.0"      NA           
## rmarkdown            "1.16"       NA           
## robustbase           "0.93-5"     NA           
## roxygen2             "6.1.1"      NA           
## roxygen2md           "1.0.0"      NA           
## rpart                "4.1-15"     "recommended"
## rpivotTable          "0.3.0"      NA           
## rprojroot            "1.3-2"      NA           
## rrcov                "1.4-7"      NA           
## Rsamtools            "1.34.1"     NA           
## rstudioapi           "0.10"       NA           
## rversions            "2.0.0"      NA           
## rvest                "0.3.4"      NA           
## S4Vectors            "0.20.1"     NA           
## scales               "1.0.0"      NA           
## segmented            "1.0-0"      NA           
## selectr              "0.4-1"      NA           
## seqinr               "3.6-1"      NA           
## sessioninfo          "1.1.1"      NA           
## sfsmisc              "1.1-4"      NA           
## shiny                "1.4.0"      NA           
## ShortRead            "1.40.0"     NA           
## sloop                "1.0.1"      NA           
## snow                 "0.4-3"      NA           
## sourcetools          "0.1.7"      NA           
## sp                   "1.3-1"      NA           
## spam                 "2.3-0"      NA           
## SparseM              "1.77"       NA           
## spatial              "7.3-11"     "recommended"
## splines              "3.6.1"      "base"       
## SQUAREM              "2017.10-1"  NA           
## stats                "3.6.1"      "base"       
## stats4               "3.6.1"      "base"       
## stringdist           "0.9.5.3"    NA           
## stringi              "1.4.3"      NA           
## stringr              "1.4.0"      NA           
## SummarizedExperiment "1.12.0"     NA           
## survival             "2.44-1.1"   "recommended"
## sys                  "3.3"        NA           
## tcltk                "3.6.1"      "base"       
## testns               "0.0.0.9000" NA           
## testthat             "2.2.1"      NA           
## tibble               "2.1.3"      NA           
## tidyr                "1.0.0"      NA           
## tidyselect           "0.2.5"      NA           
## tidyverse            "1.2.1"      NA           
## timeDate             "3043.102"   NA           
## tinytex              "0.16"       NA           
## tools                "3.6.1"      "base"       
## UpSetR               "1.4.0"      NA           
## usethis              "1.5.1"      NA           
## utf8                 "1.1.4"      NA           
## utils                "3.6.1"      "base"       
## uuid                 "0.1-2"      NA           
## vctrs                "0.2.0"      NA           
## vegan                "2.5-6"      NA           
## vipor                "0.4.5"      NA           
## viridisLite          "0.3.0"      NA           
## wbr                  "4.6"        NA           
## wbrlims              "0.9.1"      NA           
## webshot              "0.5.1"      NA           
## whisker              "0.4"        NA           
## withr                "2.1.2"      NA           
## xfun                 "0.10"       NA           
## XML                  "3.98-1.20"  NA           
## xml2                 "1.2.2"      NA           
## xmlparsedata         "1.0.3"      NA           
## xopen                "1.0.0"      NA           
## xtable               "1.8-4"      NA           
## XVector              "0.22.0"     NA           
## yaml                 "2.2.0"      NA           
## zeallot              "0.1.0"      NA           
## zip                  "2.0.4"      NA           
## zlibbioc             "1.28.0"     NA           
## zoo                  "1.8-6"      NA           
##                      Depends                                                                                                                                                                                                                                
## abind                "R (>= 1.5.0)"                                                                                                                                                                                                                         
## ade4                 "R (>= 2.10)"                                                                                                                                                                                                                          
## ape                  "R (>= 3.2.0)"                                                                                                                                                                                                                         
## askpass              NA                                                                                                                                                                                                                                     
## assertthat           NA                                                                                                                                                                                                                                     
## backports            "R (>= 3.0.0)"                                                                                                                                                                                                                         
## base                 NA                                                                                                                                                                                                                                     
## base64enc            "R (>= 2.9.0)"                                                                                                                                                                                                                         
## beeswarm             NA                                                                                                                                                                                                                                     
## BH                   NA                                                                                                                                                                                                                                     
## bindr                NA                                                                                                                                                                                                                                     
## bindrcpp             NA                                                                                                                                                                                                                                     
## Biobase              "R (>= 2.10), BiocGenerics (>= 0.27.1), utils"                                                                                                                                                                                         
## BiocGenerics         "methods, utils, graphics, stats, parallel"                                                                                                                                                                                            
## BiocManager          NA                                                                                                                                                                                                                                     
## BiocParallel         "methods"                                                                                                                                                                                                                              
## BiocVersion          "R (>= 3.5.0), R (< 3.6.0)"                                                                                                                                                                                                            
## biomformat           "R (>= 3.2), methods"                                                                                                                                                                                                                  
## Biostrings           "R (>= 3.5.0), methods, BiocGenerics, S4Vectors, IRanges,\nXVector"                                                                                                                                                                    
## bit                  "R (>= 2.9.2)"                                                                                                                                                                                                                         
## bit64                "R (>= 3.0.1), bit (>= 1.1-12), utils, methods, stats"                                                                                                                                                                                 
## bitops               NA                                                                                                                                                                                                                                     
## bizarro              NA                                                                                                                                                                                                                                     
## boot                 "R (>= 3.0.0), graphics, stats"                                                                                                                                                                                                        
## brew                 NA                                                                                                                                                                                                                                     
## broom                "R (>= 3.1)"                                                                                                                                                                                                                           
## callr                NA                                                                                                                                                                                                                                     
## car                  "R (>= 3.5.0), carData (>= 3.0-0)"                                                                                                                                                                                                     
## carData              "R (>= 3.0)"                                                                                                                                                                                                                           
## caret                "R (>= 3.2.0), lattice (>= 0.20), ggplot2"                                                                                                                                                                                             
## caTools              "R (>= 2.2.0)"                                                                                                                                                                                                                         
## cellranger           "R (>= 3.0.0)"                                                                                                                                                                                                                         
## class                "R (>= 3.0.0), stats, utils"                                                                                                                                                                                                           
## cli                  "R (>= 2.10)"                                                                                                                                                                                                                          
## cliapp               NA                                                                                                                                                                                                                                     
## clipr                NA                                                                                                                                                                                                                                     
## clisymbols           NA                                                                                                                                                                                                                                     
## cluster              "R (>= 3.3.0)"                                                                                                                                                                                                                         
## codetools            "R (>= 2.1)"                                                                                                                                                                                                                           
## colorspace           "R (>= 3.0.0), methods"                                                                                                                                                                                                                
## commonmark           NA                                                                                                                                                                                                                                     
## compiler             NA                                                                                                                                                                                                                                     
## conflicted           "R (>= 3.2)"                                                                                                                                                                                                                           
## corpcor              "R (>= 3.0.2)"                                                                                                                                                                                                                         
## covr                 "R (>= 3.1.0), methods"                                                                                                                                                                                                                
## cowplot              "R (>= 3.5.0)"                                                                                                                                                                                                                         
## cranlogs             NA                                                                                                                                                                                                                                     
## crayon               NA                                                                                                                                                                                                                                     
## crosstalk            NA                                                                                                                                                                                                                                     
## curl                 "R (>= 3.0.0)"                                                                                                                                                                                                                         
## cyclocomp            NA                                                                                                                                                                                                                                     
## cyl                  NA                                                                                                                                                                                                                                     
## dada2                "R (>= 3.2.0), Rcpp (>= 0.11.2), methods (>= 3.2.0)"                                                                                                                                                                                   
## data.table           "R (>= 3.1.0)"                                                                                                                                                                                                                         
## datasets             NA                                                                                                                                                                                                                                     
## DBI                  "R (>= 3.0.0), methods"                                                                                                                                                                                                                
## dbplyr               "R (>= 3.1)"                                                                                                                                                                                                                           
## decontam             "R (>= 3.4.1), methods (>= 3.4.1)"                                                                                                                                                                                                     
## DelayedArray         "R (>= 3.4), methods, stats4, matrixStats, BiocGenerics (>=\n0.27.1), S4Vectors (>= 0.19.15), IRanges (>= 2.11.17),\nBiocParallel"                                                                                                     
## DEoptimR             NA                                                                                                                                                                                                                                     
## desc                 "R (>= 3.1.0)"                                                                                                                                                                                                                         
## devtools             "R (>= 3.0.2), usethis (>= 1.5.0)"                                                                                                                                                                                                     
## digest               "R (>= 3.1.0)"                                                                                                                                                                                                                         
## docopt               NA                                                                                                                                                                                                                                     
## doParallel           "R (>= 2.14.0), foreach(>= 1.2.0), iterators(>= 1.0.0),\nparallel, utils"                                                                                                                                                              
## dotCall64            "R (>= 3.1)"                                                                                                                                                                                                                           
## dplyr                "R (>= 3.2.0)"                                                                                                                                                                                                                         
## DT                   NA                                                                                                                                                                                                                                     
## e1071                NA                                                                                                                                                                                                                                     
## ellipsis             "R (>= 3.2)"                                                                                                                                                                                                                           
## EMD                  "R (>= 3.0), fields (>= 6.9.1), locfit (>= 1.5-8)"                                                                                                                                                                                     
## enc                  "R (>= 3.1)"                                                                                                                                                                                                                           
## evaluate             "R (>= 3.0.2)"                                                                                                                                                                                                                         
## fansi                "R (>= 3.1.0)"                                                                                                                                                                                                                         
## fastmap              NA                                                                                                                                                                                                                                     
## fastmatch            NA                                                                                                                                                                                                                                     
## fields               "R (>= 3.0), methods, spam, maps"                                                                                                                                                                                                      
## filelock             NA                                                                                                                                                                                                                                     
## flexdashboard        "R (>= 3.0.2)"                                                                                                                                                                                                                         
## flowCore             "R (>= 3.0.2)"                                                                                                                                                                                                                         
## flowPeaks            "R (>= 2.12.0)"                                                                                                                                                                                                                        
## foofactor            NA                                                                                                                                                                                                                                     
## forcats              "R (>= 3.1)"                                                                                                                                                                                                                           
## foreach              "R (>= 2.5.0)"                                                                                                                                                                                                                         
## foreign              "R (>= 3.0.0)"                                                                                                                                                                                                                         
## formatR              "R (>= 3.0.2)"                                                                                                                                                                                                                         
## fs                   "R (>= 3.1)"                                                                                                                                                                                                                           
## futile.logger        "R (>= 3.0.0)"                                                                                                                                                                                                                         
## futile.options       "R (>= 2.8.0)"                                                                                                                                                                                                                         
## generics             "R (>= 3.1)"                                                                                                                                                                                                                           
## GenomeInfoDb         "R (>= 3.1), methods, BiocGenerics (>= 0.13.8), S4Vectors (>=\n0.17.25), IRanges (>= 2.13.12)"                                                                                                                                         
## GenomeInfoDbData     "R (>= 3.3)"                                                                                                                                                                                                                           
## GenomicAlignments    "R (>= 2.10), methods, BiocGenerics (>= 0.15.3), S4Vectors (>=\n0.19.11), IRanges (>= 2.15.12), GenomeInfoDb (>= 1.13.1),\nGenomicRanges (>= 1.33.4), SummarizedExperiment (>= 1.9.13),\nBiostrings (>= 2.47.6), Rsamtools (>= 1.31.2)"
## GenomicRanges        "R (>= 2.10), methods, stats4, BiocGenerics (>= 0.25.3),\nS4Vectors (>= 0.19.11), IRanges (>= 2.15.12), GenomeInfoDb (>=\n1.15.2)"                                                                                                     
## geometry             "R (>= 3.0.0)"                                                                                                                                                                                                                         
## GGally               "R (>= 3.1), ggplot2 (> 2.2.0)"                                                                                                                                                                                                        
## ggbeeswarm           "R (>= 3.0.0), ggplot2 (>= 2.0)"                                                                                                                                                                                                       
## ggplot2              "R (>= 3.2)"                                                                                                                                                                                                                           
## ggridges             "R (>= 3.2)"                                                                                                                                                                                                                           
## gh                   NA                                                                                                                                                                                                                                     
## git2r                "R (>= 3.1)"                                                                                                                                                                                                                           
## glue                 "R (>= 3.1)"                                                                                                                                                                                                                           
## googlesheets         "R (>= 3.2.0)"                                                                                                                                                                                                                         
## gower                NA                                                                                                                                                                                                                                     
## graph                "R (>= 2.10), methods, BiocGenerics (>= 0.13.11)"                                                                                                                                                                                      
## graphics             NA                                                                                                                                                                                                                                     
## grDevices            NA                                                                                                                                                                                                                                     
## grid                 NA                                                                                                                                                                                                                                     
## gridExtra            NA                                                                                                                                                                                                                                     
## gtable               "R (>= 3.0)"                                                                                                                                                                                                                           
## haven                "R (>= 3.2)"                                                                                                                                                                                                                           
## here                 NA                                                                                                                                                                                                                                     
## hexbin               "R (>= 2.0.1), methods"                                                                                                                                                                                                                
## highr                "R (>= 3.2.3)"                                                                                                                                                                                                                         
## hms                  NA                                                                                                                                                                                                                                     
## htmltools            "R (>= 2.14.1)"                                                                                                                                                                                                                        
## htmlwidgets          NA                                                                                                                                                                                                                                     
## httpuv               "R (>= 2.15.1)"                                                                                                                                                                                                                        
## httr                 "R (>= 3.2)"                                                                                                                                                                                                                           
## hwriter              "R (>= 2.6.0)"                                                                                                                                                                                                                         
## igraph               "methods"                                                                                                                                                                                                                              
## ini                  NA                                                                                                                                                                                                                                     
## ipred                "R (>= 2.10)"                                                                                                                                                                                                                          
## ips                  "R (>= 3.2.0), ape"                                                                                                                                                                                                                    
## IRanges              "R (>= 3.1.0), methods, utils, stats, BiocGenerics (>= 0.25.3),\nS4Vectors (>= 0.19.11)"                                                                                                                                               
## itdepends            NA                                                                                                                                                                                                                                     
## iterators            "R (>= 2.5.0), utils"                                                                                                                                                                                                                  
## jsonlite             "methods"                                                                                                                                                                                                                              
## kernlab              "R (>= 2.10)"                                                                                                                                                                                                                          
## KernSmooth           "R (>= 2.5.0), stats"                                                                                                                                                                                                                  
## kmer                 NA                                                                                                                                                                                                                                     
## knitr                "R (>= 3.2.3)"                                                                                                                                                                                                                         
## labeling             NA                                                                                                                                                                                                                                     
## labrador             "R (>= 3.4.3)"                                                                                                                                                                                                                         
## labradorbase         NA                                                                                                                                                                                                                                     
## lambda.r             "R (>= 3.0.0)"                                                                                                                                                                                                                         
## later                NA                                                                                                                                                                                                                                     
## lattice              "R (>= 3.0.0)"                                                                                                                                                                                                                         
## latticeExtra         "R (>= 2.10.0), lattice, RColorBrewer"                                                                                                                                                                                                 
## lava                 "R (>= 3.0)"                                                                                                                                                                                                                           
## lazyeval             "R (>= 3.1.0)"                                                                                                                                                                                                                         
## lifecycle            "R (>= 3.2)"                                                                                                                                                                                                                           
## linprog              "R (>= 2.4.0), lpSolve"                                                                                                                                                                                                                
## lintr                "R (>= 3.2)"                                                                                                                                                                                                                           
## lme4                 "R (>= 3.2.0), Matrix (>= 1.2-1), methods, stats"                                                                                                                                                                                      
## lobstr               "R (>= 3.2)"                                                                                                                                                                                                                           
## locfit               "R (>= 2.0.1)"                                                                                                                                                                                                                         
## lpSolve              NA                                                                                                                                                                                                                                     
## lubridate            "methods, R (>= 3.0.0)"                                                                                                                                                                                                                
## magic                "R (>= 2.10), abind"                                                                                                                                                                                                                   
## magrittr             NA                                                                                                                                                                                                                                     
## manipulateWidget     NA                                                                                                                                                                                                                                     
## maps                 "R (>= 3.0.0)"                                                                                                                                                                                                                         
## maptools             "R (>= 2.10), sp (>= 1.0-11)"                                                                                                                                                                                                          
## markdown             "R (>= 2.11.1)"                                                                                                                                                                                                                        
## MASS                 "R (>= 3.1.0), grDevices, graphics, stats, utils"                                                                                                                                                                                      
## Matrix               "R (>= 3.2.0)"                                                                                                                                                                                                                         
## MatrixModels         "R (>= 3.0.1)"                                                                                                                                                                                                                         
## matrixStats          "R (>= 2.12.0)"                                                                                                                                                                                                                        
## mean2                NA                                                                                                                                                                                                                                     
## memoise              NA                                                                                                                                                                                                                                     
## methods              NA                                                                                                                                                                                                                                     
## mgcv                 "R (>= 2.14.0), nlme (>= 3.1-64)"                                                                                                                                                                                                      
## mime                 NA                                                                                                                                                                                                                                     
## miniUI               NA                                                                                                                                                                                                                                     
## minpack.lm           NA                                                                                                                                                                                                                                     
## minqa                NA                                                                                                                                                                                                                                     
## ModelMetrics         "R (>= 3.2.2)"                                                                                                                                                                                                                         
## modelr               "R (>= 3.2)"                                                                                                                                                                                                                           
## MPN                  "R (>= 3.4.0)"                                                                                                                                                                                                                         
## multtest             "R (>= 2.10), methods, BiocGenerics, Biobase"                                                                                                                                                                                          
## munsell              NA                                                                                                                                                                                                                                     
## mvtnorm              "R(>= 3.5.0)"                                                                                                                                                                                                                          
## new                  NA                                                                                                                                                                                                                                     
## nlme                 "R (>= 3.4.0)"                                                                                                                                                                                                                         
## nloptr               NA                                                                                                                                                                                                                                     
## nnet                 "R (>= 2.14.0), stats, utils"                                                                                                                                                                                                          
## numDeriv             "R (>= 2.11.1)"                                                                                                                                                                                                                        
## openssl              NA                                                                                                                                                                                                                                     
## openxlsx             "R (>= 3.3.0)"                                                                                                                                                                                                                         
## parallel             NA                                                                                                                                                                                                                                     
## pbkrtest             "R (>= 3.2.3), lme4 (>= 1.1.10)"                                                                                                                                                                                                       
## pcaPP                NA                                                                                                                                                                                                                                     
## permute              "R (>= 2.14.0)"                                                                                                                                                                                                                        
## phangorn             "R (>= 3.2.0), ape (>= 5.0)"                                                                                                                                                                                                           
## phylogram            NA                                                                                                                                                                                                                                     
## phyloseq             "R (>= 3.3.0)"                                                                                                                                                                                                                         
## pillar               NA                                                                                                                                                                                                                                     
## pkgbuild             "R (>= 3.1)"                                                                                                                                                                                                                           
## pkgcache             "R (>= 3.1)"                                                                                                                                                                                                                           
## pkgconfig            NA                                                                                                                                                                                                                                     
## pkgload              NA                                                                                                                                                                                                                                     
## plogr                NA                                                                                                                                                                                                                                     
## plotly               "R (>= 3.2.0), ggplot2 (>= 3.0.0)"                                                                                                                                                                                                     
## plyr                 "R (>= 3.1.0)"                                                                                                                                                                                                                         
## praise               NA                                                                                                                                                                                                                                     
## prettycode           NA                                                                                                                                                                                                                                     
## prettyunits          NA                                                                                                                                                                                                                                     
## processx             NA                                                                                                                                                                                                                                     
## prodlim              "R (>= 2.9.0)"                                                                                                                                                                                                                         
## progress             NA                                                                                                                                                                                                                                     
## promises             NA                                                                                                                                                                                                                                     
## pryr                 "R (>= 3.1.0)"                                                                                                                                                                                                                         
## ps                   "R (>= 3.1)"                                                                                                                                                                                                                           
## pspline              "R (>= 2.0.0), stats, graphics"                                                                                                                                                                                                        
## purrr                "R (>= 3.1)"                                                                                                                                                                                                                           
## qpcR                 "R (>= 2.13.0), MASS, minpack.lm, rgl, robustbase, Matrix"                                                                                                                                                                             
## quadprog             "R (>= 3.1.0)"                                                                                                                                                                                                                         
## quantreg             "R (>= 2.6), stats, SparseM"                                                                                                                                                                                                           
## R6                   "R (>= 3.0)"                                                                                                                                                                                                                           
## rappdirs             "R (>= 2.14), methods"                                                                                                                                                                                                                 
## rcmdcheck            NA                                                                                                                                                                                                                                     
## RColorBrewer         "R (>= 2.0.0)"                                                                                                                                                                                                                         
## Rcpp                 "R (>= 3.0.0)"                                                                                                                                                                                                                         
## RcppEigen            "R (>= 2.15.1)"                                                                                                                                                                                                                        
## RcppParallel         "R (>= 3.0.2)"                                                                                                                                                                                                                         
## RcppProgress         NA                                                                                                                                                                                                                                     
## RcppRoll             "R (>= 2.15.1)"                                                                                                                                                                                                                        
## RCurl                "R (>= 3.0.0), methods, bitops"                                                                                                                                                                                                        
## readr                "R (>= 3.1)"                                                                                                                                                                                                                           
## readxl               NA                                                                                                                                                                                                                                     
## recipes              "R (>= 3.1), dplyr"                                                                                                                                                                                                                    
## rematch              NA                                                                                                                                                                                                                                     
## rematch2             NA                                                                                                                                                                                                                                     
## remotes              "R (>= 3.0.0)"                                                                                                                                                                                                                         
## reprex               "R (>= 3.1)"                                                                                                                                                                                                                           
## requirements         "R (>= 3.1)"                                                                                                                                                                                                                           
## reshape              "R (>= 2.6.1)"                                                                                                                                                                                                                         
## reshape2             "R (>= 3.1)"                                                                                                                                                                                                                           
## rex                  NA                                                                                                                                                                                                                                     
## rgl                  "R (>= 3.2.0)"                                                                                                                                                                                                                         
## rhdf5                "R (>= 3.5.0), methods"                                                                                                                                                                                                                
## Rhdf5lib             NA                                                                                                                                                                                                                                     
## rio                  "R (>= 2.15.0)"                                                                                                                                                                                                                        
## rlang                "R (>= 3.2.0)"                                                                                                                                                                                                                         
## rmarkdown            "R (>= 3.0)"                                                                                                                                                                                                                           
## robustbase           "R (>= 3.1.0)"                                                                                                                                                                                                                         
## roxygen2             "R (>= 3.1)"                                                                                                                                                                                                                           
## roxygen2md           NA                                                                                                                                                                                                                                     
## rpart                "R (>= 2.15.0), graphics, stats, grDevices"                                                                                                                                                                                            
## rpivotTable          "R (>= 3.2.0)"                                                                                                                                                                                                                         
## rprojroot            "R (>= 3.0.0)"                                                                                                                                                                                                                         
## rrcov                "R (>= 2.10), robustbase (>= 0.92.1), methods"                                                                                                                                                                                         
## Rsamtools            "methods, GenomeInfoDb (>= 1.1.3), GenomicRanges (>= 1.31.8),\nBiostrings (>= 2.47.6)"                                                                                                                                                 
## rstudioapi           NA                                                                                                                                                                                                                                     
## rversions            NA                                                                                                                                                                                                                                     
## rvest                "R (>= 3.2), xml2"                                                                                                                                                                                                                     
## S4Vectors            "R (>= 3.3.0), methods, utils, stats, stats4, BiocGenerics (>=\n0.23.3)"                                                                                                                                                               
## scales               "R (>= 3.1)"                                                                                                                                                                                                                           
## segmented            NA                                                                                                                                                                                                                                     
## selectr              "R (>= 3.0)"                                                                                                                                                                                                                           
## seqinr               "R (>= 2.10.0)"                                                                                                                                                                                                                        
## sessioninfo          NA                                                                                                                                                                                                                                     
## sfsmisc              "R (>= 3.2.0)"                                                                                                                                                                                                                         
## shiny                "R (>= 3.0.2), methods"                                                                                                                                                                                                                
## ShortRead            "BiocGenerics (>= 0.23.3), BiocParallel, Biostrings (>=\n2.47.6), Rsamtools (>= 1.31.2), GenomicAlignments (>= 1.15.6)"                                                                                                                
## sloop                "R (>= 3.3)"                                                                                                                                                                                                                           
## snow                 "R (>= 2.13.1), utils"                                                                                                                                                                                                                 
## sourcetools          "R (>= 3.0.2)"                                                                                                                                                                                                                         
## sp                   "R (>= 3.0.0), methods"                                                                                                                                                                                                                
## spam                 "R (>= 3.1), dotCall64, grid, methods"                                                                                                                                                                                                 
## SparseM              "R (>= 2.15), methods"                                                                                                                                                                                                                 
## spatial              "R (>= 3.0.0), graphics, stats, utils"                                                                                                                                                                                                 
## splines              NA                                                                                                                                                                                                                                     
## SQUAREM              "R (>= 3.0)"                                                                                                                                                                                                                           
## stats                NA                                                                                                                                                                                                                                     
## stats4               NA                                                                                                                                                                                                                                     
## stringdist           "R (>= 2.15.3)"                                                                                                                                                                                                                        
## stringi              "R (>= 2.14)"                                                                                                                                                                                                                          
## stringr              "R (>= 3.1)"                                                                                                                                                                                                                           
## SummarizedExperiment "R (>= 3.2), methods, GenomicRanges (>= 1.33.6), Biobase,\nDelayedArray (>= 0.3.20)"                                                                                                                                                   
## survival             "R (>= 2.13.0)"                                                                                                                                                                                                                        
## sys                  NA                                                                                                                                                                                                                                     
## tcltk                NA                                                                                                                                                                                                                                     
## testns               NA                                                                                                                                                                                                                                     
## testthat             "R (>= 3.1)"                                                                                                                                                                                                                           
## tibble               "R (>= 3.1.0)"                                                                                                                                                                                                                         
## tidyr                "R (>= 3.1)"                                                                                                                                                                                                                           
## tidyselect           "R (>= 3.1)"                                                                                                                                                                                                                           
## tidyverse            NA                                                                                                                                                                                                                                     
## timeDate             "R (>= 2.15.1), graphics, utils, stats, methods"                                                                                                                                                                                       
## tinytex              NA                                                                                                                                                                                                                                     
## tools                NA                                                                                                                                                                                                                                     
## UpSetR               "R (>= 3.0)"                                                                                                                                                                                                                           
## usethis              "R (>= 3.2)"                                                                                                                                                                                                                           
## utf8                 "R (>= 2.10)"                                                                                                                                                                                                                          
## utils                NA                                                                                                                                                                                                                                     
## uuid                 "R (>= 2.9.0)"                                                                                                                                                                                                                         
## vctrs                "R (>= 3.2)"                                                                                                                                                                                                                           
## vegan                "permute (>= 0.9-0), lattice, R (>= 3.4.0)"                                                                                                                                                                                            
## vipor                "R (>= 3.0.0)"                                                                                                                                                                                                                         
## viridisLite          "R (>= 2.10)"                                                                                                                                                                                                                          
## wbr                  "parallel"                                                                                                                                                                                                                             
## wbrlims              "R (>= 3.3.0)"                                                                                                                                                                                                                         
## webshot              "R (>= 3.0)"                                                                                                                                                                                                                           
## whisker              NA                                                                                                                                                                                                                                     
## withr                "R (>= 3.0.2)"                                                                                                                                                                                                                         
## xfun                 NA                                                                                                                                                                                                                                     
## XML                  "R (>= 2.13.0), methods, utils"                                                                                                                                                                                                        
## xml2                 "R (>= 3.1.0)"                                                                                                                                                                                                                         
## xmlparsedata         "R (>= 3.0.0)"                                                                                                                                                                                                                         
## xopen                "R (>= 3.1)"                                                                                                                                                                                                                           
## xtable               "R (>= 2.10.0)"                                                                                                                                                                                                                        
## XVector              "R (>= 2.8.0), methods, BiocGenerics (>= 0.19.2), S4Vectors (>=\n0.19.15), IRanges (>= 2.15.12)"                                                                                                                                       
## yaml                 NA                                                                                                                                                                                                                                     
## zeallot              NA                                                                                                                                                                                                                                     
## zip                  NA                                                                                                                                                                                                                                     
## zlibbioc             NA                                                                                                                                                                                                                                     
## zoo                  "R (>= 3.1.0), stats"                                                                                                                                                                                                                  
##                      Imports                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## abind                "methods, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## ade4                 "graphics, grDevices, methods, stats, utils, MASS"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## ape                  "nlme, lattice, graphics, methods, stats, tools, utils,\nparallel, Rcpp (>= 0.12.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## askpass              "sys (>= 2.1)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## assertthat           "tools"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## backports            "utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## base                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## base64enc            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## beeswarm             "stats, graphics, grDevices, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## BH                   NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## bindr                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## bindrcpp             "bindr (>= 0.1.1), Rcpp (>= 0.12.16)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## Biobase              "methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## BiocGenerics         "methods, utils, graphics, stats, parallel"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## BiocManager          "utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## BiocParallel         "stats, utils, futile.logger, parallel, snow"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## BiocVersion          NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## biomformat           "plyr (>= 1.8), jsonlite (>= 0.9.16), Matrix (>= 1.2), rhdf5"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## Biostrings           "graphics, methods, stats, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## bit                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## bit64                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## bitops               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## bizarro              "purrr,\nstringr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## boot                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## brew                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## broom                "backports, dplyr, generics (>= 0.0.2), methods, nlme, purrr,\nreshape2, stringr, tibble, tidyr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## callr                "processx (>= 3.4.0), R6, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## car                  "abind, MASS, mgcv, nnet, pbkrtest (>= 0.4-4), quantreg,\ngrDevices, utils, stats, graphics, maptools, rio, lme4, nlme"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## carData              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## caret                "foreach, methods, plyr, ModelMetrics (>= 1.1.0), nlme,\nreshape2, stats, stats4, utils, grDevices, recipes (>= 0.1.4),\nwithr (>= 2.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## caTools              "bitops"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## cellranger           "rematch, tibble"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## class                "MASS"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## cli                  "assertthat, crayon (>= 1.3.4), methods, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## cliapp               "cli, crayon, fansi, glue (>= 1.3.0), prettycode, progress (>=\n1.2.0), R6, selectr, utils, withr, xml2"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## clipr                "utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## clisymbols           NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## cluster              "graphics, grDevices, stats, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## codetools            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## colorspace           "graphics, grDevices, stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## commonmark           NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## compiler             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## conflicted           "rlang (>= 0.3.4), memoise"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## corpcor              "stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## covr                 "digest, stats, utils, jsonlite, rex, httr, crayon, withr (>=\n1.0.2), yaml"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## cowplot              "ggplot2 (> 2.2.1), grid, gtable, grDevices, methods, rlang,\nscales, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## cranlogs             "httr, jsonlite"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## crayon               "grDevices, methods, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## crosstalk            "htmltools (>= 0.3.5), jsonlite, lazyeval, R6, shiny (>= 0.11),\nggplot2"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## curl                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## cyclocomp            "callr, crayon, desc, remotes, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## cyl                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## dada2                "Biostrings (>= 2.42.1), ggplot2 (>= 2.1.0), data.table (>=\n1.9.4), reshape2 (>= 1.4.1), ShortRead (>= 1.32.0),\nRcppParallel (>= 4.3.0), parallel (>= 3.2.0), IRanges (>=\n2.6.0), XVector (>= 0.16.0), BiocGenerics (>= 0.22.0)"                                                                                                                                                                                                                                                                                                                                                                                                                         
## data.table           "methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## datasets             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## DBI                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## dbplyr               "assertthat (>= 0.2.0), DBI (>= 1.0.0), dplyr (>= 0.8.0), glue\n(>= 1.2.0), methods, purrr (>= 0.2.5), R6 (>= 2.2.2), rlang (>=\n0.2.0), tibble (>= 1.4.2), tidyselect (>= 0.2.4), utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## decontam             "ggplot2 (>= 2.1.0), reshape2 (>= 1.4.1), stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## DelayedArray         "stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## DEoptimR             "stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## desc                 "assertthat, utils, R6, crayon, rprojroot"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## devtools             "callr, cli, covr (>= 3.2.0), crayon, desc, digest, DT,\nellipsis (>= 0.3.0), glue, git2r (>= 0.23.0), httr (>= 0.4),\njsonlite, memoise (>= 1.0.0), pkgbuild (>= 1.0.3), pkgload (>=\n1.0.2), rcmdcheck (>= 1.3.3), remotes (>= 2.1.0), rlang,\nroxygen2 (>= 6.1.1), rstudioapi (>= 0.7), rversions,\nsessioninfo (>= 1.1.1), stats, testthat (>= 2.1.1), tools,\nutils, withr"                                                                                                                                                                                                                                                                            
## digest               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## docopt               "methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## doParallel           NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## dotCall64            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## dplyr                "assertthat (>= 0.2.0), glue (>= 1.3.0), magrittr (>= 1.5),\nmethods, pkgconfig, R6, Rcpp (>= 1.0.1), rlang (>= 0.4.0),\ntibble (>= 2.0.0), tidyselect (>= 0.2.5), utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## DT                   "htmltools (>= 0.3.6), htmlwidgets (>= 1.3), jsonlite (>=\n0.9.16), magrittr, crosstalk, promises"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## e1071                "graphics, grDevices, class, stats, methods, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## ellipsis             "rlang (>= 0.3.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## EMD                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## enc                  "methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## evaluate             "methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## fansi                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## fastmap              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## fastmatch            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## fields               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## filelock             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## flexdashboard        "tools, jsonlite, htmltools, knitr (>= 1.13), htmlwidgets (>=\n0.6), rmarkdown (>= 1.0), shiny (>= 0.13)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## flowCore             "Biobase, BiocGenerics (>= 0.1.14), graph, grDevices, graphics,\nmethods, rrcov, stats, utils, stats4, corpcor, Rcpp,\nmatrixStats, MASS"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## flowPeaks            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## foofactor            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## forcats              "ellipsis, magrittr, rlang, tibble"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## foreach              "codetools, utils, iterators"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## foreign              "methods, utils, stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## formatR              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## fs                   "methods, Rcpp"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## futile.logger        "utils, lambda.r (>= 1.1.0), futile.options"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## futile.options       NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## generics             "methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## GenomeInfoDb         "stats, stats4, utils, RCurl, GenomeInfoDbData"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## GenomeInfoDbData     NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## GenomicAlignments    "methods, utils, stats, BiocGenerics, S4Vectors, IRanges,\nGenomicRanges, Biostrings, Rsamtools, BiocParallel"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## GenomicRanges        "utils, stats, XVector (>= 0.19.8)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## geometry             "magic, Rcpp, lpSolve, linprog"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## GGally               "grDevices, grid, gtable (>= 0.2.0), plyr (>= 1.8.3), progress,\nRColorBrewer, reshape (>= 0.8.5), utils, rlang"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## ggbeeswarm           "beeswarm, vipor"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## ggplot2              "digest, grDevices, grid, gtable (>= 0.1.1), lazyeval, MASS,\nmgcv, reshape2, rlang (>= 0.3.0), scales (>= 0.5.0), stats,\ntibble, viridisLite, withr (>= 2.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## ggridges             "ggplot2 (>= 2.2.0), grid (>= 3.0.0), plyr (>= 1.8.0), scales\n(>= 0.4.1), withr (>= 2.1.1)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## gh                   "ini, jsonlite, httr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## git2r                "graphics, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## glue                 "methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## googlesheets         "cellranger (>= 1.0.0), dplyr (>= 0.4.2), httr (>= 1.1.0),\njsonlite, purrr, readr (>= 0.2.2), stats, stringr, tibble,\ntidyr, utils, xml2 (>= 1.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## gower                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## graph                "stats, stats4, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## graphics             "grDevices"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## grDevices            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## grid                 "grDevices, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## gridExtra            "gtable, grid, grDevices, graphics, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## gtable               "grid"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## haven                "forcats (>= 0.2.0), hms, Rcpp (>= 0.11.4), readr (>= 0.1.0),\ntibble"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## here                 "rprojroot (>= 1.2)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## hexbin               "lattice, grid, graphics, grDevices, stats, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## highr                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## hms                  "methods, pkgconfig, rlang, vctrs (>= 0.2.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## htmltools            "utils, digest, Rcpp, rlang"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## htmlwidgets          "grDevices, htmltools (>= 0.3), jsonlite (>= 0.9.16), yaml"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## httpuv               "Rcpp (>= 0.11.0), utils, R6, promises, later (>= 0.8.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## httr                 "curl (>= 3.0.0), jsonlite, mime, openssl (>= 0.8), R6"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## hwriter              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## igraph               "graphics, grDevices, magrittr, Matrix, pkgconfig (>= 2.0.0),\nstats, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## ini                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## ipred                "rpart (>= 3.1-8), MASS, survival, nnet, class, prodlim"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## ips                  "phangorn, plyr, seqinr, XML"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## IRanges              "stats4"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## itdepends            "dplyr, forcats, ggplot2, magrittr, memoise, stringr, lintr,\nxml2, rvest, tibble, rlang, requirements, purrr, pkgcache,\ncranlogs, desc, prettyunits, rematch2, rprojroot, xmlparsedata,\ntools, stats, utils, gh"                                                                                                                                                                                                                                                                                                                                                                                                                                         
## iterators            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## jsonlite             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## kernlab              "methods, stats, grDevices, graphics"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## KernSmooth           NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## kmer                 "openssl, phylogram, Rcpp (>= 0.12.13)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## knitr                "evaluate (>= 0.10), highr, markdown, stringr (>= 0.6), yaml\n(>= 2.1.19), methods, xfun, tools"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## labeling             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## labrador             "BiocGenerics (>= 0.22.0),\ncaret (>= 6.0.78),\ndata.table (>= 1.10.4.3),\ndplyr (>= 0.7.4),\nDT (>= 0.2),\ndoParallel (>= 1.0.11),\ne1071 (>= 1.7.2),\nEMD (>= 1.5.7),\nflowCore (>= 1.42.2),\nflowPeaks (>= 1.20.0),\nGGally (>= 1.3.2),\ngeometry (>= 0.3.6),\nggplot2 (>= 2.2.1),\ngrDevices (>= 3.4.3),\njsonlite (>= 1.5),\nkernlab (>= 0.9.25),\nlubridate (>= 1.7.1),\nmagrittr (>= 1.5),\nMASS (>= 7.3.47),\nmethods (>= 3.4.3),\nminpack.lm (>= 1.2.1),\npspline (>= 1.0.18),\nR6 (>= 2.2.2),\nRColorBrewer (>= 1.1.2),\nrmarkdown (>= 1.9),\nrobustbase (>= 0.92.8),\nscales (>= 0.5.0),\nshiny (>= 1.0.5),\nwbrlims (>= 0.8.0),\nzoo (>= 1.8.3)"
## labradorbase         NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## lambda.r             "formatR"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## later                "Rcpp (>= 0.12.9), rlang"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## lattice              "grid, grDevices, graphics, stats, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## latticeExtra         "grid, stats, utils, grDevices"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## lava                 "grDevices, graphics, methods, numDeriv, stats, survival,\nSQUAREM, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## lazyeval             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## lifecycle            "glue, rlang (>= 0.4.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## linprog              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## lintr                "rex, crayon, codetools, cyclocomp, stringdist, testthat,\ndigest, rstudioapi (>= 0.2), httr (>= 1.2.1), jsonlite, knitr,\nstats, utils, xml2 (>= 1.0.0), xmlparsedata (>= 1.0.3)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## lme4                 "graphics, grid, splines, utils, parallel, MASS, lattice, boot,\nnlme (>= 3.1-123), minqa (>= 1.1.15), nloptr (>= 1.0.4)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## lobstr               "crayon, Rcpp, rlang (>= 0.3.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## locfit               "lattice"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## lpSolve              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## lubridate            "stringr, Rcpp (>= 0.12.13),"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## magic                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## magrittr             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## manipulateWidget     "shiny (>= 1.0.3), miniUI, htmltools, htmlwidgets, knitr,\nmethods, tools, base64enc, grDevices, codetools, webshot"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## maps                 "graphics, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## maptools             "foreign (>= 0.8), methods, grid, lattice, stats, utils,\ngrDevices"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## markdown             "utils, xfun, mime (>= 0.3)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## MASS                 "methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## Matrix               "methods, graphics, grid, stats, utils, lattice"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## MatrixModels         "stats, methods, Matrix (>= 1.1-5)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## matrixStats          NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## mean2                "lubridate,\nvctrs"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## memoise              "digest (>= 0.6.3)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## methods              "utils, stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## mgcv                 "methods, stats, graphics, Matrix, splines, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## mime                 "tools"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## miniUI               "shiny (>= 0.13), htmltools (>= 0.3), utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## minpack.lm           NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## minqa                "Rcpp (>= 0.9.10)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## ModelMetrics         "Rcpp, data.table"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## modelr               "broom, dplyr, magrittr, purrr (>= 0.2.2), rlang (>= 0.2.0),\ntibble, tidyr (>= 0.8.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## MPN                  "stats (>= 3.4.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## multtest             "survival, MASS, stats4"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## munsell              "colorspace, methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## mvtnorm              "stats, methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## new                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## nlme                 "graphics, stats, utils, lattice"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## nloptr               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## nnet                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## numDeriv             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## openssl              "askpass"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## openxlsx             "methods, Rcpp, grDevices, stats, utils, zip"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## parallel             "tools, compiler"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## pbkrtest             "Matrix (>= 1.2.3), parallel, MASS, methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## pcaPP                "mvtnorm"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## permute              "stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## phangorn             "quadprog, igraph (>= 1.0), Matrix, parallel, methods, utils,\nstats, graphics, grDevices, fastmatch, magrittr, Rcpp (>=\n0.12.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## phylogram            "ape (>= 4.0), methods, stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## phyloseq             "ade4 (>= 1.7.4), ape (>= 5.0), Biobase (>= 2.36.2),\nBiocGenerics (>= 0.22.0), biomformat (>= 1.0.0), Biostrings (>=\n2.40.0), cluster (>= 2.0.4), data.table (>= 1.10.4), foreach\n(>= 1.4.3), ggplot2 (>= 2.1.0), igraph (>= 1.0.1), methods (>=\n3.3.0), multtest (>= 2.28.0), plyr (>= 1.8.3), reshape2 (>=\n1.4.1), scales (>= 0.4.0), vegan (>= 2.5)"                                                                                                                                                                                                                                                                                                
## pillar               "cli, crayon (>= 1.3.4), fansi, rlang (>= 0.3.0), utf8 (>=\n1.1.0), vctrs"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## pkgbuild             "callr (>= 3.2.0), cli, crayon, desc, prettyunits, R6,\nrprojroot, withr (>= 2.1.2)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## pkgcache             "assertthat, cli, cliapp, curl (>= 3.2), crayon, digest,\nfilelock, glue, prettyunits, R6, rappdirs, rematch2, rlang,\ntibble, tools, utils, uuid, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## pkgconfig            "utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## pkgload              "desc, methods, pkgbuild, rlang, rprojroot, rstudioapi, utils,\nwithr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## plogr                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## plotly               "tools, scales, httr, jsonlite (>= 1.6), magrittr, digest,\nviridisLite, base64enc, htmltools (>= 0.3.6), htmlwidgets (>=\n1.3), tidyr, hexbin, RColorBrewer, dplyr, tibble, lazyeval (>=\n0.2.0), rlang, crosstalk, purrr, data.table, promises"                                                                                                                                                                                                                                                                                                                                                                                                           
## plyr                 "Rcpp (>= 0.11.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## praise               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## prettycode           "crayon, utils, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## prettyunits          "magrittr, assertthat, methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## processx             "ps (>= 1.2.0), R6, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## prodlim              "Rcpp (>= 0.11.5), stats, graphics, survival, KernSmooth, lava"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## progress             "hms, prettyunits, R6, crayon"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## promises             "R6, Rcpp, later, rlang, stats, magrittr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## pryr                 "stringr, codetools, methods, Rcpp (>= 0.11.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## ps                   "utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## pspline              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## purrr                "magrittr (>= 1.5), rlang (>= 0.3.1)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## qpcR                 "methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## quadprog             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## quantreg             "methods, graphics, Matrix, MatrixModels"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## R6                   NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## rappdirs             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## rcmdcheck            "callr (>= 3.1.1.9000), cli (>= 1.1.0), crayon, desc (>=\n1.2.0), digest, pkgbuild, prettyunits, R6, rprojroot,\nsessioninfo (>= 1.1.1), utils, withr, xopen"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## RColorBrewer         NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## Rcpp                 "methods, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## RcppEigen            "Matrix (>= 1.1-0), Rcpp (>= 0.11.0), stats, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## RcppParallel         NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## RcppProgress         NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## RcppRoll             "Rcpp"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## RCurl                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## readr                "Rcpp (>= 0.12.0.5), tibble, hms (>= 0.4.1), R6, clipr, crayon,\nmethods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## readxl               "cellranger, Rcpp (>= 0.12.18), tibble (>= 1.3.1), utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## recipes              "generics, glue, gower, ipred, lubridate, magrittr, Matrix,\npurrr (>= 0.2.3), rlang (>= 0.4.0), stats, tibble, tidyr (>=\n0.8.3), tidyselect (>= 0.2.5), timeDate, utils, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## rematch              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## rematch2             "tibble"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## remotes              "methods, stats, tools, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## reprex               "callr (>= 2.0.0), clipr (>= 0.4.0), fs, rlang, rmarkdown,\nutils, whisker, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## requirements         "rlang"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## reshape              "plyr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## reshape2             "plyr (>= 1.8.1), Rcpp, stringr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## rex                  "magrittr, lazyeval"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## rgl                  "graphics, grDevices, stats, utils, htmlwidgets, htmltools,\nknitr, jsonlite (>= 0.9.20), shiny, magrittr, crosstalk,\nmanipulateWidget (>= 0.9.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## rhdf5                "Rhdf5lib (>= 1.3.2)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## Rhdf5lib             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## rio                  "tools, stats, utils, foreign, haven (>= 1.1.0), curl (>= 0.6),\ndata.table (>= 1.9.8), readxl (>= 0.1.1), openxlsx, tibble"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## rlang                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## rmarkdown            "tools, utils, knitr (>= 1.22), yaml (>= 2.1.19), htmltools (>=\n0.3.5), evaluate (>= 0.13), base64enc, jsonlite, mime, tinytex\n(>= 0.11), xfun, methods, stringr (>= 1.2.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## robustbase           "stats, graphics, utils, methods, DEoptimR"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## roxygen2             "brew, commonmark, desc (>= 1.2.0), digest, methods, pkgload\n(>= 1.0.2), purrr, R6 (>= 2.1.2), Rcpp (>= 0.11.0), stringi,\nstringr (>= 1.0.0), utils, xml2"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## roxygen2md           "desc, devtools, enc, rex, rlang, tibble, usethis, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## rpart                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## rpivotTable          "htmlwidgets (>= 0.5)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## rprojroot            "backports"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## rrcov                "stats, stats4, mvtnorm, lattice, cluster, pcaPP"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## Rsamtools            "utils, BiocGenerics (>= 0.25.1), S4Vectors (>= 0.17.25),\nIRanges (>= 2.13.12), XVector (>= 0.19.7), zlibbioc, bitops,\nBiocParallel"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## rstudioapi           NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## rversions            "curl, xml2 (>= 1.0.0), utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## rvest                "httr (>= 0.5), magrittr, selectr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## S4Vectors            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## scales               "labeling, munsell (>= 0.5), R6, RColorBrewer, Rcpp,\nviridisLite"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## segmented            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## selectr              "methods, stringr, R6"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## seqinr               "ade4,segmented"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## sessioninfo          "cli, tools, utils, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## sfsmisc              "grDevices, methods, utils, stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## shiny                "utils, grDevices, httpuv (>= 1.5.2), mime (>= 0.3), jsonlite\n(>= 0.9.16), xtable, digest, htmltools (>= 0.4.0), R6 (>= 2.0),\nsourcetools, later (>= 1.0.0), promises (>= 1.1.0), tools,\ncrayon, rlang (>= 0.4.0), fastmap (>= 1.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                   
## ShortRead            "Biobase, S4Vectors (>= 0.17.25), IRanges (>= 2.13.12),\nGenomeInfoDb (>= 1.15.2), GenomicRanges (>= 1.31.8), hwriter,\nmethods, zlibbioc, lattice, latticeExtra,"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## sloop                "codetools, crayon, methods, purrr, rlang, tibble (>= 2.0.1)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## snow                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## sourcetools          NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## sp                   "utils, stats, graphics, grDevices, lattice, grid"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## spam                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## SparseM              "graphics, stats, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## spatial              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## splines              "graphics, stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## SQUAREM              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## stats                "utils, grDevices, graphics"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## stats4               "graphics, methods, stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## stringdist           "parallel"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## stringi              "tools, utils, stats"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## stringr              "glue (>= 1.2.0), magrittr, stringi (>= 1.1.7)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## SummarizedExperiment "utils, stats, tools, Matrix, BiocGenerics (>= 0.15.3),\nS4Vectors (>= 0.17.25), IRanges (>= 2.13.16), GenomeInfoDb (>=\n1.13.1)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## survival             "graphics, Matrix, methods, splines, stats, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## sys                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## tcltk                "utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## testns               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## testthat             "cli, crayon (>= 1.3.4), digest, evaluate, magrittr, methods,\npraise, R6 (>= 2.2.0), rlang (>= 0.3.0), withr (>= 2.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## tibble               "cli, crayon (>= 1.3.4), fansi (>= 0.4.0), methods, pillar (>=\n1.3.1), pkgconfig, rlang (>= 0.3.0), utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## tidyr                "dplyr (>= 0.8.2), ellipsis (>= 0.1.0), glue, magrittr, purrr,\nRcpp, rlang, stringi, tibble (>= 2.1.1), tidyselect (>= 0.2.5),\nutils, vctrs (>= 0.2.0), lifecycle"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## tidyselect           "glue (>= 1.3.0), purrr, rlang (>= 0.2.2), Rcpp (>= 0.12.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## tidyverse            "broom (>= 0.4.2), cli (>= 1.0.0), crayon (>= 1.3.4), dplyr (>=\n0.7.4), dbplyr (>= 1.1.0), forcats (>= 0.2.0), ggplot2 (>=\n2.2.1), haven (>= 1.1.0), hms (>= 0.3), httr (>= 1.3.1),\njsonlite (>= 1.5), lubridate (>= 1.7.1), magrittr (>= 1.5),\nmodelr (>= 0.1.1), purrr (>= 0.2.4), readr (>= 1.1.1), readxl\n(>= 1.0.0), reprex (>= 0.1.1), rlang (>= 0.1.4), rstudioapi (>=\n0.7), rvest (>= 0.3.2), stringr (>= 1.2.0), tibble (>= 1.3.4),\ntidyr (>= 0.7.2), xml2 (>= 1.1.1)"                                                                                                                                                                      
## timeDate             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## tinytex              "xfun (>= 0.5)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## tools                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## UpSetR               "ggplot2, gridExtra, plyr, utils, stats, methods, grDevices,\nscales"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## usethis              "clipr (>= 0.3.0), clisymbols, crayon, curl (>= 2.7), desc, fs\n(>= 1.3.0), gh, git2r (>= 0.23), glue (>= 1.3.0), purrr, rlang,\nrprojroot (>= 1.2), rstudioapi, stats, utils, whisker, withr,\nyaml"                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## utf8                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## utils                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## uuid                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## vctrs                "backports, ellipsis (>= 0.2.0), digest, glue, rlang (>=\n0.4.0), zeallot"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## vegan                "MASS, cluster, mgcv"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## vipor                "stats, graphics"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## viridisLite          NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## wbr                  "RcppParallel, Rcpp, RColorBrewer, Biostrings, IRanges,\nRsamtools, GenomicAlignments, GenomeInfoDbData, jsonlite, httr,\ndigest"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## wbrlims              "digest (>= 0.6.11),\nhttr (>= 1.2),\njsonlite (>= 1.5),\nlubridate (>= 1.7.3),\nmethods (>= 3.3),\nmime (>= 0.5),"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## webshot              "magrittr, jsonlite, callr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## whisker              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## withr                "stats, graphics, grDevices"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## xfun                 "stats, tools"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## XML                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## xml2                 "Rcpp, methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## xmlparsedata         NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## xopen                "processx"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## xtable               "stats, utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## XVector              "methods, utils, zlibbioc, BiocGenerics, S4Vectors, IRanges"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## yaml                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## zeallot              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## zip                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## zlibbioc             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## zoo                  "utils, graphics, grDevices, lattice (>= 0.20-27)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
##                      LinkingTo                                
## abind                NA                                       
## ade4                 NA                                       
## ape                  "Rcpp"                                   
## askpass              NA                                       
## assertthat           NA                                       
## backports            NA                                       
## base                 NA                                       
## base64enc            NA                                       
## beeswarm             NA                                       
## BH                   NA                                       
## bindr                NA                                       
## bindrcpp             "plogr, Rcpp"                            
## Biobase              NA                                       
## BiocGenerics         NA                                       
## BiocManager          NA                                       
## BiocParallel         "BH"                                     
## BiocVersion          NA                                       
## biomformat           NA                                       
## Biostrings           "S4Vectors, IRanges, XVector (>= 0.21.4)"
## bit                  NA                                       
## bit64                NA                                       
## bitops               NA                                       
## bizarro              NA                                       
## boot                 NA                                       
## brew                 NA                                       
## broom                NA                                       
## callr                NA                                       
## car                  NA                                       
## carData              NA                                       
## caret                NA                                       
## caTools              NA                                       
## cellranger           NA                                       
## class                NA                                       
## cli                  NA                                       
## cliapp               NA                                       
## clipr                NA                                       
## clisymbols           NA                                       
## cluster              NA                                       
## codetools            NA                                       
## colorspace           NA                                       
## commonmark           NA                                       
## compiler             NA                                       
## conflicted           NA                                       
## corpcor              NA                                       
## covr                 NA                                       
## cowplot              NA                                       
## cranlogs             NA                                       
## crayon               NA                                       
## crosstalk            NA                                       
## curl                 NA                                       
## cyclocomp            NA                                       
## cyl                  NA                                       
## dada2                "Rcpp, RcppParallel"                     
## data.table           NA                                       
## datasets             NA                                       
## DBI                  NA                                       
## dbplyr               NA                                       
## decontam             NA                                       
## DelayedArray         "S4Vectors"                              
## DEoptimR             NA                                       
## desc                 NA                                       
## devtools             NA                                       
## digest               NA                                       
## docopt               NA                                       
## doParallel           NA                                       
## dotCall64            NA                                       
## dplyr                "BH, plogr (>= 0.2.0), Rcpp (>= 1.0.1)"  
## DT                   NA                                       
## e1071                NA                                       
## ellipsis             NA                                       
## EMD                  NA                                       
## enc                  NA                                       
## evaluate             NA                                       
## fansi                NA                                       
## fastmap              NA                                       
## fastmatch            NA                                       
## fields               NA                                       
## filelock             NA                                       
## flexdashboard        NA                                       
## flowCore             "Rcpp, BH(>= 1.65.0.1)"                  
## flowPeaks            NA                                       
## foofactor            NA                                       
## forcats              NA                                       
## foreach              NA                                       
## foreign              NA                                       
## formatR              NA                                       
## fs                   "Rcpp"                                   
## futile.logger        NA                                       
## futile.options       NA                                       
## generics             NA                                       
## GenomeInfoDb         NA                                       
## GenomeInfoDbData     NA                                       
## GenomicAlignments    "S4Vectors, IRanges"                     
## GenomicRanges        "S4Vectors, IRanges"                     
## geometry             "Rcpp, RcppProgress"                     
## GGally               NA                                       
## ggbeeswarm           NA                                       
## ggplot2              NA                                       
## ggridges             NA                                       
## gh                   NA                                       
## git2r                NA                                       
## glue                 NA                                       
## googlesheets         NA                                       
## gower                NA                                       
## graph                NA                                       
## graphics             NA                                       
## grDevices            NA                                       
## grid                 NA                                       
## gridExtra            NA                                       
## gtable               NA                                       
## haven                "Rcpp"                                   
## here                 NA                                       
## hexbin               NA                                       
## highr                NA                                       
## hms                  NA                                       
## htmltools            "Rcpp"                                   
## htmlwidgets          NA                                       
## httpuv               "Rcpp, BH, later"                        
## httr                 NA                                       
## hwriter              NA                                       
## igraph               NA                                       
## ini                  NA                                       
## ipred                NA                                       
## ips                  NA                                       
## IRanges              "S4Vectors"                              
## itdepends            NA                                       
## iterators            NA                                       
## jsonlite             NA                                       
## kernlab              NA                                       
## KernSmooth           NA                                       
## kmer                 "Rcpp"                                   
## knitr                NA                                       
## labeling             NA                                       
## labrador             NA                                       
## labradorbase         NA                                       
## lambda.r             NA                                       
## later                "Rcpp, BH"                               
## lattice              NA                                       
## latticeExtra         NA                                       
## lava                 NA                                       
## lazyeval             NA                                       
## lifecycle            NA                                       
## linprog              NA                                       
## lintr                NA                                       
## lme4                 "Rcpp (>= 0.10.5), RcppEigen"            
## lobstr               "Rcpp"                                   
## locfit               NA                                       
## lpSolve              NA                                       
## lubridate            "Rcpp,"                                  
## magic                NA                                       
## magrittr             NA                                       
## manipulateWidget     NA                                       
## maps                 NA                                       
## maptools             NA                                       
## markdown             NA                                       
## MASS                 NA                                       
## Matrix               NA                                       
## MatrixModels         NA                                       
## matrixStats          NA                                       
## mean2                NA                                       
## memoise              NA                                       
## methods              NA                                       
## mgcv                 NA                                       
## mime                 NA                                       
## miniUI               NA                                       
## minpack.lm           NA                                       
## minqa                "Rcpp"                                   
## ModelMetrics         "Rcpp"                                   
## modelr               NA                                       
## MPN                  NA                                       
## multtest             NA                                       
## munsell              NA                                       
## mvtnorm              NA                                       
## new                  NA                                       
## nlme                 NA                                       
## nloptr               NA                                       
## nnet                 NA                                       
## numDeriv             NA                                       
## openssl              NA                                       
## openxlsx             "Rcpp"                                   
## parallel             NA                                       
## pbkrtest             NA                                       
## pcaPP                NA                                       
## permute              NA                                       
## phangorn             "Rcpp"                                   
## phylogram            NA                                       
## phyloseq             NA                                       
## pillar               NA                                       
## pkgbuild             NA                                       
## pkgcache             NA                                       
## pkgconfig            NA                                       
## pkgload              NA                                       
## plogr                NA                                       
## plotly               NA                                       
## plyr                 "Rcpp"                                   
## praise               NA                                       
## prettycode           NA                                       
## prettyunits          NA                                       
## processx             NA                                       
## prodlim              "Rcpp"                                   
## progress             NA                                       
## promises             "later, Rcpp"                            
## pryr                 "Rcpp"                                   
## ps                   NA                                       
## pspline              NA                                       
## purrr                NA                                       
## qpcR                 NA                                       
## quadprog             NA                                       
## quantreg             NA                                       
## R6                   NA                                       
## rappdirs             NA                                       
## rcmdcheck            NA                                       
## RColorBrewer         NA                                       
## Rcpp                 NA                                       
## RcppEigen            "Rcpp"                                   
## RcppParallel         NA                                       
## RcppProgress         NA                                       
## RcppRoll             "Rcpp"                                   
## RCurl                NA                                       
## readr                "Rcpp, BH"                               
## readxl               "progress, Rcpp"                         
## recipes              NA                                       
## rematch              NA                                       
## rematch2             NA                                       
## remotes              NA                                       
## reprex               NA                                       
## requirements         NA                                       
## reshape              NA                                       
## reshape2             "Rcpp"                                   
## rex                  NA                                       
## rgl                  NA                                       
## rhdf5                "Rhdf5lib"                               
## Rhdf5lib             NA                                       
## rio                  NA                                       
## rlang                NA                                       
## rmarkdown            NA                                       
## robustbase           NA                                       
## roxygen2             "Rcpp"                                   
## roxygen2md           NA                                       
## rpart                NA                                       
## rpivotTable          NA                                       
## rprojroot            NA                                       
## rrcov                NA                                       
## Rsamtools            "S4Vectors, IRanges, XVector, Biostrings"
## rstudioapi           NA                                       
## rversions            NA                                       
## rvest                NA                                       
## S4Vectors            NA                                       
## scales               "Rcpp"                                   
## segmented            NA                                       
## selectr              NA                                       
## seqinr               NA                                       
## sessioninfo          NA                                       
## sfsmisc              NA                                       
## shiny                NA                                       
## ShortRead            "S4Vectors, IRanges, XVector, Biostrings"
## sloop                NA                                       
## snow                 NA                                       
## sourcetools          NA                                       
## sp                   NA                                       
## spam                 NA                                       
## SparseM              NA                                       
## spatial              NA                                       
## splines              NA                                       
## SQUAREM              NA                                       
## stats                NA                                       
## stats4               NA                                       
## stringdist           NA                                       
## stringi              NA                                       
## stringr              NA                                       
## SummarizedExperiment NA                                       
## survival             NA                                       
## sys                  NA                                       
## tcltk                NA                                       
## testns               NA                                       
## testthat             NA                                       
## tibble               NA                                       
## tidyr                "Rcpp"                                   
## tidyselect           "Rcpp (>= 0.12.0),"                      
## tidyverse            NA                                       
## timeDate             NA                                       
## tinytex              NA                                       
## tools                NA                                       
## UpSetR               NA                                       
## usethis              NA                                       
## utf8                 NA                                       
## utils                NA                                       
## uuid                 NA                                       
## vctrs                NA                                       
## vegan                NA                                       
## vipor                NA                                       
## viridisLite          NA                                       
## wbr                  "Rcpp, RcppParallel"                     
## wbrlims              NA                                       
## webshot              NA                                       
## whisker              NA                                       
## withr                NA                                       
## xfun                 NA                                       
## XML                  NA                                       
## xml2                 "Rcpp (>= 0.12.12)"                      
## xmlparsedata         NA                                       
## xopen                NA                                       
## xtable               NA                                       
## XVector              "S4Vectors, IRanges"                     
## yaml                 NA                                       
## zeallot              NA                                       
## zip                  NA                                       
## zlibbioc             NA                                       
## zoo                  NA                                       
##                      Suggests                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## abind                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## ade4                 "ade4TkGUI, adegraphics, adephylo, ape, CircStats, deldir,\nlattice, pixmap, sp, spdep, splancs, waveslim"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## ape                  "gee, expm, igraph"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## askpass              "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## assertthat           "testthat, covr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## backports            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## base                 "methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## base64enc            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## beeswarm             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## BH                   NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## bindr                "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## bindrcpp             "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## Biobase              "tools, tkWidgets, ALL, RUnit, golubEsets"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## BiocGenerics         "Biobase, S4Vectors, IRanges, GenomicRanges, Rsamtools,\nAnnotationDbi, oligoClasses, oligo, affyPLM, flowClust, affy,\nDESeq2, MSnbase, annotate, RUnit"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## BiocManager          "BiocStyle, BiocVersion, remotes, testthat, withr, curl, knitr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## BiocParallel         "BiocGenerics, tools, foreach, BatchJobs, BBmisc, doParallel,\nRmpi, GenomicRanges, RNAseqData.HNRNPC.bam.chr14,\nTxDb.Hsapiens.UCSC.hg19.knownGene, VariantAnnotation,\nRsamtools, GenomicAlignments, ShortRead, codetools, RUnit,\nBiocStyle, knitr, batchtools, data.table"                                                                                                                                                                                                                                                                                                                                                                  
## BiocVersion          NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## biomformat           "testthat (>= 0.10), knitr (>= 1.10), BiocStyle (>= 1.6),\nrmarkdown (>= 0.7)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## Biostrings           "BSgenome (>= 1.13.14), BSgenome.Celegans.UCSC.ce2 (>=\n1.3.11), BSgenome.Dmelanogaster.UCSC.dm3 (>= 1.3.11),\nBSgenome.Hsapiens.UCSC.hg18, drosophila2probe, hgu95av2probe,\nhgu133aprobe, GenomicFeatures (>= 1.3.14), hgu95av2cdf, affy\n(>= 1.41.3), affydata (>= 1.11.5), RUnit"                                                                                                                                                                                                                                                                                                                                                           
## bit                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## bit64                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## bitops               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## bizarro              "testthat (>= 2.1.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## boot                 "MASS, survival"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## brew                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## broom                "AER, akima, AUC, bbmle, betareg, biglm, binGroup, boot, brms,\nbtergm, car, caret, coda, covr, e1071, emmeans, ergm, gam (>=\n1.15), gamlss, gamlss.data, gamlss.dist, geepack, ggplot2,\nglmnet, gmm, Hmisc, irlba, joineRML, Kendall, knitr, ks,\nLahman, lavaan, lfe, lme4, lmodel2, lmtest, lsmeans, maps,\nmaptools, MASS, Matrix, mclust, mgcv, muhaz, multcomp, network,\nnnet, orcutt (>= 2.2), ordinal, plm, plyr, poLCA, psych,\nquantreg, rgeos, rmarkdown, robust, rsample, rstan, rstanarm,\nsp, speedglm, statnet.common, survey, survival, testthat,\ntseries, xergm, zoo"                                                      
## callr                "cliapp, covr, crayon, fansi, knitr, pingr, ps, rmarkdown,\nrprojroot, spelling, testthat, tibble, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## car                  "alr4, boot, coxme, leaps, lmtest, Matrix, MatrixModels, rgl\n(>= 0.93.960), sandwich, SparseM, survival, survey"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## carData              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## caret                "BradleyTerry2, e1071, earth (>= 2.2-3), fastICA, gam (>=\n1.15), ipred, kernlab, knitr, klaR, MASS, ellipse, mda, mgcv,\nmlbench, MLmetrics, nnet, party (>= 0.9-99992), pls, pROC,\nproxy, randomForest, RANN, spls, subselect, pamr, superpc,\nCubist, testthat (>= 0.9.1), rpart, dplyr"                                                                                                                                                                                                                                                                                                                                                    
## caTools              "MASS, rpart"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## cellranger           "covr, testthat (>= 1.0.0), knitr, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## class                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## cli                  "covr, fansi, mockery, testthat, webshot, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## cliapp               "callr, covr, rstudioapi, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## clipr                "covr, knitr, rmarkdown, rstudioapi (>= 0.5), testthat (>=\n2.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## clisymbols           "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## cluster              "MASS, Matrix"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## codetools            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## colorspace           "datasets, utils, KernSmooth, MASS, kernlab, mvtnorm, vcd,\ntcltk, shiny, shinyjs, ggplot2, dplyr, scales, grid, png, jpeg,\nknitr, rmarkdown, RColorBrewer, rcartocolor, scico, viridis,\nwesanderson"                                                                                                                                                                                                                                                                                                                                                                                                                                         
## commonmark           "curl, testthat, xml2"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## compiler             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## conflicted           "covr, crayon, dplyr, pkgdown, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## corpcor              ""                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## covr                 "R6, knitr, rmarkdown, htmltools, DT (>= 0.2), testthat,\nrlang, rstudioapi (>= 0.2), xml2 (>= 1.0.0), parallel, memoise,\nmockery"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## cowplot              "Cairo, covr, dplyr, forcats, gridGraphics (>= 0.4-0), knitr,\nlattice, magick, maps, PASWR, rmarkdown, testthat (>= 1.0.0),\ntidyr, vdiffr (>= 0.3.0), VennDiagram"                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## cranlogs             "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## crayon               "mockery, rstudioapi, testthat, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## crosstalk            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## curl                 "spelling, testthat (>= 1.0.0), knitr, jsonlite, rmarkdown,\nmagrittr, httpuv (>= 1.4.4), webutils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## cyclocomp            "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## cyl                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## dada2                "BiocStyle, knitr, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## data.table           "bit64, curl, R.utils, knitr, xts, nanotime, zoo, yaml"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## datasets             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## DBI                  "blob, covr, hms, knitr, magrittr, rprojroot, rmarkdown,\nRSQLite (>= 1.1-2), testthat, xml2"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## dbplyr               "bit64, covr, knitr, Lahman, nycflights13, RMariaDB (>=\n1.0.2), rmarkdown, RMySQL (>= 0.10.11), RPostgreSQL (>= 0.4.1),\nRSQLite (>= 2.1.0), testthat (>= 2.0.0), withr (>= 2.1.2)"                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## decontam             "BiocStyle, knitr, rmarkdown, phyloseq"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## DelayedArray         "Matrix, HDF5Array, genefilter, SummarizedExperiment, airway,\npryr, DelayedMatrixStats, knitr, BiocStyle, RUnit"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## DEoptimR             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## desc                 "covr, testthat, whoami, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## devtools             "BiocManager, bitops, curl (>= 0.9), evaluate, foghorn (>=\n1.1.0), gmailr (> 0.7.0), knitr, lintr (>= 0.2.1), mockery,\npingr, MASS, pkgdown, Rcpp (>= 0.10.0), rhub (>= 1.0.2),\nrmarkdown, spelling (>= 1.1), whisker"                                                                                                                                                                                                                                                                                                                                                                                                                       
## digest               "tinytest, knitr, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## docopt               "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## doParallel           "caret, mlbench, rpart, RUnit"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## dotCall64            "microbenchmark, OpenMPController, RColorBrewer, roxygen2,\nspam, testthat,"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## dplyr                "bit64, callr, covr, crayon (>= 1.3.4), DBI, dbplyr, dtplyr,\nggplot2, hms, knitr, Lahman, lubridate, MASS, mgcv,\nmicrobenchmark, nycflights13, rmarkdown, RMySQL, RPostgreSQL,\nRSQLite, testthat, withr, broom, purrr, readr"                                                                                                                                                                                                                                                                                                                                                                                                                
## DT                   "knitr (>= 1.8), rmarkdown, shiny (>= 1.1.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## e1071                "cluster, mlbench, nnet, randomForest, rpart, SparseM, xtable,\nMatrix, MASS, slam"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## ellipsis             "covr, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## EMD                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## enc                  "digest, pillar, readr, rlang, testthat, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## evaluate             "testthat, lattice, ggplot2"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## fansi                "unitizer, knitr, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## fastmap              "testthat (>= 2.1.1)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## fastmatch            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## fields               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## filelock             "callr (>= 2.0.0), covr, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## flexdashboard        "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## flowCore             "Rgraphviz, flowViz, flowStats, testthat, flowWorkspace,\nflowWorkspaceData, openCyto, knitr, ggcyto, gridExtra"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## flowPeaks            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## foofactor            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## forcats              "covr, ggplot2, testthat, readr, knitr, rmarkdown, dplyr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## foreach              "randomForest"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## foreign              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## formatR              "codetools, shiny, testit, rmarkdown, knitr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## fs                   "testthat, covr, pillar (>= 1.0.0), crayon, rmarkdown, knitr,\nwithr, spelling"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## futile.logger        "testthat, jsonlite"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## futile.options       NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## generics             "covr, pkgload, testthat, tibble"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## GenomeInfoDb         "GenomicRanges, Rsamtools, GenomicAlignments, BSgenome,\nGenomicFeatures, BSgenome.Scerevisiae.UCSC.sacCer2,\nBSgenome.Celegans.UCSC.ce2, BSgenome.Hsapiens.NCBI.GRCh38,\nTxDb.Dmelanogaster.UCSC.dm3.ensGene, RUnit, BiocStyle, knitr"                                                                                                                                                                                                                                                                                                                                                                                                         
## GenomeInfoDbData     NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## GenomicAlignments    "ShortRead, rtracklayer, BSgenome, GenomicFeatures,\nRNAseqData.HNRNPC.bam.chr14, pasillaBamSubset,\nTxDb.Hsapiens.UCSC.hg19.knownGene,\nTxDb.Dmelanogaster.UCSC.dm3.ensGene,\nBSgenome.Dmelanogaster.UCSC.dm3, BSgenome.Hsapiens.UCSC.hg19,\nDESeq2, edgeR, RUnit, BiocStyle"                                                                                                                                                                                                                                                                                                                                                                  
## GenomicRanges        "Matrix, Biobase, AnnotationDbi, annotate, Biostrings (>=\n2.25.3), SummarizedExperiment (>= 0.1.5), Rsamtools (>=\n1.13.53), GenomicAlignments, rtracklayer, BSgenome,\nGenomicFeatures, Gviz, VariantAnnotation, AnnotationHub,\nDESeq2, DEXSeq, edgeR, KEGGgraph, RNAseqData.HNRNPC.bam.chr14,\npasillaBamSubset, KEGG.db, hgu95av2.db, hgu95av2probe,\nBSgenome.Scerevisiae.UCSC.sacCer2, BSgenome.Hsapiens.UCSC.hg19,\nBSgenome.Mmusculus.UCSC.mm10,\nTxDb.Athaliana.BioMart.plantsmart22,\nTxDb.Dmelanogaster.UCSC.dm3.ensGene,\nTxDb.Hsapiens.UCSC.hg19.knownGene,\nTxDb.Mmusculus.UCSC.mm10.knownGene, RUnit, digest, knitr,\nBiocStyle"
## geometry             "spelling, testthat, rgl, R.matlab, tripack"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## GGally               "broom (>= 0.4.0), chemometrics, geosphere (>= 1.5-1), igraph\n(>= 1.0.1), intergraph (>= 2.0-2), maps (>= 3.1.0), mapproj,\nnetwork (>= 1.12.0), scagnostics, scales (>= 0.4.0), sna (>=\n2.3-2), survival, packagedocs (>= 0.4.0), rmarkdown, roxygen2,\ntestthat, crosstalk"                                                                                                                                                                                                                                                                                                                                                                 
## ggbeeswarm           "gridExtra"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## ggplot2              "covr, dplyr, ggplot2movies, hexbin, Hmisc, knitr, lattice,\nmapproj, maps, maptools, multcomp, munsell, nlme, profvis,\nquantreg, rgeos, rmarkdown, rpart, sf (>= 0.7-3), svglite (>=\n1.2.0.9001), testthat (>= 0.11.0), vdiffr (>= 0.3.0)"                                                                                                                                                                                                                                                                                                                                                                                                   
## ggridges             "covr, dplyr, gridExtra, ggplot2movies, DAAG, forcats, knitr,\nrmarkdown, testthat, vdiffr, viridis"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## gh                   "covr, pingr, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## git2r                "getPass"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## glue                 "testthat, covr, magrittr, crayon, knitr, rmarkdown, DBI,\nRSQLite, R.utils, forcats, microbenchmark, rprintf, stringr,\nggplot2, dplyr, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## googlesheets         "covr, ggplot2, knitr, rmarkdown, rprojroot, testthat (>=\n1.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## gower                "tinytest (>= 0.9.3),"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## graph                "SparseM (>= 0.36), XML, RBGL, RUnit, cluster"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## graphics             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## grDevices            "KernSmooth"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## grid                 "lattice"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## gridExtra            "ggplot2, egg, lattice, knitr, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## gtable               "covr, testthat, knitr, rmarkdown, ggplot2, profvis"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## haven                "covr, fs, knitr, rmarkdown, testthat, pillar (>= 1.1.1), cli,\ncrayon"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## here                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## hexbin               "marray, affy, Biobase, limma"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## highr                "knitr, testit"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## hms                  "crayon, lubridate, pillar (>= 1.1.0), testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## htmltools            "markdown, testthat, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## htmlwidgets          "knitr (>= 1.8)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## httpuv               "testthat, callr, curl, websocket"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## httr                 "covr, httpuv, jpeg, knitr, png, readr, rmarkdown, testthat\n(>= 0.8.0), xml2"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## hwriter              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## igraph               "ape, digest, graph, igraphdata, rgl, scales, stats4, tcltk,\ntestthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## ini                  "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## ipred                "mvtnorm, mlbench, TH.data"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## ips                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## IRanges              "XVector, GenomicRanges, Rsamtools, GenomicAlignments,\nGenomicFeatures, BSgenome.Celegans.UCSC.ce2, pasillaBamSubset,\nRUnit, BiocStyle"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## itdepends            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## iterators            "RUnit, foreach"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## jsonlite             "httr, curl, plyr, testthat, knitr, rmarkdown, R.rsp, sp"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## kernlab              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## KernSmooth           "MASS"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## kmer                 "ape (>= 4.0), dendextend, knitr, rmarkdown, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## knitr                "formatR, testit, digest, rgl (>= 0.95.1201), codetools,\nrmarkdown, htmlwidgets (>= 0.7), webshot, tikzDevice (>= 0.10),\ntinytex, reticulate (>= 1.4), JuliaCall (>= 0.11.1), magick,\npng, jpeg, gifski, xml2 (>= 1.2.0), httr, DBI (>= 0.4-1),\nshowtext, tibble, sass, styler"                                                                                                                                                                                                                                                                                                                                                             
## labeling             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## labrador             "bit64 (>= 0.9.7),\ndocopt (>= 0.4.5),\nflexdashboard (>= 0.5.1),\nknitr (>= 1.17),\nplotly (>= 4.7.1),\nroxygen2 (>= 6.0.1),\nrpivotTable (>= 0.3.0),\nstringr (>= 1.4.0),\ntestthat (>= 2.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                               
## labradorbase         NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## lambda.r             "testit"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## later                "knitr, rmarkdown, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## lattice              "KernSmooth, MASS, latticeExtra"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## latticeExtra         "maps, mapproj, deldir, tripack, zoo, MASS, quantreg, mgcv"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## lava                 "KernSmooth, Matrix, Rgraphviz, data.table, ellipse, fields,\nforeach, geepack, gof (>= 0.9), graph, igraph (>= 0.6),\nlava.tobit (>= 0.4.7), lme4, mets (>= 1.1), nlme, optimx,\npolycor, quantreg, rgl, testthat (>= 0.11), visNetwork, zoo"                                                                                                                                                                                                                                                                                                                                                                                                  
## lazyeval             "knitr, rmarkdown (>= 0.2.65), testthat, covr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## lifecycle            "covr, crayon, knitr, rmarkdown, testthat (>= 2.1.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## linprog              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## lintr                "rmarkdown, mockery"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## lme4                 "knitr, rmarkdown, PKPDmodels, MEMSS, testthat (>= 0.8.1),\nggplot2, mlmRev, optimx (>= 2013.8.6), gamm4, pbkrtest, HSAUR2,\nnumDeriv, car, dfoptim"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## lobstr               "covr, pillar, pkgdown, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## locfit               "akima, gam"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## lpSolve              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## lubridate            "testthat, knitr, covr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## magic                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## magrittr             "testthat, knitr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## manipulateWidget     "dygraphs, leaflet, plotly, xts, rmarkdown, testthat, covr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## maps                 "mapproj (>= 1.2-0), mapdata (>= 2.3.0), sp, maptools,\nrnaturalearth"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## maptools             "rgeos (>= 0.1-8), spatstat (>= 1.60), PBSmapping, maps,\nRColorBrewer, raster, polyclip, spatstat.utils"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## markdown             "knitr, RCurl"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## MASS                 "lattice, nlme, nnet, survival"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## Matrix               "expm, MASS"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## MatrixModels         NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## matrixStats          "base64enc, ggplot2, knitr, microbenchmark, R.devices, R.rsp"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## mean2                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## memoise              "testthat, aws.s3, httr, covr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## methods              "codetools"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## mgcv                 "parallel, survival, MASS"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## mime                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## miniUI               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## minpack.lm           "MASS"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## minqa                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## ModelMetrics         "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## modelr               "compiler, covr, ggplot2, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## MPN                  "knitr (>= 1.20), rmarkdown (>= 1.10), testthat (>= 2.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## multtest             "snow"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## munsell              "ggplot2, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## mvtnorm              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## new                  NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## nlme                 "Hmisc, MASS"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## nloptr               "testthat (>= 0.8.1), knitr, rmarkdown, inline (>= 0.3.14)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## nnet                 "MASS"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## numDeriv             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## openssl              "testthat, digest, knitr, rmarkdown, jsonlite, jose, sodium"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## openxlsx             "knitr, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## parallel             "methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## pbkrtest             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## pcaPP                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## permute              "vegan (>= 2.0-0), testthat (>= 0.5), parallel"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## phangorn             "testthat, vdiffr, seqinr, xtable, rgl, knitr, rmarkdown,\nBiostrings"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## phylogram            "dendextend, knitr, rmarkdown, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## phyloseq             "BiocStyle (>= 2.4), DESeq2 (>= 1.16.1), genefilter (>= 1.58),\nknitr (>= 1.16), metagenomeSeq (>= 1.14), rmarkdown (>= 1.6),\ntestthat (>= 1.0.2)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## pillar               "knitr, lubridate, testthat, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## pkgbuild             "Rcpp, testthat, covr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## pkgcache             "callr, covr, debugme, desc, fs, jsonlite, mockery, pingr,\nrprojroot, testthat,"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## pkgconfig            "covr, testthat, disposables (>= 1.0.3)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## pkgload              "bitops, covr, Rcpp, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## plogr                "Rcpp"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## plotly               "MASS, maps, ggthemes, GGally, testthat, knitr, devtools,\nshiny (>= 1.1.0), shinytest (>= 1.3.0), curl, rmarkdown,\nvdiffr, Cairo, broom, webshot, listviewer, dendextend, sf,\nmaptools, rgeos, png, IRdisplay, processx, plotlyGeoAssets,\nforcats"                                                                                                                                                                                                                                                                                                                                                                                          
## plyr                 "abind, testthat, tcltk, foreach, doParallel, itertools,\niterators, covr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## praise               "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## prettycode           "covr, mockery, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## prettyunits          "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## processx             "callr (>= 3.2.0), codetools, covr, crayon, curl, debugme,\nparallel, testthat, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## prodlim              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## progress             "Rcpp, testthat, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## promises             "testthat, future, knitr, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## pryr                 "testthat (>= 0.8.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## ps                   "callr, covr, curl, pingr, processx (>= 3.1.0), R6, rlang,\ntestthat, tibble"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## pspline              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## purrr                "covr, crayon, dplyr (>= 0.7.8), knitr, rmarkdown, testthat,\ntibble, tidyselect"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## qpcR                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## quadprog             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## quantreg             "tripack, akima, MASS, survival, rgl, logspline, nor1mix,\nFormula, zoo, R.rsp"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## R6                   "knitr, microbenchmark, pryr, testthat, ggplot2, scales"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## rappdirs             "testthat, roxygen2"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## rcmdcheck            "covr, knitr, mockery, rmarkdown, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## RColorBrewer         NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## Rcpp                 "RUnit, inline, rbenchmark, knitr, rmarkdown, pinp, pkgKitten\n(>= 0.1.2)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## RcppEigen            "inline, RUnit, pkgKitten, microbenchmark"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## RcppParallel         "Rcpp, RUnit, knitr, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## RcppProgress         "RcppArmadillo, devtools, roxygen2, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## RcppRoll             "zoo, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## RCurl                "Rcompression, XML"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## readr                "curl, testthat, knitr, rmarkdown, stringi, covr, spelling"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## readxl               "covr, knitr, rmarkdown, rprojroot (>= 1.1), testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## recipes              "covr, ddalpha, dimRed (>= 0.2.2), fastICA, ggplot2, igraph,\nkernlab, knitr, pls, RANN, RcppRoll, rmarkdown, rpart, rsample,\nRSpectra, testthat (>= 2.1.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## rematch              "covr, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## rematch2             "covr, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## remotes              "brew, callr, codetools, curl, covr, git2r (>= 0.23.0), knitr,\nmockery, pkgbuild (>= 1.0.1), pingr, rmarkdown, rprojroot,\ntestthat, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## reprex               "covr, devtools, fortunes, knitr, miniUI, rprojroot,\nrstudioapi, shiny, styler (>= 1.0.2), testthat (>= 2.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## requirements         "testthat, covr, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## reshape              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## reshape2             "covr, lattice, testthat (>= 0.8.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## rex                  "testthat, knitr, rmarkdown, dplyr, ggplot2, Hmisc, stringr,\nrvest, roxygen2, covr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## rgl                  "MASS, rmarkdown, deldir, orientlib, lattice, misc3d,\nrstudioapi, magick, plotrix (>= 3.7-3), tripack, interp,\nalphashape3d"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## rhdf5                "bit64, BiocStyle, knitr, rmarkdown, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## Rhdf5lib             "BiocStyle, knitr, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## rio                  "datasets, bit64, testthat, knitr, magrittr, clipr, csvy,\nfeather, fst, hexView, jsonlite, readODS (>= 1.6.4), readr,\nrmatio, xml2 (>= 1.2.0), yaml"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## rlang                "covr, crayon, magrittr, methods, pillar, rmarkdown, testthat\n(>= 2.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## rmarkdown            "shiny (>= 0.11), tufte, testthat, digest, dygraphs, tibble,\nfs, pkgdown, callr (>= 2.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## robustbase           "grid, MASS, lattice, boot, cluster, Matrix, robust,\nfit.models, MPV, xtable, ggplot2, GGally, RColorBrewer,\nreshape2, sfsmisc, catdata, doParallel, foreach, skewt"                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## roxygen2             "covr, devtools, knitr, rmarkdown, testthat (>= 0.8.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## roxygen2md           "rstudioapi, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## rpart                "survival"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## rpivotTable          "testthat, htmltools, knitr, rmarkdown, devtools, dplyr,\ndata.table"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## rprojroot            "testthat, mockr, knitr, withr, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## rrcov                "grid, MASS, ellipse"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## Rsamtools            "GenomicAlignments, ShortRead (>= 1.19.10), GenomicFeatures,\nTxDb.Dmelanogaster.UCSC.dm3.ensGene, KEGG.db,\nTxDb.Hsapiens.UCSC.hg18.knownGene, RNAseqData.HNRNPC.bam.chr14,\nBSgenome.Hsapiens.UCSC.hg19, RUnit, BiocStyle"                                                                                                                                                                                                                                                                                                                                                                                                                    
## rstudioapi           "testthat, knitr, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## rversions            "mockery, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## rvest                "covr, knitr, png, rmarkdown, spelling, stringi (>= 0.3.1),\ntestthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## S4Vectors            "IRanges, GenomicRanges, SummarizedExperiment, Matrix,\nDelayedArray, ShortRead, graph, data.table, RUnit, BiocStyle"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## scales               "dichromat, bit64, covr, hms, testthat (>= 2.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## segmented            NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## selectr              "testthat, XML, xml2"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## seqinr               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## sessioninfo          "callr, covr, mockery, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## sfsmisc              "datasets, tcltk, cluster, lattice, MASS, Matrix, nlme, lokern"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## shiny                "datasets, Cairo (>= 1.5-5), testthat (>= 2.1.1), knitr (>=\n1.6), markdown, rmarkdown, ggplot2, reactlog (>= 1.0.0),\nmagrittr, yaml"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## ShortRead            "BiocStyle, RUnit, biomaRt, GenomicFeatures, yeastNagalakshmi"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## sloop                "covr, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## snow                 "Rmpi,rlecuyer,nws"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## sourcetools          "testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## sp                   "RColorBrewer, rgdal (>= 0.8-7), rgeos (>= 0.3-13), gstat,\nmaptools, deldir"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## spam                 "spam64, fields, SparseM, Matrix, testthat, R.rsp, truncdist,\nknitr, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## SparseM              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## spatial              "MASS"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## splines              "Matrix, methods"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## SQUAREM              "setRNG"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## stats                "MASS, Matrix, SuppDists, methods, stats4"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## stats4               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## stringdist           "tinytest"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## stringi              NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## stringr              "covr, htmltools, htmlwidgets, knitr, rmarkdown, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## SummarizedExperiment "annotate, AnnotationDbi, hgu95av2.db, GenomicFeatures,\nTxDb.Hsapiens.UCSC.hg19.knownGene, BiocStyle, knitr, rmarkdown,\ndigest, jsonlite, rhdf5, HDF5Array (>= 1.7.5), airway, RUnit,\ntestthat"                                                                                                                                                                                                                                                                                                                                                                                                                                              
## survival             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## sys                  "unix (>= 1.4), spelling, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## tcltk                NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## testns               NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## testthat             "covr, curl (>= 0.9.5), devtools, knitr, rmarkdown, usethis,\nvctrs (>= 0.1.0), xml2"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## tibble               "bench, covr, dplyr, htmltools, import, knitr, mockr,\nnycflights13, rmarkdown, testthat, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## tidyr                "covr, jsonlite, knitr, repurrrsive (>= 1.0.0), rmarkdown,\nreadr, testthat (>= 2.1.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## tidyselect           "covr, dplyr, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## tidyverse            "feather (>= 0.3.1), knitr (>= 1.17), rmarkdown (>= 1.7.4)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## timeDate             "date, RUnit"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## tinytex              "testit, rstudioapi"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## tools                "codetools, methods, xml2, curl, commonmark"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## UpSetR               "knitr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## usethis              "covr, knitr, magick, pkgdown (>= 1.1.0), rmarkdown, roxygen2,\nspelling (>= 1.2), styler (>= 1.0.2), testthat (>= 2.1.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## utf8                 "knitr, rmarkdown, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    
## utils                "methods, xml2, commonmark"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## uuid                 NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## vctrs                "bit64, covr, crayon, generics, knitr, pillar (>= 1.4.1),\npkgdown, rmarkdown, testthat, tibble"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## vegan                "parallel, tcltk, knitr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## vipor                "testthat, beeswarm, lattice, ggplot2, beanplot, vioplot,\nggbeeswarm,"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## viridisLite          "hexbin (>= 1.27.0), ggplot2 (>= 1.0.1), testthat, covr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
## wbr                  "knitr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## wbrlims              "docopt (>= 0.4.5),\nknitr (>= 1.17),\ntestthat (>= 2.0.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## webshot              "httpuv, knitr, rmarkdown, shiny"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
## whisker              "markdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## withr                "testthat, covr, lattice, DBI, RSQLite, methods, knitr,\nrmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
## xfun                 "testit, parallel, rstudioapi, tinytex, mime, markdown, knitr,\nhtmltools, base64enc, remotes, rmarkdown"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
## XML                  "bitops, RCurl"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
## xml2                 "covr, curl, httr, knitr, magrittr, mockery, rmarkdown,\ntestthat (>= 2.1.0)"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## xmlparsedata         "covr, testthat, xml2"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
## xopen                "ps, testthat"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
## xtable               "knitr, plm, zoo, survival"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
## XVector              "Biostrings, drosophila2probe, RUnit"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## yaml                 "RUnit"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
## zeallot              "testthat, knitr, rmarkdown, purrr, magrittr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
## zip                  "covr, processx, R6, testthat, withr"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           
## zlibbioc             NA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## zoo                  "coda, chron, DAAG, fts, ggplot2, mondate, scales,\nstrucchange, timeDate, timeSeries, tis, tseries, xts"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
##                      Enhances                                                  
## abind                NA                                                        
## ade4                 NA                                                        
## ape                  NA                                                        
## askpass              NA                                                        
## assertthat           NA                                                        
## backports            NA                                                        
## base                 NA                                                        
## base64enc            "png"                                                     
## beeswarm             NA                                                        
## BH                   NA                                                        
## bindr                NA                                                        
## bindrcpp             NA                                                        
## Biobase              NA                                                        
## BiocGenerics         NA                                                        
## BiocManager          NA                                                        
## BiocParallel         NA                                                        
## BiocVersion          NA                                                        
## biomformat           NA                                                        
## Biostrings           "Rmpi"                                                    
## bit                  NA                                                        
## bit64                NA                                                        
## bitops               NA                                                        
## bizarro              NA                                                        
## boot                 NA                                                        
## brew                 NA                                                        
## broom                NA                                                        
## callr                NA                                                        
## car                  NA                                                        
## carData              NA                                                        
## caret                NA                                                        
## caTools              NA                                                        
## cellranger           NA                                                        
## class                NA                                                        
## cli                  NA                                                        
## cliapp               NA                                                        
## clipr                NA                                                        
## clisymbols           NA                                                        
## cluster              NA                                                        
## codetools            NA                                                        
## colorspace           NA                                                        
## commonmark           NA                                                        
## compiler             NA                                                        
## conflicted           NA                                                        
## corpcor              NA                                                        
## covr                 NA                                                        
## cowplot              NA                                                        
## cranlogs             NA                                                        
## crayon               NA                                                        
## crosstalk            NA                                                        
## curl                 NA                                                        
## cyclocomp            NA                                                        
## cyl                  NA                                                        
## dada2                NA                                                        
## data.table           NA                                                        
## datasets             NA                                                        
## DBI                  NA                                                        
## dbplyr               NA                                                        
## decontam             NA                                                        
## DelayedArray         NA                                                        
## DEoptimR             "robustbase"                                              
## desc                 NA                                                        
## devtools             NA                                                        
## digest               NA                                                        
## docopt               NA                                                        
## doParallel           "compiler"                                                
## dotCall64            NA                                                        
## dplyr                NA                                                        
## DT                   NA                                                        
## e1071                NA                                                        
## ellipsis             NA                                                        
## EMD                  NA                                                        
## enc                  NA                                                        
## evaluate             NA                                                        
## fansi                NA                                                        
## fastmap              NA                                                        
## fastmatch            NA                                                        
## fields               NA                                                        
## filelock             NA                                                        
## flexdashboard        NA                                                        
## flowCore             NA                                                        
## flowPeaks            "flowCore"                                                
## foofactor            NA                                                        
## forcats              NA                                                        
## foreach              "compiler, doMC, RUnit, doParallel"                       
## foreign              NA                                                        
## formatR              NA                                                        
## fs                   NA                                                        
## futile.logger        NA                                                        
## futile.options       NA                                                        
## generics             NA                                                        
## GenomeInfoDb         NA                                                        
## GenomeInfoDbData     NA                                                        
## GenomicAlignments    NA                                                        
## GenomicRanges        NA                                                        
## geometry             NA                                                        
## GGally               NA                                                        
## ggbeeswarm           NA                                                        
## ggplot2              "sp"                                                      
## ggridges             NA                                                        
## gh                   NA                                                        
## git2r                NA                                                        
## glue                 NA                                                        
## googlesheets         NA                                                        
## gower                NA                                                        
## graph                "Rgraphviz"                                               
## graphics             NA                                                        
## grDevices            NA                                                        
## grid                 NA                                                        
## gridExtra            NA                                                        
## gtable               NA                                                        
## haven                NA                                                        
## here                 NA                                                        
## hexbin               NA                                                        
## highr                NA                                                        
## hms                  NA                                                        
## htmltools            "knitr"                                                   
## htmlwidgets          "shiny (>= 1.1)"                                          
## httpuv               NA                                                        
## httr                 NA                                                        
## hwriter              NA                                                        
## igraph               NA                                                        
## ini                  NA                                                        
## ipred                NA                                                        
## ips                  NA                                                        
## IRanges              NA                                                        
## itdepends            NA                                                        
## iterators            NA                                                        
## jsonlite             NA                                                        
## kernlab              NA                                                        
## KernSmooth           NA                                                        
## kmer                 NA                                                        
## knitr                NA                                                        
## labeling             NA                                                        
## labrador             NA                                                        
## labradorbase         NA                                                        
## lambda.r             NA                                                        
## later                NA                                                        
## lattice              "chron"                                                   
## latticeExtra         NA                                                        
## lava                 NA                                                        
## lazyeval             NA                                                        
## lifecycle            NA                                                        
## linprog              NA                                                        
## lintr                NA                                                        
## lme4                 NA                                                        
## lobstr               NA                                                        
## locfit               NA                                                        
## lpSolve              NA                                                        
## lubridate            "chron, fts, timeSeries, timeDate, tis, tseries, xts, zoo"
## magic                NA                                                        
## magrittr             NA                                                        
## manipulateWidget     NA                                                        
## maps                 NA                                                        
## maptools             "gpclib, RArcInfo"                                        
## markdown             NA                                                        
## MASS                 NA                                                        
## Matrix               "MatrixModels, graph, SparseM, sfsmisc"                   
## MatrixModels         NA                                                        
## matrixStats          NA                                                        
## mean2                NA                                                        
## memoise              NA                                                        
## methods              NA                                                        
## mgcv                 NA                                                        
## mime                 NA                                                        
## miniUI               NA                                                        
## minpack.lm           NA                                                        
## minqa                NA                                                        
## ModelMetrics         NA                                                        
## modelr               NA                                                        
## MPN                  NA                                                        
## multtest             NA                                                        
## munsell              NA                                                        
## mvtnorm              NA                                                        
## new                  NA                                                        
## nlme                 NA                                                        
## nloptr               NA                                                        
## nnet                 NA                                                        
## numDeriv             NA                                                        
## openssl              NA                                                        
## openxlsx             NA                                                        
## parallel             "snow, nws, Rmpi"                                         
## pbkrtest             NA                                                        
## pcaPP                NA                                                        
## permute              NA                                                        
## phangorn             NA                                                        
## phylogram            NA                                                        
## phyloseq             "doParallel (>= 1.0.10)"                                  
## pillar               NA                                                        
## pkgbuild             NA                                                        
## pkgcache             NA                                                        
## pkgconfig            NA                                                        
## pkgload              NA                                                        
## plogr                NA                                                        
## plotly               NA                                                        
## plyr                 NA                                                        
## praise               NA                                                        
## prettycode           NA                                                        
## prettyunits          NA                                                        
## processx             NA                                                        
## prodlim              NA                                                        
## progress             NA                                                        
## promises             NA                                                        
## pryr                 NA                                                        
## ps                   NA                                                        
## pspline              NA                                                        
## purrr                NA                                                        
## qpcR                 NA                                                        
## quadprog             NA                                                        
## quantreg             NA                                                        
## R6                   NA                                                        
## rappdirs             NA                                                        
## rcmdcheck            NA                                                        
## RColorBrewer         NA                                                        
## Rcpp                 NA                                                        
## RcppEigen            NA                                                        
## RcppParallel         NA                                                        
## RcppProgress         NA                                                        
## RcppRoll             NA                                                        
## RCurl                NA                                                        
## readr                NA                                                        
## readxl               NA                                                        
## recipes              NA                                                        
## rematch              NA                                                        
## rematch2             NA                                                        
## remotes              NA                                                        
## reprex               NA                                                        
## requirements         NA                                                        
## reshape              NA                                                        
## reshape2             NA                                                        
## rex                  NA                                                        
## rgl                  NA                                                        
## rhdf5                NA                                                        
## Rhdf5lib             NA                                                        
## rio                  NA                                                        
## rlang                NA                                                        
## rmarkdown            NA                                                        
## robustbase           NA                                                        
## roxygen2             NA                                                        
## roxygen2md           NA                                                        
## rpart                NA                                                        
## rpivotTable          "shiny (>= 0.12)"                                         
## rprojroot            NA                                                        
## rrcov                NA                                                        
## Rsamtools            NA                                                        
## rstudioapi           NA                                                        
## rversions            NA                                                        
## rvest                NA                                                        
## S4Vectors            NA                                                        
## scales               NA                                                        
## segmented            NA                                                        
## selectr              NA                                                        
## seqinr               NA                                                        
## sessioninfo          NA                                                        
## sfsmisc              "mgcv, rpart, nor1mix, polycor, sm, tikzDevice"           
## shiny                NA                                                        
## ShortRead            NA                                                        
## sloop                NA                                                        
## snow                 NA                                                        
## sourcetools          NA                                                        
## sp                   NA                                                        
## spam                 NA                                                        
## SparseM              NA                                                        
## spatial              NA                                                        
## splines              NA                                                        
## SQUAREM              NA                                                        
## stats                NA                                                        
## stats4               NA                                                        
## stringdist           NA                                                        
## stringi              NA                                                        
## stringr              NA                                                        
## SummarizedExperiment NA                                                        
## survival             NA                                                        
## sys                  NA                                                        
## tcltk                NA                                                        
## testns               NA                                                        
## testthat             NA                                                        
## tibble               NA                                                        
## tidyr                NA                                                        
## tidyselect           NA                                                        
## tidyverse            NA                                                        
## timeDate             NA                                                        
## tinytex              NA                                                        
## tools                NA                                                        
## UpSetR               NA                                                        
## usethis              NA                                                        
## utf8                 NA                                                        
## utils                NA                                                        
## uuid                 NA                                                        
## vctrs                NA                                                        
## vegan                NA                                                        
## vipor                NA                                                        
## viridisLite          NA                                                        
## wbr                  NA                                                        
## wbrlims              NA                                                        
## webshot              NA                                                        
## whisker              NA                                                        
## withr                NA                                                        
## xfun                 NA                                                        
## XML                  NA                                                        
## xml2                 NA                                                        
## xmlparsedata         NA                                                        
## xopen                NA                                                        
## xtable               NA                                                        
## XVector              NA                                                        
## yaml                 NA                                                        
## zeallot              NA                                                        
## zip                  NA                                                        
## zlibbioc             NA                                                        
## zoo                  NA                                                        
##                      License                                 
## abind                "LGPL (>= 2)"                           
## ade4                 "GPL (>= 2)"                            
## ape                  "GPL (>= 2)"                            
## askpass              "MIT + file LICENSE"                    
## assertthat           "GPL-3"                                 
## backports            "GPL-2 | GPL-3"                         
## base                 "Part of R 3.6.1"                       
## base64enc            "GPL-2 | GPL-3"                         
## beeswarm             "Artistic-2.0"                          
## BH                   "BSL-1.0"                               
## bindr                "MIT + file LICENSE"                    
## bindrcpp             "MIT + file LICENSE"                    
## Biobase              "Artistic-2.0"                          
## BiocGenerics         "Artistic-2.0"                          
## BiocManager          "Artistic-2.0"                          
## BiocParallel         "GPL-2 | GPL-3"                         
## BiocVersion          "Artistic-2.0"                          
## biomformat           "GPL-2"                                 
## Biostrings           "Artistic-2.0"                          
## bit                  "GPL-2"                                 
## bit64                "GPL-2"                                 
## bitops               "GPL (>= 2)"                            
## bizarro              "MIT + file LICENSE"                    
## boot                 "Unlimited"                             
## brew                 "GPL-2"                                 
## broom                "MIT + file LICENSE"                    
## callr                "MIT + file LICENSE"                    
## car                  "GPL (>= 2)"                            
## carData              "GPL (>= 2)"                            
## caret                "GPL (>= 2)"                            
## caTools              "GPL-3"                                 
## cellranger           "MIT + file LICENSE"                    
## class                "GPL-2 | GPL-3"                         
## cli                  "MIT + file LICENSE"                    
## cliapp               "MIT + file LICENSE"                    
## clipr                "GPL-3"                                 
## clisymbols           "MIT + file LICENSE"                    
## cluster              "GPL (>= 2)"                            
## codetools            "GPL"                                   
## colorspace           "BSD_3_clause + file LICENSE"           
## commonmark           "BSD_2_clause + file LICENSE"           
## compiler             "Part of R 3.6.1"                       
## conflicted           "GPL-3"                                 
## corpcor              "GPL (>= 3)"                            
## covr                 "GPL-3"                                 
## cowplot              "GPL-2"                                 
## cranlogs             "MIT + file LICENSE"                    
## crayon               "MIT + file LICENSE"                    
## crosstalk            "MIT + file LICENSE"                    
## curl                 "MIT + file LICENSE"                    
## cyclocomp            "MIT + file LICENSE"                    
## cyl                  "What license it uses"                  
## dada2                "LGPL-3"                                
## data.table           "MPL-2.0 | file LICENSE"                
## datasets             "Part of R 3.6.1"                       
## DBI                  "LGPL (>= 2)"                           
## dbplyr               "MIT + file LICENSE"                    
## decontam             "Artistic-2.0"                          
## DelayedArray         "Artistic-2.0"                          
## DEoptimR             "GPL (>= 2)"                            
## desc                 "MIT + file LICENSE"                    
## devtools             "GPL (>= 2)"                            
## digest               "GPL (>= 2)"                            
## docopt               "MIT + file LICENSE"                    
## doParallel           "GPL-2"                                 
## dotCall64            "GPL (>= 2)"                            
## dplyr                "MIT + file LICENSE"                    
## DT                   "GPL-3 | file LICENSE"                  
## e1071                "GPL-2 | GPL-3"                         
## ellipsis             "GPL-3"                                 
## EMD                  "GPL (>= 3)"                            
## enc                  "GPL-3"                                 
## evaluate             "MIT + file LICENSE"                    
## fansi                "GPL (>= 2)"                            
## fastmap              "MIT + file LICENSE"                    
## fastmatch            "GPL-2"                                 
## fields               "GPL (>= 2)"                            
## filelock             "MIT + file LICENSE"                    
## flexdashboard        "MIT + file LICENSE"                    
## flowCore             "Artistic-2.0"                          
## flowPeaks            "Artistic-1.0"                          
## foofactor            "MIT + file LICENSE"                    
## forcats              "GPL-3"                                 
## foreach              "Apache License (== 2.0)"               
## foreign              "GPL (>= 2)"                            
## formatR              "GPL"                                   
## fs                   "GPL-3"                                 
## futile.logger        "LGPL-3"                                
## futile.options       "LGPL-3"                                
## generics             "GPL-2"                                 
## GenomeInfoDb         "Artistic-2.0"                          
## GenomeInfoDbData     "Artistic-2.0"                          
## GenomicAlignments    "Artistic-2.0"                          
## GenomicRanges        "Artistic-2.0"                          
## geometry             "GPL (>= 3)"                            
## GGally               "GPL (>= 2.0)"                          
## ggbeeswarm           "GPL (>= 2)"                            
## ggplot2              "GPL-2 | file LICENSE"                  
## ggridges             "GPL-2 | file LICENSE"                  
## gh                   "MIT + file LICENSE"                    
## git2r                "GPL-2"                                 
## glue                 "MIT + file LICENSE"                    
## googlesheets         "MIT + file LICENSE"                    
## gower                "GPL-3"                                 
## graph                "Artistic-2.0"                          
## graphics             "Part of R 3.6.1"                       
## grDevices            "Part of R 3.6.1"                       
## grid                 "Part of R 3.6.1"                       
## gridExtra            "GPL (>= 2)"                            
## gtable               "GPL-2"                                 
## haven                "MIT + file LICENSE"                    
## here                 "GPL-3"                                 
## hexbin               "GPL-2"                                 
## highr                "GPL"                                   
## hms                  "GPL-3"                                 
## htmltools            "GPL (>= 2)"                            
## htmlwidgets          "MIT + file LICENSE"                    
## httpuv               "GPL (>= 2) | file LICENSE"             
## httr                 "MIT + file LICENSE"                    
## hwriter              "LGPL-2.1"                              
## igraph               "GPL (>= 2)"                            
## ini                  "GPL-3"                                 
## ipred                "GPL (>= 2)"                            
## ips                  "GPL-3"                                 
## IRanges              "Artistic-2.0"                          
## itdepends            "MIT + file LICENSE"                    
## iterators            "Apache License (== 2.0)"               
## jsonlite             "MIT + file LICENSE"                    
## kernlab              "GPL-2"                                 
## KernSmooth           "Unlimited"                             
## kmer                 "GPL-3"                                 
## knitr                "GPL"                                   
## labeling             "MIT + file LICENSE | Unlimited"        
## labrador             "Copyright, Whole Biome Inc."           
## labradorbase         "Copyright Pendulum Therapeutics"       
## lambda.r             "LGPL-3"                                
## later                "GPL (>= 2)"                            
## lattice              "GPL (>= 2)"                            
## latticeExtra         "GPL (>= 2)"                            
## lava                 "GPL-3"                                 
## lazyeval             "GPL-3"                                 
## lifecycle            "GPL-3"                                 
## linprog              "GPL (>= 2)"                            
## lintr                "MIT + file LICENSE"                    
## lme4                 "GPL (>= 2)"                            
## lobstr               "GPL-3"                                 
## locfit               "GPL (>= 2)"                            
## lpSolve              "LGPL-2"                                
## lubridate            "GPL (>= 2)"                            
## magic                "GPL-2"                                 
## magrittr             "MIT + file LICENSE"                    
## manipulateWidget     "GPL (>= 2) | file LICENSE"             
## maps                 "GPL-2"                                 
## maptools             "GPL (>= 2)"                            
## markdown             "GPL-2"                                 
## MASS                 "GPL-2 | GPL-3"                         
## Matrix               "GPL (>= 2) | file LICENCE"             
## MatrixModels         "GPL (>= 2)"                            
## matrixStats          "Artistic-2.0"                          
## mean2                "MIT + file LICENSE"                    
## memoise              "MIT + file LICENSE"                    
## methods              "Part of R 3.6.1"                       
## mgcv                 "GPL (>= 2)"                            
## mime                 "GPL"                                   
## miniUI               "GPL-3"                                 
## minpack.lm           "GPL-3"                                 
## minqa                "GPL-2"                                 
## ModelMetrics         "GPL (>= 2)"                            
## modelr               "GPL-3"                                 
## MPN                  "Unlimited"                             
## multtest             "LGPL"                                  
## munsell              "MIT + file LICENSE"                    
## mvtnorm              "GPL-2"                                 
## new                  "What license it uses"                  
## nlme                 "GPL (>= 2) | file LICENCE"             
## nloptr               "LGPL-3"                                
## nnet                 "GPL-2 | GPL-3"                         
## numDeriv             "GPL-2"                                 
## openssl              "MIT + file LICENSE"                    
## openxlsx             "MIT + file LICENSE"                    
## parallel             "Part of R 3.6.1"                       
## pbkrtest             "GPL (>= 2)"                            
## pcaPP                "GPL (>= 3)"                            
## permute              "GPL-2"                                 
## phangorn             "GPL (>= 2)"                            
## phylogram            "GPL-3"                                 
## phyloseq             "AGPL-3"                                
## pillar               "GPL-3"                                 
## pkgbuild             "GPL-3"                                 
## pkgcache             "MIT + file LICENSE"                    
## pkgconfig            "MIT + file LICENSE"                    
## pkgload              "GPL-3"                                 
## plogr                "MIT + file LICENSE"                    
## plotly               "MIT + file LICENSE"                    
## plyr                 "MIT + file LICENSE"                    
## praise               "MIT + file LICENSE"                    
## prettycode           "MIT + file LICENSE"                    
## prettyunits          "MIT + file LICENSE"                    
## processx             "MIT + file LICENSE"                    
## prodlim              "GPL (>= 2)"                            
## progress             "MIT + file LICENSE"                    
## promises             "MIT + file LICENSE"                    
## pryr                 "GPL-2"                                 
## ps                   "BSD_3_clause + file LICENSE"           
## pspline              "Unlimited"                             
## purrr                "GPL-3 | file LICENSE"                  
## qpcR                 "GPL (>= 2)"                            
## quadprog             "GPL (>= 2)"                            
## quantreg             "GPL (>= 2)"                            
## R6                   "MIT + file LICENSE"                    
## rappdirs             "MIT + file LICENSE"                    
## rcmdcheck            "MIT + file LICENSE"                    
## RColorBrewer         "Apache License 2.0"                    
## Rcpp                 "GPL (>= 2)"                            
## RcppEigen            "GPL (>= 2) | file LICENSE"             
## RcppParallel         "GPL-2"                                 
## RcppProgress         "GPL (>= 3)"                            
## RcppRoll             "GPL (>= 2)"                            
## RCurl                "BSD"                                   
## readr                "GPL (>= 2) | file LICENSE"             
## readxl               "GPL-3"                                 
## recipes              "GPL-2"                                 
## rematch              "MIT + file LICENSE"                    
## rematch2             "MIT + file LICENSE"                    
## remotes              "GPL (>= 2)"                            
## reprex               "MIT + file LICENSE"                    
## requirements         "GPL-3"                                 
## reshape              "MIT + file LICENSE"                    
## reshape2             "MIT + file LICENSE"                    
## rex                  "MIT + file LICENSE"                    
## rgl                  "GPL"                                   
## rhdf5                "Artistic-2.0"                          
## Rhdf5lib             "Artistic-2.0"                          
## rio                  "GPL-2"                                 
## rlang                "GPL-3"                                 
## rmarkdown            "GPL-3"                                 
## robustbase           "GPL (>= 2)"                            
## roxygen2             "GPL (>= 2)"                            
## roxygen2md           "GPL-3"                                 
## rpart                "GPL-2 | GPL-3"                         
## rpivotTable          "MIT + file LICENSE"                    
## rprojroot            "GPL-3"                                 
## rrcov                "GPL (>= 2)"                            
## Rsamtools            "Artistic-2.0 | file LICENSE"           
## rstudioapi           "MIT + file LICENSE"                    
## rversions            "MIT + file LICENSE"                    
## rvest                "GPL-3"                                 
## S4Vectors            "Artistic-2.0"                          
## scales               "MIT + file LICENSE"                    
## segmented            "GPL"                                   
## selectr              "BSD_3_clause + file LICENCE"           
## seqinr               "GPL (>= 2)"                            
## sessioninfo          "GPL-2"                                 
## sfsmisc              "GPL (>= 2)"                            
## shiny                "GPL-3 | file LICENSE"                  
## ShortRead            "Artistic-2.0"                          
## sloop                "GPL-3"                                 
## snow                 "GPL"                                   
## sourcetools          "MIT + file LICENSE"                    
## sp                   "GPL (>= 2)"                            
## spam                 "LGPL-2 | BSD_3_clause + file LICENSE"  
## SparseM              "GPL (>= 2)"                            
## spatial              "GPL-2 | GPL-3"                         
## splines              "Part of R 3.6.1"                       
## SQUAREM              "GPL (>= 2)"                            
## stats                "Part of R 3.6.1"                       
## stats4               "Part of R 3.6.1"                       
## stringdist           "GPL-3"                                 
## stringi              "file LICENSE"                          
## stringr              "GPL-2 | file LICENSE"                  
## SummarizedExperiment "Artistic-2.0"                          
## survival             "LGPL (>= 2)"                           
## sys                  "MIT + file LICENSE"                    
## tcltk                "Part of R 3.6.1"                       
## testns               "MIT + file LICENSE"                    
## testthat             "MIT + file LICENSE"                    
## tibble               "MIT + file LICENSE"                    
## tidyr                "MIT + file LICENSE"                    
## tidyselect           "GPL-3"                                 
## tidyverse            "GPL-3 | file LICENSE"                  
## timeDate             "GPL (>= 2)"                            
## tinytex              "MIT + file LICENSE"                    
## tools                "Part of R 3.6.1"                       
## UpSetR               "MIT + file LICENSE"                    
## usethis              "GPL-3"                                 
## utf8                 "Apache License (== 2.0) | file LICENSE"
## utils                "Part of R 3.6.1"                       
## uuid                 "MIT + file LICENSE"                    
## vctrs                "GPL-3"                                 
## vegan                "GPL-2"                                 
## vipor                "GPL (>= 2)"                            
## viridisLite          "MIT + file LICENSE"                    
## wbr                  "Artistic Liscence"                     
## wbrlims              "Artistic License"                      
## webshot              "GPL-2"                                 
## whisker              "GPL-3"                                 
## withr                "GPL (>= 2)"                            
## xfun                 "MIT + file LICENSE"                    
## XML                  "BSD_2_clause + file LICENSE"           
## xml2                 "GPL (>= 2)"                            
## xmlparsedata         "MIT + file LICENSE"                    
## xopen                "MIT + file LICENSE"                    
## xtable               "GPL (>= 2)"                            
## XVector              "Artistic-2.0"                          
## yaml                 "BSD_3_clause + file LICENSE"           
## zeallot              "MIT + file LICENSE"                    
## zip                  "CC0"                                   
## zlibbioc             "Artistic-2.0 + file LICENSE"           
## zoo                  "GPL-2 | GPL-3"                         
##                      License_is_FOSS License_restricts_use OS_type MD5sum
## abind                NA              NA                    NA      NA    
## ade4                 NA              NA                    NA      NA    
## ape                  NA              NA                    NA      NA    
## askpass              NA              NA                    NA      NA    
## assertthat           NA              NA                    NA      NA    
## backports            NA              NA                    NA      NA    
## base                 NA              NA                    NA      NA    
## base64enc            NA              NA                    NA      NA    
## beeswarm             NA              NA                    NA      NA    
## BH                   NA              NA                    NA      NA    
## bindr                NA              NA                    NA      NA    
## bindrcpp             NA              NA                    NA      NA    
## Biobase              NA              NA                    NA      NA    
## BiocGenerics         NA              NA                    NA      NA    
## BiocManager          NA              NA                    NA      NA    
## BiocParallel         NA              NA                    NA      NA    
## BiocVersion          NA              NA                    NA      NA    
## biomformat           NA              NA                    NA      NA    
## Biostrings           NA              NA                    NA      NA    
## bit                  NA              NA                    NA      NA    
## bit64                NA              NA                    NA      NA    
## bitops               NA              NA                    NA      NA    
## bizarro              NA              NA                    NA      NA    
## boot                 NA              NA                    NA      NA    
## brew                 NA              NA                    NA      NA    
## broom                NA              NA                    NA      NA    
## callr                NA              NA                    NA      NA    
## car                  NA              NA                    NA      NA    
## carData              NA              NA                    NA      NA    
## caret                NA              NA                    NA      NA    
## caTools              NA              NA                    NA      NA    
## cellranger           NA              NA                    NA      NA    
## class                NA              NA                    NA      NA    
## cli                  NA              NA                    NA      NA    
## cliapp               NA              NA                    NA      NA    
## clipr                NA              NA                    NA      NA    
## clisymbols           NA              NA                    NA      NA    
## cluster              NA              NA                    NA      NA    
## codetools            NA              NA                    NA      NA    
## colorspace           NA              NA                    NA      NA    
## commonmark           NA              NA                    NA      NA    
## compiler             NA              NA                    NA      NA    
## conflicted           NA              NA                    NA      NA    
## corpcor              NA              NA                    NA      NA    
## covr                 NA              NA                    NA      NA    
## cowplot              NA              NA                    NA      NA    
## cranlogs             NA              NA                    NA      NA    
## crayon               NA              NA                    NA      NA    
## crosstalk            NA              NA                    NA      NA    
## curl                 NA              NA                    NA      NA    
## cyclocomp            NA              NA                    NA      NA    
## cyl                  NA              NA                    NA      NA    
## dada2                NA              NA                    NA      NA    
## data.table           NA              NA                    NA      NA    
## datasets             NA              NA                    NA      NA    
## DBI                  NA              NA                    NA      NA    
## dbplyr               NA              NA                    NA      NA    
## decontam             NA              NA                    NA      NA    
## DelayedArray         NA              NA                    NA      NA    
## DEoptimR             NA              NA                    NA      NA    
## desc                 NA              NA                    NA      NA    
## devtools             NA              NA                    NA      NA    
## digest               NA              NA                    NA      NA    
## docopt               NA              NA                    NA      NA    
## doParallel           NA              NA                    NA      NA    
## dotCall64            NA              NA                    NA      NA    
## dplyr                NA              NA                    NA      NA    
## DT                   NA              NA                    NA      NA    
## e1071                NA              NA                    NA      NA    
## ellipsis             NA              NA                    NA      NA    
## EMD                  NA              NA                    NA      NA    
## enc                  NA              NA                    NA      NA    
## evaluate             NA              NA                    NA      NA    
## fansi                NA              NA                    NA      NA    
## fastmap              NA              NA                    NA      NA    
## fastmatch            NA              NA                    NA      NA    
## fields               NA              NA                    NA      NA    
## filelock             NA              NA                    NA      NA    
## flexdashboard        NA              NA                    NA      NA    
## flowCore             NA              NA                    NA      NA    
## flowPeaks            NA              NA                    NA      NA    
## foofactor            NA              NA                    NA      NA    
## forcats              NA              NA                    NA      NA    
## foreach              NA              NA                    NA      NA    
## foreign              NA              NA                    NA      NA    
## formatR              NA              NA                    NA      NA    
## fs                   NA              NA                    NA      NA    
## futile.logger        NA              NA                    NA      NA    
## futile.options       NA              NA                    NA      NA    
## generics             NA              NA                    NA      NA    
## GenomeInfoDb         NA              NA                    NA      NA    
## GenomeInfoDbData     NA              NA                    NA      NA    
## GenomicAlignments    NA              NA                    NA      NA    
## GenomicRanges        NA              NA                    NA      NA    
## geometry             NA              NA                    NA      NA    
## GGally               NA              NA                    NA      NA    
## ggbeeswarm           NA              NA                    NA      NA    
## ggplot2              NA              NA                    NA      NA    
## ggridges             NA              NA                    NA      NA    
## gh                   NA              NA                    NA      NA    
## git2r                NA              NA                    NA      NA    
## glue                 NA              NA                    NA      NA    
## googlesheets         NA              NA                    NA      NA    
## gower                NA              NA                    NA      NA    
## graph                NA              NA                    NA      NA    
## graphics             NA              NA                    NA      NA    
## grDevices            NA              NA                    NA      NA    
## grid                 NA              NA                    NA      NA    
## gridExtra            NA              NA                    NA      NA    
## gtable               NA              NA                    NA      NA    
## haven                NA              NA                    NA      NA    
## here                 NA              NA                    NA      NA    
## hexbin               NA              NA                    NA      NA    
## highr                NA              NA                    NA      NA    
## hms                  NA              NA                    NA      NA    
## htmltools            NA              NA                    NA      NA    
## htmlwidgets          NA              NA                    NA      NA    
## httpuv               NA              NA                    NA      NA    
## httr                 NA              NA                    NA      NA    
## hwriter              NA              NA                    NA      NA    
## igraph               NA              NA                    NA      NA    
## ini                  NA              NA                    NA      NA    
## ipred                NA              NA                    NA      NA    
## ips                  NA              NA                    NA      NA    
## IRanges              NA              NA                    NA      NA    
## itdepends            NA              NA                    NA      NA    
## iterators            NA              NA                    NA      NA    
## jsonlite             NA              NA                    NA      NA    
## kernlab              NA              NA                    NA      NA    
## KernSmooth           NA              NA                    NA      NA    
## kmer                 NA              NA                    NA      NA    
## knitr                NA              NA                    NA      NA    
## labeling             NA              NA                    NA      NA    
## labrador             NA              NA                    NA      NA    
## labradorbase         NA              NA                    NA      NA    
## lambda.r             NA              NA                    NA      NA    
## later                NA              NA                    NA      NA    
## lattice              NA              NA                    NA      NA    
## latticeExtra         NA              NA                    NA      NA    
## lava                 NA              NA                    NA      NA    
## lazyeval             NA              NA                    NA      NA    
## lifecycle            NA              NA                    NA      NA    
## linprog              NA              NA                    NA      NA    
## lintr                NA              NA                    NA      NA    
## lme4                 NA              NA                    NA      NA    
## lobstr               NA              NA                    NA      NA    
## locfit               NA              NA                    NA      NA    
## lpSolve              NA              NA                    NA      NA    
## lubridate            NA              NA                    NA      NA    
## magic                NA              NA                    NA      NA    
## magrittr             NA              NA                    NA      NA    
## manipulateWidget     NA              NA                    NA      NA    
## maps                 NA              NA                    NA      NA    
## maptools             NA              NA                    NA      NA    
## markdown             NA              NA                    NA      NA    
## MASS                 NA              NA                    NA      NA    
## Matrix               NA              NA                    NA      NA    
## MatrixModels         NA              NA                    NA      NA    
## matrixStats          NA              NA                    NA      NA    
## mean2                NA              NA                    NA      NA    
## memoise              NA              NA                    NA      NA    
## methods              NA              NA                    NA      NA    
## mgcv                 NA              NA                    NA      NA    
## mime                 NA              NA                    NA      NA    
## miniUI               NA              NA                    NA      NA    
## minpack.lm           NA              NA                    NA      NA    
## minqa                NA              NA                    NA      NA    
## ModelMetrics         NA              NA                    NA      NA    
## modelr               NA              NA                    NA      NA    
## MPN                  NA              NA                    NA      NA    
## multtest             NA              NA                    NA      NA    
## munsell              NA              NA                    NA      NA    
## mvtnorm              NA              NA                    NA      NA    
## new                  NA              NA                    NA      NA    
## nlme                 NA              NA                    NA      NA    
## nloptr               NA              NA                    NA      NA    
## nnet                 NA              NA                    NA      NA    
## numDeriv             NA              NA                    NA      NA    
## openssl              NA              NA                    NA      NA    
## openxlsx             NA              NA                    NA      NA    
## parallel             NA              NA                    NA      NA    
## pbkrtest             NA              NA                    NA      NA    
## pcaPP                NA              NA                    NA      NA    
## permute              NA              NA                    NA      NA    
## phangorn             NA              NA                    NA      NA    
## phylogram            NA              NA                    NA      NA    
## phyloseq             NA              NA                    NA      NA    
## pillar               NA              NA                    NA      NA    
## pkgbuild             NA              NA                    NA      NA    
## pkgcache             NA              NA                    NA      NA    
## pkgconfig            NA              NA                    NA      NA    
## pkgload              NA              NA                    NA      NA    
## plogr                NA              NA                    NA      NA    
## plotly               NA              NA                    NA      NA    
## plyr                 NA              NA                    NA      NA    
## praise               NA              NA                    NA      NA    
## prettycode           NA              NA                    NA      NA    
## prettyunits          NA              NA                    NA      NA    
## processx             NA              NA                    NA      NA    
## prodlim              NA              NA                    NA      NA    
## progress             NA              NA                    NA      NA    
## promises             NA              NA                    NA      NA    
## pryr                 NA              NA                    NA      NA    
## ps                   NA              NA                    NA      NA    
## pspline              NA              NA                    NA      NA    
## purrr                NA              NA                    NA      NA    
## qpcR                 NA              NA                    NA      NA    
## quadprog             NA              NA                    NA      NA    
## quantreg             NA              NA                    NA      NA    
## R6                   NA              NA                    NA      NA    
## rappdirs             NA              NA                    NA      NA    
## rcmdcheck            NA              NA                    NA      NA    
## RColorBrewer         NA              NA                    NA      NA    
## Rcpp                 NA              NA                    NA      NA    
## RcppEigen            NA              NA                    NA      NA    
## RcppParallel         NA              NA                    NA      NA    
## RcppProgress         NA              NA                    NA      NA    
## RcppRoll             NA              NA                    NA      NA    
## RCurl                NA              NA                    NA      NA    
## readr                NA              NA                    NA      NA    
## readxl               NA              NA                    NA      NA    
## recipes              NA              NA                    NA      NA    
## rematch              NA              NA                    NA      NA    
## rematch2             NA              NA                    NA      NA    
## remotes              NA              NA                    NA      NA    
## reprex               NA              NA                    NA      NA    
## requirements         NA              NA                    NA      NA    
## reshape              NA              NA                    NA      NA    
## reshape2             NA              NA                    NA      NA    
## rex                  NA              NA                    NA      NA    
## rgl                  NA              NA                    NA      NA    
## rhdf5                NA              NA                    NA      NA    
## Rhdf5lib             NA              NA                    NA      NA    
## rio                  NA              NA                    NA      NA    
## rlang                NA              NA                    NA      NA    
## rmarkdown            NA              NA                    NA      NA    
## robustbase           NA              NA                    NA      NA    
## roxygen2             NA              NA                    NA      NA    
## roxygen2md           NA              NA                    NA      NA    
## rpart                NA              NA                    NA      NA    
## rpivotTable          NA              NA                    NA      NA    
## rprojroot            NA              NA                    NA      NA    
## rrcov                NA              NA                    NA      NA    
## Rsamtools            NA              NA                    NA      NA    
## rstudioapi           NA              NA                    NA      NA    
## rversions            NA              NA                    NA      NA    
## rvest                NA              NA                    NA      NA    
## S4Vectors            NA              NA                    NA      NA    
## scales               NA              NA                    NA      NA    
## segmented            NA              NA                    NA      NA    
## selectr              NA              NA                    NA      NA    
## seqinr               NA              NA                    NA      NA    
## sessioninfo          NA              NA                    NA      NA    
## sfsmisc              NA              NA                    NA      NA    
## shiny                NA              NA                    NA      NA    
## ShortRead            NA              NA                    NA      NA    
## sloop                NA              NA                    NA      NA    
## snow                 NA              NA                    NA      NA    
## sourcetools          NA              NA                    NA      NA    
## sp                   NA              NA                    NA      NA    
## spam                 NA              NA                    NA      NA    
## SparseM              NA              NA                    NA      NA    
## spatial              NA              NA                    NA      NA    
## splines              NA              NA                    NA      NA    
## SQUAREM              NA              NA                    NA      NA    
## stats                NA              NA                    NA      NA    
## stats4               NA              NA                    NA      NA    
## stringdist           NA              NA                    NA      NA    
## stringi              "yes"           NA                    NA      NA    
## stringr              NA              NA                    NA      NA    
## SummarizedExperiment NA              NA                    NA      NA    
## survival             NA              NA                    NA      NA    
## sys                  NA              NA                    NA      NA    
## tcltk                NA              NA                    NA      NA    
## testns               NA              NA                    NA      NA    
## testthat             NA              NA                    NA      NA    
## tibble               NA              NA                    NA      NA    
## tidyr                NA              NA                    NA      NA    
## tidyselect           NA              NA                    NA      NA    
## tidyverse            NA              NA                    NA      NA    
## timeDate             NA              NA                    NA      NA    
## tinytex              NA              NA                    NA      NA    
## tools                NA              NA                    NA      NA    
## UpSetR               NA              NA                    NA      NA    
## usethis              NA              NA                    NA      NA    
## utf8                 NA              NA                    NA      NA    
## utils                NA              NA                    NA      NA    
## uuid                 NA              NA                    NA      NA    
## vctrs                NA              NA                    NA      NA    
## vegan                NA              NA                    NA      NA    
## vipor                NA              NA                    NA      NA    
## viridisLite          NA              NA                    NA      NA    
## wbr                  NA              NA                    NA      NA    
## wbrlims              NA              NA                    NA      NA    
## webshot              NA              NA                    NA      NA    
## whisker              NA              NA                    NA      NA    
## withr                NA              NA                    NA      NA    
## xfun                 NA              NA                    NA      NA    
## XML                  NA              NA                    NA      NA    
## xml2                 NA              NA                    NA      NA    
## xmlparsedata         NA              NA                    NA      NA    
## xopen                NA              NA                    NA      NA    
## xtable               NA              NA                    NA      NA    
## XVector              NA              NA                    NA      NA    
## yaml                 NA              NA                    NA      NA    
## zeallot              NA              NA                    NA      NA    
## zip                  NA              NA                    NA      NA    
## zlibbioc             NA              NA                    NA      NA    
## zoo                  NA              NA                    NA      NA    
##                      NeedsCompilation Built  
## abind                "no"             "3.6.0"
## ade4                 "yes"            "3.6.0"
## ape                  "yes"            "3.6.0"
## askpass              "yes"            "3.6.0"
## assertthat           "no"             "3.6.0"
## backports            "yes"            "3.6.0"
## base                 NA               "3.6.1"
## base64enc            "yes"            "3.6.0"
## beeswarm             "no"             "3.6.0"
## BH                   "no"             "3.6.0"
## bindr                "no"             "3.6.0"
## bindrcpp             "yes"            "3.6.0"
## Biobase              "yes"            "3.5.1"
## BiocGenerics         "no"             "3.5.1"
## BiocManager          "no"             "3.6.1"
## BiocParallel         "yes"            "3.5.2"
## BiocVersion          "no"             "3.5.1"
## biomformat           "no"             "3.5.2"
## Biostrings           "yes"            "3.5.2"
## bit                  "yes"            "3.6.0"
## bit64                "yes"            "3.6.0"
## bitops               "yes"            "3.6.0"
## bizarro              NA               "3.5.2"
## boot                 "no"             "3.6.0"
## brew                 NA               "3.6.0"
## broom                "no"             "3.6.0"
## callr                "no"             "3.6.0"
## car                  "no"             "3.6.0"
## carData              "no"             "3.6.0"
## caret                "yes"            "3.6.0"
## caTools              "yes"            "3.6.0"
## cellranger           "no"             "3.6.0"
## class                "yes"            "3.6.1"
## cli                  "no"             "3.6.0"
## cliapp               "no"             "3.6.0"
## clipr                "no"             "3.6.0"
## clisymbols           "no"             "3.6.0"
## cluster              "yes"            "3.6.1"
## codetools            "no"             "3.6.1"
## colorspace           "yes"            "3.6.0"
## commonmark           "yes"            "3.6.0"
## compiler             NA               "3.6.1"
## conflicted           "no"             "3.6.0"
## corpcor              "no"             "3.6.0"
## covr                 "yes"            "3.6.0"
## cowplot              "no"             "3.6.0"
## cranlogs             "no"             "3.6.0"
## crayon               "no"             "3.6.0"
## crosstalk            "no"             "3.6.0"
## curl                 "yes"            "3.6.0"
## cyclocomp            "no"             "3.6.0"
## cyl                  NA               "3.5.2"
## dada2                "yes"            "3.5.2"
## data.table           "yes"            "3.6.1"
## datasets             NA               "3.6.1"
## DBI                  "no"             "3.6.0"
## dbplyr               "no"             "3.6.0"
## decontam             "no"             "3.5.2"
## DelayedArray         "yes"            "3.5.1"
## DEoptimR             "no"             "3.6.0"
## desc                 "no"             "3.6.0"
## devtools             "no"             "3.6.0"
## digest               "yes"            "3.6.0"
## docopt               "no"             "3.6.0"
## doParallel           "no"             "3.6.0"
## dotCall64            "yes"            "3.6.0"
## dplyr                "yes"            "3.6.0"
## DT                   "no"             "3.6.0"
## e1071                "yes"            "3.6.0"
## ellipsis             "yes"            "3.6.0"
## EMD                  "yes"            "3.6.0"
## enc                  "yes"            "3.6.0"
## evaluate             "no"             "3.6.0"
## fansi                "yes"            "3.6.0"
## fastmap              "yes"            "3.6.0"
## fastmatch            "yes"            "3.6.0"
## fields               "yes"            "3.6.0"
## filelock             "yes"            "3.6.0"
## flexdashboard        "no"             "3.6.0"
## flowCore             "yes"            "3.5.2"
## flowPeaks            "yes"            "3.5.2"
## foofactor            "no"             "3.5.2"
## forcats              "no"             "3.6.0"
## foreach              "no"             "3.6.0"
## foreign              "yes"            "3.6.0"
## formatR              "no"             "3.6.0"
## fs                   "yes"            "3.6.0"
## futile.logger        "no"             "3.6.0"
## futile.options       "no"             "3.6.0"
## generics             "no"             "3.6.0"
## GenomeInfoDb         "no"             "3.5.2"
## GenomeInfoDbData     "no"             "3.5.2"
## GenomicAlignments    "yes"            "3.5.2"
## GenomicRanges        "yes"            "3.5.1"
## geometry             "yes"            "3.6.0"
## GGally               "no"             "3.6.0"
## ggbeeswarm           "no"             "3.6.0"
## ggplot2              "no"             "3.6.0"
## ggridges             "no"             "3.6.0"
## gh                   "no"             "3.6.0"
## git2r                "yes"            "3.6.0"
## glue                 "yes"            "3.6.0"
## googlesheets         "no"             "3.6.0"
## gower                "yes"            "3.6.0"
## graph                "yes"            "3.5.1"
## graphics             "yes"            "3.6.1"
## grDevices            "yes"            "3.6.1"
## grid                 "yes"            "3.6.1"
## gridExtra            "no"             "3.6.0"
## gtable               "no"             "3.6.0"
## haven                "yes"            "3.6.0"
## here                 "no"             "3.6.0"
## hexbin               "yes"            "3.6.0"
## highr                "no"             "3.6.0"
## hms                  "no"             "3.6.0"
## htmltools            "yes"            "3.6.0"
## htmlwidgets          "no"             "3.6.0"
## httpuv               "yes"            "3.6.0"
## httr                 "no"             "3.6.0"
## hwriter              "no"             "3.6.0"
## igraph               "yes"            "3.6.0"
## ini                  "no"             "3.6.0"
## ipred                "yes"            "3.6.0"
## ips                  "no"             "3.6.0"
## IRanges              "yes"            "3.5.1"
## itdepends            "no"             "3.5.2"
## iterators            "no"             "3.6.0"
## jsonlite             "yes"            "3.6.0"
## kernlab              "yes"            "3.6.0"
## KernSmooth           "yes"            "3.6.1"
## kmer                 "yes"            "3.6.0"
## knitr                "no"             "3.6.0"
## labeling             "no"             "3.6.0"
## labrador             NA               "3.5.2"
## labradorbase         NA               "3.5.2"
## lambda.r             "no"             "3.6.0"
## later                "yes"            "3.6.0"
## lattice              "yes"            "3.6.1"
## latticeExtra         "no"             "3.6.0"
## lava                 "no"             "3.6.0"
## lazyeval             "yes"            "3.6.0"
## lifecycle            "no"             "3.6.0"
## linprog              NA               "3.6.0"
## lintr                "no"             "3.6.0"
## lme4                 "yes"            "3.6.0"
## lobstr               "yes"            "3.6.0"
## locfit               "yes"            "3.6.0"
## lpSolve              "yes"            "3.6.0"
## lubridate            "yes"            "3.6.0"
## magic                "no"             "3.6.0"
## magrittr             "no"             "3.6.0"
## manipulateWidget     "no"             "3.6.0"
## maps                 "yes"            "3.6.0"
## maptools             "yes"            "3.6.0"
## markdown             "yes"            "3.6.0"
## MASS                 "yes"            "3.6.1"
## Matrix               "yes"            "3.6.1"
## MatrixModels         "no"             "3.6.0"
## matrixStats          "yes"            "3.6.0"
## mean2                NA               "3.5.2"
## memoise              "no"             "3.6.0"
## methods              "yes"            "3.6.1"
## mgcv                 "yes"            "3.6.0"
## mime                 "yes"            "3.6.0"
## miniUI               "no"             "3.6.0"
## minpack.lm           "yes"            "3.6.0"
## minqa                "yes"            "3.6.0"
## ModelMetrics         "yes"            "3.6.0"
## modelr               "no"             "3.6.0"
## MPN                  "no"             "3.6.0"
## multtest             "yes"            "3.5.1"
## munsell              "no"             "3.6.0"
## mvtnorm              "yes"            "3.6.0"
## new                  NA               "3.5.2"
## nlme                 "yes"            "3.6.0"
## nloptr               "yes"            "3.6.0"
## nnet                 "yes"            "3.6.1"
## numDeriv             "no"             "3.6.0"
## openssl              "yes"            "3.6.0"
## openxlsx             "yes"            "3.6.0"
## parallel             "yes"            "3.6.1"
## pbkrtest             "no"             "3.6.0"
## pcaPP                "yes"            "3.6.0"
## permute              "no"             "3.6.0"
## phangorn             "yes"            "3.6.0"
## phylogram            "no"             "3.6.0"
## phyloseq             "no"             "3.5.2"
## pillar               "no"             "3.6.0"
## pkgbuild             "no"             "3.6.0"
## pkgcache             "no"             "3.6.0"
## pkgconfig            "no"             "3.6.0"
## pkgload              "yes"            "3.6.0"
## plogr                "no"             "3.6.0"
## plotly               "no"             "3.6.0"
## plyr                 "yes"            "3.6.0"
## praise               "no"             "3.6.0"
## prettycode           "no"             "3.6.0"
## prettyunits          "no"             "3.6.0"
## processx             "yes"            "3.6.0"
## prodlim              "yes"            "3.6.0"
## progress             "no"             "3.6.0"
## promises             "yes"            "3.6.0"
## pryr                 "yes"            "3.6.0"
## ps                   "yes"            "3.6.0"
## pspline              "yes"            "3.6.0"
## purrr                "yes"            "3.6.0"
## qpcR                 "yes"            "3.6.0"
## quadprog             "yes"            "3.6.0"
## quantreg             "yes"            "3.6.0"
## R6                   "no"             "3.6.0"
## rappdirs             "yes"            "3.6.0"
## rcmdcheck            "no"             "3.6.0"
## RColorBrewer         "no"             "3.6.0"
## Rcpp                 "yes"            "3.6.0"
## RcppEigen            "yes"            "3.6.0"
## RcppParallel         "yes"            "3.6.0"
## RcppProgress         "no"             "3.6.0"
## RcppRoll             "yes"            "3.6.0"
## RCurl                "yes"            "3.6.0"
## readr                "yes"            "3.6.0"
## readxl               "yes"            "3.6.0"
## recipes              "no"             "3.6.0"
## rematch              "no"             "3.6.0"
## rematch2             "no"             "3.6.0"
## remotes              "no"             "3.6.0"
## reprex               "no"             "3.6.0"
## requirements         "no"             "3.5.2"
## reshape              "yes"            "3.6.0"
## reshape2             "yes"            "3.6.0"
## rex                  "no"             "3.6.0"
## rgl                  "yes"            "3.6.0"
## rhdf5                "yes"            "3.5.2"
## Rhdf5lib             "yes"            "3.5.3"
## rio                  "no"             "3.6.0"
## rlang                "yes"            "3.6.0"
## rmarkdown            "no"             "3.6.0"
## robustbase           "yes"            "3.6.0"
## roxygen2             "yes"            "3.6.0"
## roxygen2md           "no"             "3.6.0"
## rpart                "yes"            "3.6.1"
## rpivotTable          "no"             "3.6.0"
## rprojroot            "no"             "3.6.0"
## rrcov                "yes"            "3.6.0"
## Rsamtools            "yes"            "3.5.2"
## rstudioapi           "no"             "3.6.0"
## rversions            "no"             "3.6.0"
## rvest                "no"             "3.6.0"
## S4Vectors            "yes"            "3.5.1"
## scales               "yes"            "3.6.0"
## segmented            "no"             "3.6.0"
## selectr              "no"             "3.6.0"
## seqinr               "yes"            "3.6.0"
## sessioninfo          "no"             "3.6.0"
## sfsmisc              "no"             "3.6.0"
## shiny                "no"             "3.6.0"
## ShortRead            "yes"            "3.5.1"
## sloop                "no"             "3.6.0"
## snow                 "no"             "3.6.0"
## sourcetools          "yes"            "3.6.0"
## sp                   "yes"            "3.6.0"
## spam                 "yes"            "3.6.0"
## SparseM              "yes"            "3.6.0"
## spatial              "yes"            "3.6.1"
## splines              "yes"            "3.6.1"
## SQUAREM              "no"             "3.6.0"
## stats                "yes"            "3.6.1"
## stats4               NA               "3.6.1"
## stringdist           "yes"            "3.6.0"
## stringi              "yes"            "3.6.0"
## stringr              "no"             "3.6.0"
## SummarizedExperiment "no"             "3.5.1"
## survival             "yes"            "3.6.1"
## sys                  "yes"            "3.6.0"
## tcltk                "yes"            "3.6.1"
## testns               NA               "3.5.2"
## testthat             "yes"            "3.6.0"
## tibble               "yes"            "3.6.0"
## tidyr                "yes"            "3.6.0"
## tidyselect           "yes"            "3.6.0"
## tidyverse            "no"             "3.6.0"
## timeDate             "no"             "3.6.0"
## tinytex              "no"             "3.6.0"
## tools                "yes"            "3.6.1"
## UpSetR               "no"             "3.6.0"
## usethis              "no"             "3.6.0"
## utf8                 "yes"            "3.6.0"
## utils                "yes"            "3.6.1"
## uuid                 "yes"            "3.6.0"
## vctrs                "yes"            "3.6.0"
## vegan                "yes"            "3.6.0"
## vipor                "no"             "3.6.0"
## viridisLite          "no"             "3.6.0"
## wbr                  "yes"            "3.5.2"
## wbrlims              NA               "3.6.1"
## webshot              "no"             "3.6.0"
## whisker              "no"             "3.6.0"
## withr                "no"             "3.6.0"
## xfun                 "no"             "3.6.0"
## XML                  "yes"            "3.6.0"
## xml2                 "yes"            "3.6.0"
## xmlparsedata         "no"             "3.6.0"
## xopen                "no"             "3.6.0"
## xtable               "no"             "3.6.0"
## XVector              "yes"            "3.5.1"
## yaml                 "yes"            "3.6.0"
## zeallot              "no"             "3.6.0"
## zip                  "yes"            "3.6.0"
## zlibbioc             "yes"            "3.5.1"
## zoo                  "yes"            "3.6.0"
```

Loading the R project code with the `use_course` command

```r
library(usethis)
use_course("rstd.io/wtf-explore-libraries", "~/Documents/Workshop/WTFaboutR") # Timed out because of too many people, manually downloaded from github
```
Below is copied from `01_explore-libraries_comfy.R`

```r
#' Which libraries does R search for packages?

# try .libPaths(), .Library


#' Installed packages

## use installed.packages() to get all installed packages
## if you like working with data frame or tibble, make it so right away!
## remember to use View(), dplyr::glimpse(), or similar to inspect
library(data.table)
pkgs <- installed.packages() %>% data.table

## how many packages?
dim(pkgs) 
# 308 packages

#' Exploring the packages

## count some things! inspiration
##   * tabulate by LibPath, Priority, or both
pkgs[, .N, by = .(LibPath)]
pkgs[, .N, by = .(Priority)]

##   * what proportion need compilation?
pkgs[, .N/nrow(pkgs), by = .(NeedsCompilation)]

##   * how break down re: version of R they were built on
pkgs[, .N, by = .(Built)]

## for tidyverts, here are some useful patterns
# data %>% count(var)
# data %>% count(var1, var2)
# data %>% count(var) %>% mutate(prop = n / sum(n))

#' Reflections

## reflect on ^^ and make a few notes to yourself; inspiration
##   * does the number of base + recommended packages make sense to you?
# I guess it's an indication that getting priority on CRAN is difficult? From stackoverflow, base R are not actually packages at all and are included in every R distribution. In contrast, the 'recommended' packages are specifically installed.


##   * how does the result of .libPaths() relate to the result of .Library?
.Library
.libPaths()

#' Going further

## if you have time to do more ...

## is every package in .Library either base or recommended?
# No, most are not either of these! Only R core can set these

## study package naming style (all lower case, contains '.', etc)

## use `fields` argument to installed.packages() to get more info and use it!
```

## Adopt a project oriented workflow
Why? Create isolated unit for each project - easier to work on multiple projects, collaborate/distribute, and start and stop

How? 
* Lowest tech is dedicated directory - manual curation. 
* Rstudio Project - feature in Rstudio to track 
* Git repo

Bad practices
* setwd at the top of a script to a local path that only I have - doesn't work for anyone else! 
* rm(list = ls()) - usually suggested to do a 'clean slate' but does not remove full environment and could interfere with the working environment of others

Instead - workflows instead of scripts
<https://www.tidyverse.org/articles/2017/12/workflow-vs-script/>
<https://whattheyforgot.org/>

What is an Rstudio Project?
* dedicated instance of Rstudio
* file browser pointed to project directory
* working directory also pointed to project directory

Use a 'blank slate' options
* DO NOT restore .Rdata
* "NEVER" save workspace on exit

### Practice
Create a new R project with create_project

```r
usethis::create_project("~/Documents/Workshop/WTFaboutR/new_project")
```

"Safe paths"
* relative to a stable base - if you have copies of the project around, it should work across those copies. 
  * project directory, user's home directory, official location for installed software
* Use file system functions (NOT `paste`, `strsplit`, etc)

Rather than hard coding the absolute path, create the path at runtime relative to the stable base

Two packages
* "fs"
* "here" - build paths inside a project
  * top level of the project is the working directory and forms the paths at runtime
  * it knows where you are in the tree and will give the correct location even if the relative path has changed (e.g. working directory is now in a subfolder)
  


```r
install.packages("fs")
install.packages("here")
```


```r
library(usethis)
use_course("rstats-wtf/wtf-fix-paths", "~/Documents/Workshop/WTFaboutR/")
```

Exercises within the `wtf-fix-paths.Rproj`

Syntax for here::here() arguments are separated by commas for easier integration with variables.

## Names
Names should: be machine readable, human readable, and sort nicely

Machine readable - regular expressions and globbing, delimiter use consistent
Human readable - name contains context info, and use user friendly names (longer, more informative)
Sort nicely - put something numeric and left pad with 0s for width, use the ISO 8601 (YYYY-MM-DD) for dates, order chronological or common sense

Example names - they used underscores to delimit fields (e..g number, topic, type) while dashes allow for multi-word fields

## Project modularity
Break logic and output into pieces rather than a monolithic script (e.g. parsing, wrangling, analyzing, visualizing, reporting)


```r
use_course("rstd.io/wtf-packages-report", "~/Desktop/")
```

For distribution - how to handle dependencies? Renv is a package for managing that 

## Debugging
<https://rstats.wtf/debugging-r-code.html>
Usually confront an error message. Places to search:
* google exact error message
* keyword search on community.rstudio.com
* stackoverflow [r] tag

Tools for debugging
* traceback() - look at call stack 
* inspect objects (e.g. print, cat, str)
* browser() - puts into interactive debugger
* debug, trace, recover - inspecting code that you don't have full control over (debugging someone else's code, like a package)

*Traceback*
Read the commands bottom to top

Could create a shortcut in .Rprofile
Or can use rlang with `options(error = rlang::entrace)`. `rlang::last_error()` and `rlang::last_trace()`

Traceback is informative for the maintainer of code to determine where the error occurred. 

*Print*
Printing messages can help identify where the error occurs. 

*str*
Gives structure of the variable

*browser*
Puts you into the interactive debugger. Let's your run any R command at the location of the `browser()` function call, e.g. ls, print, str. 

Controlling execution:
* n = next statement - run next statement and then stop again
* c = continue - keep running until error or finish
* s = step into function call
* f = finish loop/function - then stop
* where = show previous calls
* Q - quit debugger

Exercises in `wtf-debugging-master`

*RStudio debugging breakpoints*
Clicking at a line number inserts a breakpoint - same as adding `browser()` at that line when the file is sourced

*Debug error inspector*
Re-run with debug is not as useful because it usually goes too low level

*Debug console*
Buttons for the commands

*recover*
Like browser but more powerful
Gives a dialogue to ask where to recover from. Enter again and goes back to the selection menu for where to inspect.

Can set the global option: `options(error = recover)` so that dialog always gets brought up when an error occurs. Can reset back to `error = NULL`

### Debug exercise 2
Debugging with pipes can be difficult - can try to use without pipes first. 
`options(error = rlang::entrace)` filters the backtrace to only keep the relevant function calls


*debug*
puts a browser statement at the beginning of the argument

*trace* 
allows you to put any code into other code
can also specify where in the function to add the code

Can explore the location of code using `as.list` to add code with trace

## Version control
Track the evolution of the project at the snapshots, or "commits" - a state that is meaningful to you for inspection, comparison, restoration.

<https://doi.org/10.7287/peerj.preprints.3159v2> paper about version control
<https://happygitwithr.com> book about git with R

### Project initiation
Make a remote copy of their remote repo - "fork"
Make a local project from a remote - "clone" - first focus
Make a remote repo from a local project - a little fiddly

*Clone*
daily work, push and pull from local to remote
Possible to clone someone else's repo but not as useful because you can't upload those changes into that repo 

*Fork*
Copy a remote repo into your Github account, then clone it to a local copy so you can do the push and pull with your repo. Then can do a pull request back to original repo you forked from (how to contribute to other people's stuff)

*new project, github first*
This approach glosses over a couple big technical points: remotes and branches. 

Created `packages-report` Git repo. When the R project is created Github first, there's a Git tab next to Environment. Diff will then show what's changed from the last commit. 

Two step process: "add"/"stage" and then "commit"

When do you need to stage?
You do every time you want to save a snapshot/commit. Git window will show which files got edited with "M" for modified file. 

What should you include in a commit?
* .Rproj can be useful for collaboration
* .gitignore - Kara uses it to keep consistent across machines

Push by clicking green up arrow button.

*Writing vs reading*
Difference between what you write vs what people like to read

Compile report button in Rstudio is ~"render::Rmarkdown"

Github does not render .html but Markdown .md files are useful. Render to .md instead of .html. Do this using the comment at the top:

```r
# Only html output
#' ---
#' title: "Untitled"
#' output: html_document
#' ---

# Keep the .md
#' ---
#' title: "Untitled"
#' output: 
#'  html_document:
#'    keep_md: yes
#' ---


# Only md
#' output: md_document

# github document
#' output: github_document
```


Takeaways:
1. Consider putting rendered products on GitHub
2. Markdown (.md) is much more useful on Github than html, docx, pdf. Binary formats like docx and pdf are very difficult to resolve merge conflicts, so be wary of tracking them with Git.







# Downloading course materials

```r
use_course("rstd.io/wtf-startup", destdir = "~/Documents/Workshop/WTFaboutR")
```
Try reinstalling curl and test with a simple download. Somehow the timeout from curl is crashing R. 

