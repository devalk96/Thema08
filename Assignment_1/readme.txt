Author:
	Kasper Notebomer, Susan Reefman, Sander Bouwman

Date:
    23-april-2021

Version:
    1.0

Name:
    Deelopdracht_1


Description
This project aims to simulate the change in mRNA using the decay and synthesis of mRNA using deSolve with the “Euler” method of modelling. 


Installation:
    Requirements:
            R (R-Studio or alternative)
		R packages:
					- deSolve (https://CRAN.R-project.org/package=deSolve)



Usage:
    1. Open Assignment_1.Rmd with R-Studio.
    2. It is possible to change the simulation output by changing various parameters: 
		-  The variable “state” (R) corresponds to the starting amount of mRNA molecules.
		-  times will alter the starting/stopping time, increments can also be supplied.
		-  for more info visit the docs for deSolve, as the function ode is used.
		-  To change the rate of decay change the parameter r, decay is set as a percentage.
		-  To change the amount of mRNA synthesis change the parameter M.
   3. Knit to generate a PDF report.

Support:
    Kasper Notebomber: k.a.notebomer@st.hanze.nl
    Susan Reefman: h.s.reefman@st.hanze.nl
    Sander Bouwman: s.j.bouwman@st.hanze.nl
