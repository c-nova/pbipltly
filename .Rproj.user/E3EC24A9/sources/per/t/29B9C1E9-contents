################# DEBUG in RStudio #################
# setwd("C:/opt/sandbox/testVizR")
# Values <- read.csv("../testVizRDoc/HR_comma_test2.csv", sep = ",")
# fileRda = "C:/Users/maotsuka.FAREAST/AppData/Local/Temp/tempData.Rda"
# if(file.exists(dirname(fileRda)))
# {
#  if(Sys.getenv("RSTUDIO")!="")
#    load(file= fileRda)
#  else
#    save(list = ls(all.names = TRUE), file=fileRda)
# }
####################################################

source('./r_files/flatten_HTML.r')

############### Library Declarations ###############
libraryRequireInstall("ggplot2")
libraryRequireInstall("plotly")
####################################################

####### Validate number of columns and rows ########
pbiWarning <- NULL
# filter out non-numeric columns and constant columns (Should be comment if not use column test)
# correctColumn <- function(someColumn) { is.numeric(someColumn) && length(unique(someColumn)) > 1 }
# useColumns <- sapply(Values,correctColumn)
# if(sum(useColumns) < ncol(Values))
#   pbiWarning <- "Filtered out non numeric columns and constant columns"
# 
# Values <- as.data.frame(Values[,useColumns])

# filter out < 2 columns and < 2 columns
columnCount <- ncol(Values)
rowCount <- nrow(Values)

if (rowCount < 2 || columnCount < 3) {
  pbiWarning <- paste(pbiWarning, "<br><br>", "Not enough input dimensions");

# Plot error message to ggplot and convert to Plotly
  gg = ggplot()
  gg = gg + labs (title = pbiWarning, caption = NULL) + theme_bw() +
    theme(plot.title=element_text(hjust = 0.5, size = 20),
          axis.title=element_text(size =  11),
          axis.text=element_text(size =  8),
          panel.border = element_blank())
  p <- plotly_build(gg)
  internalSaveWidget(p, 'out.html')
  quit()
}
####################################################

################### Actual code ####################
p = plot_ly(Values,
            x = Values[,1],
            y = Values[,2],
            z = Values[,3],
            type = "heatmap"
)
####################################################

############# Create and save widget ###############
internalSaveWidget(p, 'out.html')
####################################################