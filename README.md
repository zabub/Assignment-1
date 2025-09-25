

# Assignment-1
vowel plots

## Plot 1
code:
```
library(readxl)
vowels <- read_excel("Grad School/LING 349 - Comp Ling/Assignment #1/vowels.xlsx")
View(vowels)
ggplot(vowels, aes(x=F2, y=F1, fill=Vowel)) +
    geom_text(aes(label=Vowel, color=Vowel)) + 
    ylim(1100, 150) +
    xlim(3500, 500) +
    stat_ellipse() +
    stat_ellipse(geom = "polygon", alpha = 0.2) +
    stat_ellipse(aes(color=Vowel), size=0.8) +
    stat_ellipse(linetype = 2, size = 0.1, level = 0.5)
    labs(x = "F2 (Hz)", y = "F1 (Hz)", title = "Vowel Chart")
```
Plot:

![Vowel Plot 1](https://github.com/user-attachments/assets/05887fb6-be81-4799-8293-4e8270a55cc3)

## Plot 2
code:
```
ggplot(vowels, aes(x=F2, y=F1, fill=Vowel)) +
    geom_text(aes(label=Vowel, color=Vowel)) + 
    ylim(1100, 200) +
    xlim(3500, 600) +
    stat_ellipse() +
    stat_ellipse(geom = "polygon", alpha = 0.2) +
    stat_ellipse(aes(color=Vowel), size=0.5) +
    stat_ellipse(linetype = 1, size = 1, level = 0.001) + 
    labs(x = "F2 (Hz)", y = "F1 (Hz)", title = "Vowel Chart") + 
    geom_density_2d(size = 0.25, colour = "black")
```
Plot:

![Vowel Plot 2](https://github.com/zabub/Assignment-1/blob/main/Vowel%20Plot%202.svg)

## Plot 3
code:
```
ggplot(vowels, aes(x=F2, y=F1,fill=Vowel)) + 
    ylim(1100,200)+xlim(3500,600) + 
    labs(x="F2 (Hz)", y="F1 (Hz)", title ="Vowel Chart") + 
    stat_density_2d(aes(fill = ..level..), bins=15)
```
Plot:

![Vowel Plot 3](https://github.com/zabub/Assignment-1/blob/main/Vowel%20Plot%203.svg)


## Plot 4
code:
```
ggplot(vowels, aes(x=F2, y=F1,fill=Vowel)) + 
    ylim(1100,200)+xlim(3500,600) + 
    labs(x="F2 (Hz)", y="F1 (Hz)", title ="Vowel Chart") + 
    stat_density_2d(aes(fill = ..level..), geom = "polygon")
```
Plot:

![Vowel Plot 4](https://github.com/zabub/Assignment-1/blob/main/Vowel%20Plot%204.svg)


## Plot 5
code:
```
library(concaveman)
library(ggforce)
ggplot(vowels, aes(x=F2, y=F1,fill=Vowel)) +
    geom_text(aes(label=Vowel, color=Vowel)) +
    ylim(1100,200)+xlim(3500,600) +
    geom_mark_hull(concavity = 10,expand=-0.025,radius=0,aes(fill=Vowel))
```
Plot:

![Vowel Plot 5](https://github.com/zabub/Assignment-1/blob/main/Vowel%20Plot%205.svg)


## Plot 6
code:
```
library(MASS)
library(plotly)
iDensity=kde2d(vowels$F1,vowels$F2,lims=c(range(vowels$F1),range(vowels$F2)))
iDensity2=as.data.frame(iDensity)
iDensity3=iDensity2[,-1:-2]
iDensity4=data.matrix(iDensity3, rownames.force=NA)
plot_ly(z=iDensity4) %>% add_surface()
```
Plot:

![Vowel Plot 6](https://github.com/zabub/Assignment-1/blob/main/Vowel%20Plot%206.html)







