---
title: "titel "
author: "my_name"
date: "`r Sys.Date()`"

header-includes:
   - \usepackage{longtable}
   - \usepackage{hyperref}
output:
    pdf_document:
      number_sections: yes
linkcolor: blue
---


```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

# Introduction
In this research mRNA dynamic is programmed.  

The number of mRNA transcripts is researched by means of the rate in decay of existing transcripts and the number of new transcripts produced per second. This resulted in the answer to the question: "What is the difference in number of mRNA over time, in different conditions?". To answer this question multiple sub questions, need to be answered. These questions include: 

- "What is the difference in number of mRNA over time, when the system is at the steady state?" 

- "What is the difference in number of mRNA over time, when mRNA is increasing over time?" 

- "What is the difference in number of mRNA over time, when mRNA is decreasing over time?" 


## Goal

Simulating the amount of mRNA transcripts over time in 3 various conditions: 

1. System is in steady state. 
2. Number of mRNA is increasing over time. 
3. Number of mRNA is decreasing over time. 

The expectation differs between the conditions. The first hypothesis, H0, is: There is no difference in the number of mRNA transcripts over time. The second hypothesis, H1, is: There is difference in the number of mRNA transcripts over time.  

To reach the goal the R package deSolve is used. There are two parameters programmed: r and m. Also, the time over which the number of mRNA is programmed. By using the “euler”-method the number of mRNA transcripts is calculated.  

## Theory

- Describe biological model
- Picture of the biological model

```{r, echo=FALSE, out.width='95%'}
#knitr::include_graphics('example.png')
```
Give an explanation of the model with citations of source \cite{Soertaert10} (replace this with actual source)
and formula explanation

$$\frac{\delta R}{\delta t} = -r * R + m $$
Describe each element and the transformations

# Methods

## The software model

- Describe the software tools used, as well as the libraries
- Describe the software implementation (note: code below is an example)
```{r}
library(deSolve)
parameters <- c(r = 0.5, m = 50) 
parameters2 <- parameters
parameters3 <- parameters
parameters2[1] <- 0.4
parameters3[1] <- 0.65


# define model 
transcripts <- function(t, R, parms){
  with(as.list(c(parms)),{
         dR <- -r * R + m
         return(list(c(dR)))
       }
       )
}

#initial state
state <- c(R = 100)

#define time sequence you want to run the model
times <- seq(0, 10,  by = 0.1)

# run simulation using continuous approach
out  <- ode(times = times, y = state,   parms = parameters, func = transcripts, method = "euler")
out2 <- ode(times = times, y = state,   parms = parameters2, func = transcripts, method = "euler")
out3 <- ode(times = times, y = state,   parms = parameters3, func = transcripts, method = "euler")


```

## Model configuration

Explain chosen initial state, parameter values and time sequence. Use tables with values as for example below
\begin{longtable}[l]{l|l|l}
\caption{Parameter Values} \\ \hline
\label{param_table}
$\textbf{Parameter}$             &$\textbf{Value}$& $\textbf{Unit}$              \\ \hline
\endhead
$a$       & 0.08  & $hour^{-1}$         \\ \hline
$b$       & 0.06  & $hour^{-1}$         \\ \hline
$c$       & 0.06  & $hour^{-1}$         \\ \hline
\end{longtable}


# Results
Introduction of results, how does it answer your research questions.
```{r}
plot(out, out2, out3, main = "ammount of mRNA transcripts over time", ylab="number of mRNA transcripts", xlab="timepoint", lty=1, col = c("black", "purple", "orange"))
legend(x = 7.5, y = 95, lty = 1, col = c("black", "purple", "orange"), legend = c("Steady", "Increase", "Decrease"))
```

This research is conducting an experiment to look at the difference in number of mRNA, in different conditions in time. In figure 1, the amount of mRNA transcripts over time, is shown. The black line is the line that displays the number of mRNA changes over time when a system is at the steady state. In the steady state is there no difference in number because the rate of decay of existing transcripts is the same amount as the number of new transcripts produced. We accept the H0 hypothesis. 

There are changes in the number of mRNA over time when the system is not steady, which means the system either increases or decreases in the number of mRNA.  
In figure 1, the purple line displays the number of mRNA when the number of mRNA is increasing over time. This means that the number of new transcripts produced is higher than the rate of decay of existing transcripts. Over time the system is reaches an equilibrium state, in this state the number of new transcripts produced is equal to the rate of decay of existing transcripts. 
The yellow line in figure 1, displays the number of mRNA when the number of mRNA is decreasing over time. This means that the rate of decay of existing transcripts is higher than the number of new transcripts produced. This system also, reaches an equilibrium state, which means that the number of new transcripts produced is equal to the rate of decay of existing transcripts. 
In both of these cases we reject the H0 hypothesis and accept H1 hypothesis.  


# Discussion and Conclusion
## Discussion
- Compare your results with what is expecting from the literature and discuss differences with them.
- Discuss striking and surprising results.
- Discuss weaknesses in your research and how they could be addressed.

## General conclusion and perspective
Discuss what your goal was, what the end result is and how you could continue working from here.


\begin{thebibliography}{9}

\bibitem{Soertaert10}
Soetaert, K., Petzoldt, T., and Woodrow Setzer, R.: \textit{Solving differential equations in R: package deSolve}, J. Stat. Softw., 33, 1-25, 2010.

\end{thebibliography}
