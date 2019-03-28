README

This repository shows the process of the Data Visualization group and its results.

Aim

Use the BrAPI calls implemented in OpenSILEX / PHIS to retrieve both environmental and phenotypic data and then display them in a responsive histogram.

For this purpose, we will test if it is possible to adapt the BrAPI-Graphical-Filtering BrAPP created by the BrAPI team : https://github.com/solgenomics/BrAPI-Graphical-Filtering
Process step by step

    Connect to GitHub and download the R app created by Jean-Eudes Hollebecq (optionnally, fork this repository) : https://github.com/OpenSILEX/opensilex-datavis-rapp-demo

git clone https://github.com/OpenSILEX/opensilex-datavis-rapp-demo.git

    Change your directory name from "opensilex-datavis-rapp-demo" to something else (e.g. "hackathonApp")

    Double-click on the .RProj file to open with RStudio the project you downloaded from GitHub

    Install the packages necessary to communicate with OpenSILEX / PHIS Web Services :

devtools::install_github("OpenSILEX/phisWSClientR", build_vignettes=TRUE) #"sanchezi/docAppPhisWSClientR"
devtools::install_github("OpenSILEX/opensilex-datavis-rapp-demo", build_vignettes=TRUE)

    Initialize your connection with opensilex.org and get a token using the following R code :

library(phisWSClientR)
initializeClientConnection(apiID="ws_private", url = "www.opensilex.org/openSilexAPI/rest/")
token <- getToken("guest@opensilex.org","guest")$data

    Explore the phisWSClientR package functions :

?phisWSClientR::getEnvironmentData

    Explore the compareVariableDemo package (dowloaded from the OpenSILEX/opensilex-datavis-rapp-demo repository) functions :

library(compareVariableDemo)

    Change the plotVarDemo.R file using RStudio to your new R visualization

    Change the getDF.R file in order to create a table based on your filters

    The variables of interest in our example are :

    LAI : http://www.opensilex.org/demo/id/variables/v001
    maximum wind speed : http://www.opensilex.org/demo/id/variables/v004

    The changes made by Jean-Eudes are available in the GitHub repository he just created :

https://github.com/JeanEudesH/hackathonApp

This app requires OPENCPU to run R code within the web application. It requires some installation.
But it also works with R only, but just the R script and not the web app.

Because it is the result of a hackathon session. It is very minimal and not stable at all.
