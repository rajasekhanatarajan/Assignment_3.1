# Assignment_3.1
How many vowels are there in the names of USA States?
View(USArrests)

names(USArrests) #to get the column names

US_States<-rownames(USArrests) # to get the row names, i.e the USA states

US_States

b<-gsub("[^aeiouAEIOU]","C",US_States)#is basically "if not any of 'aeiouAEIOU' then 'C'

#if aeiouAEIOU is NOT in [], its a complete pattern.

using ^ means, exclude what comes after this
b<-gsub("[^C]","V",b)# is "if not 'C', then 'V'

b

library(stringr)

str_count(b,"V") #counts character in a string

sum(str_count(b,"V")) # adds the count of "V" i.e vowels

177 Vowels
Visualize the vowels distribution.
USArrests # data set

names(USArrests) # to know the column names for State names

USA_States <- rownames(USArrests) # names of states

USA_States <- paste(USA_States, collapse = "") # converting the names to a string

USA_States

USA_States <- tolower(strsplit(USA_States, "")[[1]]) # converting to lower case and spliting each letter

USA_States

USA_States <- USA_States[USA_States %in% letters]

table(USA_States) # Frequency of each letter

distribution <- as.data.frame(table(USA_States)) # converted to data frame

names(distribution)

colnames(distribution) <- c("letters", "Freq") # changed column names

names(distribution)

library(dplyr)

filter(distribution, letters %in% c("a","e","i","o","u")) # finding number of vowels in the names of USA States

thus there are 61 a, 28 e , 44 i , 36 o and 8 u in the names of USA States
type 1
vowel_dist <- filter(distribution, letters %in% c("a","e","i","o","u"))

vowel_dist

barplot(vowel_dist$Freq, axes = TRUE, axisnames = TRUE, xlab = "Vowels", ylab = "frequency")

type 2
since we want vowel distribution, assiging colour to position of vowel
area.color <- c("withcolour",NA,NA,NA,"withcolour",NA,NA,NA,"withcolour",

            NA,NA,NA,NA,NA,"withcolour",NA,NA,NA,NA,"withcolour",



            NA,NA,NA,NA,NA)
area.color

library(ggplot2)

plot.vowel <- ggplot(data = distribution, aes(x=letters, y=Freq, fill=area.color))+

geom_bar(stat = "identity") +

xlab(colnames(distribution)[1]) +

ylab(colnames(distribution)[2])

plot.vowel # vowel distribution is visualized with different colour
