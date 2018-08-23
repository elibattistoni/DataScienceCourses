---
title: "Final’s project Shiny App"
author: "Elisa Battistoni"
output: 
  ioslides_presentation: 
    keep_md: yes
---


## Predicting animal's body weigth from brain weigth

This is an R Markdown presentation, hosted on Github Pages.

It contains a description of the Shiny App created for the final project of the **Developing Data Products** Course in the Data Science Specialization.

The **MASS package** contains the **Animals** dataset, which contains the average brain and body weights for 28 species of land animals.
I created a simple linear model with the animal's brain weight as predictor and the animal's body weigth as outcome. Since visual inspection of the data showed an outlier, it was removed before fitting the linear model. The following slide shows the R code.

## R code for the linear model


```r
library(MASS) # load library
data(Animals) # load data

idx_outlier = which(Animals$body == max(Animals$body)) # find outlier
Animals = Animals[-idx_outlier,] # remove outlier

model <- lm(body ~ brain, Animals) # fit a simple linear model
data.frame(pvalue = summary(model)$coefficients[2,4])
```

```
     pvalue
1 0.1177583
```
<font size="4"> The p-value highlights that, in fact, you fail to reject the null hypothesis, therefore an animal's brain weigth is not a good predictor of an animal's body weigth. </font>

## R code in the ui.R file

```r
library(shiny)
shinyUI(fluidPage(
    titlePanel("Predict Animals' Body Weight (kg) From Brain Weight (gr)"),
    sidebarLayout(
        sidebarPanel(
            sliderInput("sliderBRAINWT", 
                        "Choose the animal's brain weight (gr)", 
                        0, 6000, value = 1000),
            checkboxInput("showModel", "Show/Hide Model", 
                          value = TRUE),
            submitButton("OK")
        ),
        mainPanel(
            textOutput("introduction"),
            plotOutput("plot_body_weight"),
            h4("Predicted Body Weight (kg) from Model:"),
            textOutput("prediction")
        )
    )
))
```


## Part of the R code in the server.R file

```r
library(shiny)
library(MASS)
shinyServer(function(input, output) {
    data(Animals)
    idx_outlier = which(Animals$body == max(Animals$body))
    Animals = Animals[-idx_outlier,]
    model <- lm(body ~ brain, Animals)
    output$introduction <- renderText({
        "..."
    })
    modelpred <- reactive({
        BrainInput <- input$sliderBRAINWT
        predict(model, data.frame(brain = BrainInput))
    })
    output$plot_body_weight <- renderPlot({
        BrainInput <- input$sliderBRAINWT
        plot(Animals$brain, Animals$body, xlab = "Brain weight (gr)", 
             ylab = "Body weight (kg)", pch = 16, cex = 2)
        if(input$showModel){
            abline(model, col = "purple", lwd = 3)
        }
        legend(3500, 10000, "ModelPrediction", cex = 1.5, pch = 16, 
               col = "purple", bty = "n", pt.cex = 2)
        points(BrainInput, modelpred(), col = "purple", pch = 16, cex = 2)
    })
    output$prediction <- renderText({
        modelpred()
    })
})
```
