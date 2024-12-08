---
author:
- Steven Lopez
authors:
- Steven Lopez
title: BGGN213_Lopez_Lab6
toc-title: Table of contents
---

# Intro to functions lecture activities

::: cell
``` {.r .cell-code}
add <- function(x,y) {
  x+y
}
```
:::

Can I execute this chunk?

::::: cell
``` {.r .cell-code}
add (1,1)
```

::: {.cell-output .cell-output-stdout}
    [1] 2
:::

``` {.r .cell-code}
add (c(100,1),1)
```

::: {.cell-output .cell-output-stdout}
    [1] 101   2
:::
:::::

::: cell
``` {.r .cell-code}
add<-function(x, y=1) {
  x+y
}
```
:::

:::::: cell
``` {.r .cell-code}
add(5)
```

::: {.cell-output .cell-output-stdout}
    [1] 6
:::

``` {.r .cell-code}
add (1,3)
```

::: {.cell-output .cell-output-stdout}
    [1] 4
:::

``` {.r .cell-code}
add (c(100,1),2)
```

::: {.cell-output .cell-output-stdout}
    [1] 102   3
:::
::::::

:::: cell
``` {.r .cell-code}
add <- function(x, y, z) {
  x+y+z
}
add(10, 1, 1)
```

::: {.cell-output .cell-output-stdout}
    [1] 12
:::
::::

Make a function "generate_DNA()" that makes a random nucleotide sequence
of any length.

:::: cell
``` {.r .cell-code}
#generate_DNA <- function() {
bases <- c("A", "C", "G", "T")
sample(bases, size = 5, replace = TRUE)
```

::: {.cell-output .cell-output-stdout}
    [1] "C" "T" "C" "T" "A"
:::
::::

Make function

:::: cell
``` {.r .cell-code}
generate_DNA <- function(length) {
  bases <- c("A", "C", "G", "T")
  sequence <- sample(bases, size = length, replace = TRUE)
  return(sequence)
}
generate_DNA(10)
```

::: {.cell-output .cell-output-stdout}
     [1] "A" "G" "G" "C" "G" "G" "T" "A" "G" "C"
:::
::::

:::: cell
``` {.r .cell-code}
#install.packages("bio3d")
library(bio3d)
unique(bio3d::aa.table$aa1)[1:20]
```

::: {.cell-output .cell-output-stdout}
     [1] "A" "R" "N" "D" "C" "Q" "E" "G" "H" "I" "L" "K" "M" "F" "P" "S" "T" "W" "Y"
    [20] "V"
:::
::::

Generate random protein sequences of length 6 to 12.

::: cell
``` {.r .cell-code}
generate_protein <- function(length){
  amino_acids <- unique(bio3d::aa.table$aa1)
  sequence <- sample(amino_acids, size=length, replace = TRUE)
  sequence <- paste(sequence, collapse = "")
  return(sequence)
}
```
:::

Sequences from length 6 to 12.

:::: cell
``` {.r .cell-code}
answer <- sapply(6:12, generate_protein)
answer
```

::: {.cell-output .cell-output-stdout}
    [1] "FVQLFK"       "NXPWRSF"      "KYQXNHCM"     "HMDPRRVIE"    "RRENDYRXLA"  
    [6] "CYCSHNXLFWE"  "DQWKIEXELNWC"
:::
::::

Run function

:::: cell
``` {.r .cell-code}
generate_protein(6)
```

::: {.cell-output .cell-output-stdout}
    [1] "CVXDVN"
:::
::::

:::: cell
``` {.r .cell-code}
paste(c("barry", "alice", "amy", "chandra"),
      "loves R")
```

::: {.cell-output .cell-output-stdout}
    [1] "barry loves R"   "alice loves R"   "amy loves R"     "chandra loves R"
:::
::::

:::: cell
``` {.r .cell-code}
paste(">id.", 6:12, "\n", answer, "\n", sep ="")
```

::: {.cell-output .cell-output-stdout}
    [1] ">id.6\nFVQLFK\n"        ">id.7\nNXPWRSF\n"       ">id.8\nKYQXNHCM\n"     
    [4] ">id.9\nHMDPRRVIE\n"     ">id.10\nRRENDYRXLA\n"   ">id.11\nCYCSHNXLFWE\n" 
    [7] ">id.12\nDQWKIEXELNWC\n"
:::
::::

:::: cell
``` {.r .cell-code}
cat(paste(">id.", 6:12, "\n", answer, "\n", sep =""), sep = "")
```

::: {.cell-output .cell-output-stdout}
    >id.6
    FVQLFK
    >id.7
    NXPWRSF
    >id.8
    KYQXNHCM
    >id.9
    HMDPRRVIE
    >id.10
    RRENDYRXLA
    >id.11
    CYCSHNXLFWE
    >id.12
    DQWKIEXELNWC
:::
::::
