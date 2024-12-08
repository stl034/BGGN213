---
title: "Class_10 Structural Bioinformatics"
author: Steven Lopez (A14837063)
format: html
---

## Running Code

When you click the **Render** button a document will be generated that includes both content and the output of embedded code. You can embed code like this:

```{r}
pdbstats <- read.csv("Data Export Summary.csv",row.names = 1)
pdbstats$Total
convert_comma_numbers <-function(x) {
  #remove commas 
  x<- gsub(',','',x)
  x<- as.numeric(x)
  return(x)
}
Total_num <- sum(convert_comma_numbers(pdbstats$Total))
Xray_sum<-sum(convert_comma_numbers(pdbstats$X.ray))
EM_sum<-sum(convert_comma_numbers(pdbstats$EM))

percentage<- Xray_sum/Total_num + EM_sum/Total_num

```

Q1. 93.49%

```{r}
library(readr)
pdb_stats<- read_csv("Data Export Summary.csv")

proteinprop<-pdb_stats$Total[1]/sum(pdb_stats$Total)
```
## Q2. 86.4%

## Using Mol*
```{r} 
library(bio3d)
pdb <- read.pdb("1hsg")
pdb
```

![](1HSG.png)

```{r}
attributes(pdb)
head(pdb$atom)
pdbseq(pdb)[25]
```

How many amino acids are in this sequence

```{r}
length( pdbseq(pdb))
```

## Functional dynamics prediction

Predicting functional motions of a single protein structure

```{r}
source ("https://tinyurl.com/viewpdb")
library(r3dmol)
view.pdb(pdb)
view.pdb(pdb, backgroundColor = "pink")
```

```{r}
adk<- read.pdb("6s36")
modes<- nma(adk)
mktrj(modes,file ="adk.pdb")
view.pdb(adk)
```
