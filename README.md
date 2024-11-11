java c
STATS 380
SEMESTER ONE 2024
STATISTICS
Statistical Computing

group,X17,X18,X19,X20,X21,X22
15-17,3.8,4 . 1,3 . 5,1 .4  e,1 . 1  e,1 . 0  e
18-24,20 . 2,19 . 9,16 . 2,11 .8,11 . 0,8 . 0
15-24,15 .3,14 . 9,12 .7,8 . 6,8 . 2,5 .8
25-34,22 .7,19,20 . 2,14 . 6,11 .4,10 . 1
35-44,17.3,19 . 9,14 . 1,12 .8,10 . 1,9 .8
45-54,16,16 . 2,17,13 . 0,11 .8,9 . 9
55-64,15,12 . 6,12 .8,12 . 5,12 .8,10 .7
65-74,7 . 6,7 . 9,7.3,6 . 2,6 .8,6 . 2
75+,2 . 2,4 . 1,3 . 9,2 . 6,3 .4,2 .4

Figure 1: A CSV ﬁle called "smoking-by-age . csv".
Figure 1 shows the contents of a CSV ﬁle called  "smoking-by-age . csv".The following code reads the CSV ﬁle into R and prints out the resulting data frame, smokingByAge.  This data frame. will be used in several of the questions in this exam.
>  smokingByAge  <-  read. csv("smoking-by-age. csv")
>  smokingByAgegroup    X17   X18   X19     X20     X21     X221  15-17    3.8   4 . 1    3 . 5  1 .4  e   1 . 1  e   1 . 0  e2  18-24  20 . 2   19 . 9  16 . 2     11 .8    11 . 0     8 . 03  15-24  15 .3  14 . 9  12 .7      8 . 6       8 . 2     5 .84  25-34  22 .7  19 . 0  20 . 2     14 . 6    11 .4    10 . 15  35-44  17.3  19 . 9  14 . 1     12 .8    10 . 1      9 .86  45-54   16 . 0  16 . 2  17 . 0    13 . 0     11 .8     9 . 97  55-64  15 . 0  12 . 6   12 .8    12 . 5     12 .8     10 .78  65-74    7 . 6    7 . 9    7.3       6 . 2     6 .8     6 . 29     75+    2 . 2   4 . 1    3 . 9       2 . 6       3 .4     2 .4
1.                                                                                                                     [10 marks]
Write down what the output of the following code would be.
(a)                                                                                                               [6 marks]
>  sapply(smokingByAge,  mode)(b)                                                                                                               [2 marks]
>  dim(smokingByAge)
(c)                                                                                                               [2 marks]
>  colnames(smokingByAge)
The data frames shown below will be used in some of the remaining questions in this exam.
> maoriSmoking
group  2017  2018  2019  2020  2021  2022
16  Total  Maori  33.4  33 .4  31 . 2  25 .7  22 .3  20 . 2
17      Maori  men  29 .7  31 .4  27.3  25 . 6  23 . 0  20 .4
18  Maori  women  36 .8  35 .4  35 . 0  25 .8  21 .7  20 . 2
> pacificSmoking
group  2017  2018  2019  2020  2021  2022
20  Total  Pacific  23 . 1  24.7  22 . 5  19 . 9  18.8  10 .3
21      Pacific  men  28 . 5  28 . 1  26 .8  20 .3  16 . 9  10 . 6
22  Pacific  women  18 . 1  21 .8   19 . 0  19 . 5  20 .4   10 . 1
>  asianSmoking
group  2017  2018  2019  2020  2021  2022
24  Total  Asian    7 . 9    8 . 5    8 . 9    5 .8    3.3    3.7
25      Asian men   12 .8  14 . 1  14 . 0    9 . 0   4.7    6 . 1
26  Asian  women     2 . 9    2 .3    2 . 5     1 . 5     1 .8    0 . 6
>  euroOtherSmoking
group  2017  2018  2019  2020  2021  2022
28  Total  European/Other  13 . 6  12 .7  11 .8    9 .4    9 . 2    7.7
29      European/Other  men   14 . 9  14 . 2  11 . 9  10 .3  10 . 5    8 . 5
30  European/Other  women  12 .3  11 . 2  11 .7    8 . 6     7 . 9    6 . 9
>  test1
group
1 not  this  row
2       Total  Row
>  test2
group
1 not  this  row
2    or  this  row
3       Total  Row
>  test3
group
1  Total  Row  One
2  Total  Row  Two
2.                                                                                                                    [10 marks]
(a)                                                                                                               [3 marks]
Write a function called findTotal().  The function should have a single argument, which is a data frame.  It should use grepl() to search the group column of the data frame. for values that contain the text  "Total".   The function should return a logical vector.
The findTotal() function should behave like this:
>  findTotal(maoriSmoking)
[1]   TRUE  FALSE  FALSE
>  findTotal(pacificSmoking)
[1]   TRUE  FALSE  FALSE
>  findTotal(test1)
[1]  FALSE   TRUE
>  findTotal(test2)
[1]  FALSE  FALSE   TRUE
>  findTotal(test3)
[1]  TRUE  TRUE
The values of the symbols maoriSmoking, pacificSmoking, test1, test2, and test3 can be found on page 3.
(b)                                                                                                               [7 marks]
Write  a  function called getTotal().   The function  should have a single argument, which is a data frame.  It should use findTotal() to search the group column of the data frame. for values that contains the word "Total" and then subset() to extract those rows from the data frame. and thengsub() to remove the word "Total" from the group column of those rows.  The function should return a data frame.
The getTotal() function should behave like this:
> getTotal(maoriSmoking)
group  2017  2018  2019  2020  2021  2022
16  Maori  33.4  33 .4  31 . 2  25 .7  22 .3  20 . 2
> getTotal(pacificSmoking)
group  2017  2018  2019  2020  2021  2022
20  Pacific  23 . 1  24.7  22 . 5  19 . 9  18.8  10 .3
> getTotal(test1)
group
2     Row
> getTotal(test2)
group
3     Row
> getTotal(test3)
group
1  Row  One
2  Row  Two
The values of the symbols maoriSmoking, pacificSmoking, test1, test2, and test3 can be found on page 3.
The following code creates a list called tables and prints out the list.  This list will be used in some of the remaining questions in this exam.
>  tables  <-  list(maoriSmoking,
+                           pacificSmoking,
+                              asianSmoking,
+                               euroOtherSmoking)
>  tables
[[1]]
group  2017  2018  2019  2020  2021  2022
16  Total  Maori  33.4  33 .4  31 . 2  25 .7  22 .3  20 . 2
17      Maori  men  29 .7  31 .4  27.3  25 . 6  23 . 0  20 .4
18  Maori  women  36 .8  35 .4  35 . 0  25 .8  21 .7  20 . 2
[[2]]
group  2017  2018  2019  2020  2021  2022
20  Total  Pacific  23 . 1  24.7  22 . 5  19 . 9  18.8  10 .3
21      Pacific  men  28 . 5  28 . 1  26 .8  20 .3  16 . 9  10 . 6
22  Pacific  women  18 . 1  21 .8   19 . 0  19 . 5  20 .4   10 . 1
[[3]]
group  2017  2018  2019  2020  2021  2022
24  Total  Asian    7 . 9    8 . 5    8 . 9    5 .8    3.3    3.7
25      Asian men   12 .8  14 . 1  14 . 0    9 . 0   4.7    6 . 1
26  Asian  women     2 . 9    2 .3    2 . 5     1 . 5     1 .8    0 . 6
[[4]]
group  2017  2018  2019  2020  2021  2022
28  Total  European/Other  13 . 6  12 .7  11 .8    9 .4    9 . 2    7.7
29      European/Other  men   14 . 9  14 . 2  11 . 9  10 .3  10 . 5    8 . 5
30  European/Other  women  12 .3  11 . 2  11 .7    8 . 6     7 . 9    6 . 9
3.                   代 写STATS 380 Statistical Computing SEMESTER ONE 2024Python
代做程序编程语言                                                                                                 [10 marks](a)                                                                                                               [2 marks]Write  R  code that uses the list tables  (from page 6) and the functions lapply() and getTotal() (from page 5) to create a list of data frames that just contain "Total" rows and assign the result to the symbol totalTables.
The list totalTables should look like this:
>  totalTables
[[1]]
group  2017  2018  2019  2020  2021  2022
16  Maori  33.4  33 .4  31 . 2  25 .7  22 .3  20 . 2
[[2]]
group  2017  2018  2019  2020  2021  2022
20  Pacific  23 . 1  24.7  22 . 5  19 . 9  18.8  10 .3
[[3]]
group  2017  2018  2019  2020  2021  2022
24  Asian    7 . 9    8 . 5    8 . 9    5 .8    3.3    3.7
[[4]]
group  2017  2018  2019  2020  2021  2022
28  European/Other  13 . 6  12 .7  11 .8    9 .4    9 . 2    7.7
(b)                                                                                                               [3 marks] 
Write  R  code  that  uses the  functions  do. call()  and  rbind() to  com- bine the list of data frames,  totalTables, into a single data frame. called ethnicSmoking.
The data frame. ethnicSmoking should look like this:
>  ethnicSmoking
group  2017  2018  2019  2020  2021  2022
16                    Maori  33.4  33 .4  31 . 2  25 .7  22 .3  20 . 2
20               Pacific  23 . 1  24.7  22 . 5  19 . 9  18.8  10 .3
24                    Asian    7 . 9    8 . 5    8 . 9    5 .8    3.3    3.7
28  European/Other  13 . 6  12 .7  11 .8    9 .4    9 . 2    7.7
(c)                                                                                                               [5 marks] 
Write down what the output of the following code would be.
> groups  <-  split(ethnicSmoking[1:2,  ],  ethnicSmoking$group[1:2]) 
> groups
>  ranges  <-  lapply(groups,  function(df)  range(df[-1])) 
>  ranges
>  do. call(rbind,  ranges)
The following code creates a plot (Figure 2) that shows the prevalence of smoking overtime for diﬀerent ethnic groups.
The code makes use of the data in the ethnicSmoking data frame. (from page 7). The code and plot will be used in some of the remaining questions in this exam.
> par(mar=margins) > plot. new()
> plot. window(xlim, ylim) >  axis(1,  at=years)
>  axis(right) >  box()
>  for  (i  in  1:numGroups)  {
+         y  <-  ethnicSmoking[i,  -1]
+        lines(years, y)
+        points(years,  y, pch=pch) +  }
> mtext(ethnicSmoking$group,  side=left,  at=ethnicSmoking$"2017", 
+           adj=adj,  line=.5,  las=horizontal)
Figure 2:  A plot of smoking prevalence for diﬀerent ethnic groups.   The grey border around the outside is not drawn by R; it is just there to show the extent of the “page” that R is drawing on.
4.                                                                                                                   [10 marks]
The code shown on page 8 makes use of some symbols that have not yet been assigned a value.
Write R code that assigns values to each of the following symbols:
(i) margins
(ii) xlim
(iii) ylim
(iv) years
(v) right
(vi) numGroups
(vii) pch
(viii)  left
(ix)  adj
(x) horizontal
HINTS:
• The left margin of the plot has been made wider to leave room for the ethnic group labels.
• The y-axis range is calculated from the data for all ethnic groups.
•  The data symbols are ﬁlled circles.
• The ethnic group labels are right-aligned.
• The help page for themtext() function shown in Appendix B may be helpful.The following code deﬁnes a function called middle() that will be used in some of the remaining questions in this exam.  Line numbers are provided in grey so that you can refer to speciﬁclines in your answers if necessary.The purpose of this function is to calculate a “middle” value for each age range in the group column of the smokingByAge data frame. (from page 2).  For each row of the group column, if the value contains a dash, the function splits the value into pieces either side of the dash, converts those pieces into numbers, and averages the numbers.  If the value does not contain a dash, the function searches for and removes any plus signs, converts what remains into a number and then calulates the average of that number and 100.
1   middle  <-  function()  {
2          n  <-  nrow(smokingByAge)
3          column  <-  smokingByAge[["group"]]
4          middle  <-  rep(NA, n)
5          for  (i  in  1:n)  {
6                  range  <-  column[i]
7                  if  (grepl("-",  range))  {
8                          bounds  <-  strsplit(range,  "-")[[1]]
9                          boundsNum  <-  as. numeric(bounds)
10                         middle[i]  <-  mean(boundsNum)
11                 }  else  {
12                        lower  <-  gsub("+",  "",  range,  fixed=TRUE)
13                         lowerNum  <-  as. numeric(lower)
14                        middle[i]  <-  mean(c(lowerNum,  100))
15                  }
16           }
17          middle
18   }
The following code and output shows that the middle() function returns a numeric vector of “middle” values.
> middle()
[1]  16 . 0  21 . 0   19 . 5  29 . 5  39 . 5  49 . 5  59 . 5  69 . 5  87 . 5
5.                                                                                                                    [10 marks] 
Identify all constant values in the middle() function code (from page 10) and, for each constant, describe what the constant represents.
Describe any overall assumptions that the function is making.
6.                                                                                                                    [10 marks] 
Identify all local and global symbols (excluding functions) in the middle() function code (from page 10) and, for each symbol, describe the mode of the R object that is assigned to the symbol.
The data frame. shown below, vapingByAge, will be used in some of the remaining questions in this exam.
vapingByAge
group      X17     X18     X19     X20     X21     X22
1  15-17  0 . 6  e  1 .7  e  2 .3  e  5 .8  e  8.3  e  15 .4   
2  18-24    4 . 1     4.4       5 . 0    15 .3    23 . 0     25 . 2   
3  15-24    3 . 0     3 . 6     4.3    12 .4    18.8    22 . 1   
4  25-34   4 . 1       5 . 2      5 . 9       9 .8    10 . 9    14.8   
5  35-44    3 . 2     5 . 0     4 . 6       5 .8    10 .3    10 .7   
6  45-54    2 .4     3 . 2     3.3     6 . 5     5 .7     6 .3   
7  55-64    2 . 5       2 . 2       2 . 1       2 . 6       5 . 2       4 . 2   
8  65-74     1 . 1       1 . 0      1 . 5      1 . 0      1 .7       2 . 5   
9     75+           S  0 . 2  e           S  0 .4  e  0 .8  e  0 .7  e



         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
