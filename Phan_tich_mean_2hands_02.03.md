---
title: "Phan tich mean hand Wilcox test"
author: "Minh"
date: "2024-03-25"
output:
  html_document:
    keep_md: yes
  pdf_document: default
  word_document: default
params:
  warning: no
---




## Load bộ số liệu và các packages


```
## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
## ✔ dplyr     1.1.3     ✔ readr     2.1.4
## ✔ forcats   1.0.0     ✔ stringr   1.5.0
## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
## ✔ purrr     1.0.2     
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
## 
## Attaching package: 'rstatix'
## 
## 
## The following object is masked from 'package:stats':
## 
##     filter
```

## So sánh khác biệt về trung bình của chỉ số 2 tay theo các subgroup


Tạo hàm tính 95%CI



Tạo hàm so sánh trung bình bằng Wilcox.test nếu subgroup có 2 level


Tạo hàm so sánh bắt cặp các trung bình bằng Wilcox.pairwise test nếu group có >2 level




Tạo hàm vẽ Forest plot




Hàm để tạo bảng 




Sub group list = "Gender", "Race", "Smoking", "Obesity", "BMI_25_30", "Stress index", "Type of skins", "Hypertension", "Age_stage", 




## Tạo bảng và Forest plot với biến M_mean

|   |Subgroup_Category |Subgroup                  | n_M_mean|     Mean|   CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|--------:|--------:|----------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |       33| 25.23066|  22.951082|  27.51024|        NA|
|5  |Age_stage         |Age [40-50)               |       14| 23.81860|  18.427889|  29.20930|        NA|
|4  |Age_stage         |Age <30                   |       26| 19.41503|  15.093954|  23.73611|        NA|
|6  |Age_stage         |Age >=50                  |        6| 18.30167|   7.117392|  29.48594|        NA|
|30 |Anxiety           |0                         |       63| 21.38829|  19.064357|  23.71221|        NA|
|33 |Anxiety           |1                         |        5| 26.12000|  11.211142|  41.02886|        NA|
|31 |Anxiety           |2                         |        5| 26.16750|  21.697559|  30.63744|        NA|
|34 |Anxiety           |3                         |        2| 30.94875| -14.809470|  76.70697|        NA|
|32 |Anxiety           |4                         |        4| 27.46898|  17.290166|  37.64780|        NA|
|38 |BMI_25_30         |BMI [25-30)               |       28| 26.35789|  23.125619|  29.59016|        NA|
|37 |BMI_25_30         |BMI <25                   |       43| 19.34076|  16.496402|  22.18513|        NA|
|39 |BMI_25_30         |BMI >=30                  |        8| 26.37490|  23.570361|  29.17943|        NA|
|21 |DASS_21           |ANXIETY                   |        3| 29.20167|  24.635204|  33.76813|        NA|
|25 |DASS_21           |DEPRESSION                |        2| 19.81792| -98.185666| 137.82150|        NA|
|20 |DASS_21           |NORMAL                    |       57| 21.01634|  18.547665|  23.48501|        NA|
|22 |DASS_21           |STRESS                    |        4| 27.47375|  18.372354|  36.57515|        NA|
|24 |DASS_21           |STRESS ANXIETY            |        4| 29.70000|  22.871814|  36.52819|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |        9| 25.20066|  18.104595|  32.29672|        NA|
|1  |Gender            |female                    |       34| 21.35809|  18.402465|  24.31372| 0.1878680|
|2  |Gender            |male                      |       45| 23.43329|  20.548402|  26.31817| 0.1878680|
|35 |Hypertension      |No                        |       58| 23.59258|  21.312831|  25.87233| 0.1866318|
|36 |Hypertension      |Yes                       |       21| 19.63349|  15.102313|  24.16467| 0.1866318|
|40 |Obesity           |No                        |       71| 22.10808|  19.862808|  24.35335| 0.2726702|
|41 |Obesity           |Yes                       |        8| 26.37490|  23.570361|  29.17943| 0.2726702|
|7  |Race              |Asian or Asian British    |       61| 21.07010|  18.630418|  23.50979|        NA|
|9  |Race              |Black                     |        3| 29.87167|  15.850781|  43.89255|        NA|
|8  |Race              |White                     |       15| 27.05211|  24.085581|  30.01864|        NA|
|18 |Smoking           |Non smoker                |       65| 22.84827|  20.670031|  25.02651| 0.9130984|
|19 |Smoking           |Smoker                    |       14| 21.10967|  14.850255|  27.36908| 0.9130984|
|26 |Stress            |0                         |       62| 21.37374|  19.023904|  23.72358|        NA|
|27 |Stress            |1                         |       10| 24.95975|  19.119608|  30.79989|        NA|
|28 |Stress            |2                         |        3| 30.04781|  10.255354|  49.84027|        NA|
|29 |Stress            |3                         |        4| 28.94000|  20.569958|  37.31004|        NA|
|16 |Stress index      |No                        |       57| 21.01634|  18.547665|  23.48501| 0.0161211|
|17 |Stress index      |Yes                       |       22| 26.48826|  23.156869|  29.81966| 0.0161211|
|12 |Typer of skins    |1                         |       13| 25.20237|  22.799807|  27.60494|        NA|
|14 |Typer of skins    |2                         |        5| 31.27200|  25.257861|  37.28614|        NA|
|10 |Typer of skins    |3                         |       40| 19.60355|  16.435905|  22.77119|        NA|
|11 |Typer of skins    |4                         |       11| 26.43410|  23.779655|  29.08854|        NA|
|15 |Typer of skins    |5                         |        6| 17.04917|   3.788464|  30.30987|        NA|
|13 |Typer of skins    |6                         |        4| 29.86750|  22.534428|  37.20057|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.0831089|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.6839356|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.2201242|
|Age_stage      |Age <30                   |Age [40-50)               | 0.1690260|
|Age_stage      |Age <30                   |Age >=50                  | 0.9807390|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.3530444|
|Race           |Asian or Asian British    |White                     | 0.0318033|
|Race           |Asian or Asian British    |Black                     | 0.1122592|
|Race           |White                     |Black                     | 0.3602941|
|Typer of skins |3                         |4                         | 0.0426806|
|Typer of skins |3                         |1                         | 0.0754198|
|Typer of skins |3                         |6                         | 0.0392338|
|Typer of skins |3                         |2                         | 0.0088323|
|Typer of skins |3                         |5                         | 0.5681321|
|Typer of skins |4                         |1                         | 0.5690834|
|Typer of skins |4                         |6                         | 0.2256410|
|Typer of skins |4                         |2                         | 0.1451465|
|Typer of skins |4                         |5                         | 0.1801875|
|Typer of skins |1                         |6                         | 0.0445378|
|Typer of skins |1                         |2                         | 0.0592904|
|Typer of skins |1                         |5                         | 0.2440660|
|Typer of skins |6                         |2                         | 1.0000000|
|Typer of skins |6                         |5                         | 0.1714286|
|Typer of skins |2                         |5                         | 0.0519481|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.0575089|
|DASS_21        |NORMAL                    |STRESS                    | 0.1849399|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.4163229|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.0428708|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.8834470|
|DASS_21        |ANXIETY                   |STRESS                    | 0.6285714|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.3727273|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.8571429|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.4000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.9398601|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.6857143|
|DASS_21        |STRESS                    |DEPRESSION                | 0.5333333|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.3300699|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.7272727|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.5333333|
|Stress         |0                         |1                         | 0.3881316|
|Stress         |0                         |2                         | 0.1459876|
|Stress         |0                         |3                         | 0.1159210|
|Stress         |1                         |2                         | 0.3706294|
|Stress         |1                         |3                         | 0.4535465|
|Stress         |2                         |3                         | 1.0000000|
|Anxiety        |0                         |2                         | 0.3656517|
|Anxiety        |0                         |4                         | 0.2958884|
|Anxiety        |0                         |1                         | 0.1656458|
|Anxiety        |0                         |3                         | 0.1239302|
|Anxiety        |2                         |4                         | 0.9047619|
|Anxiety        |2                         |1                         | 0.5476190|
|Anxiety        |2                         |3                         | 0.3809524|
|Anxiety        |4                         |1                         | 0.7301587|
|Anxiety        |4                         |3                         | 0.8000000|
|Anxiety        |1                         |3                         | 0.8571429|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.0013452|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.0370609|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.6407065|






## Tạo bảng và Forest plot với biến Kv100_mean

|   |Subgroup_Category |Subgroup                  | n_Kv100_mean|     Mean|     CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|------------:|--------:|------------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |           33| 19.90264|   16.2535011|  23.55179|        NA|
|5  |Age_stage         |Age [40-50)               |           14| 12.29769|    9.6605674|  14.93481|        NA|
|4  |Age_stage         |Age <30                   |           26| 25.59429|   20.5850815|  30.60351|        NA|
|6  |Age_stage         |Age >=50                  |            6| 28.58972|   10.7716272|  46.40782|        NA|
|30 |Anxiety           |0                         |           63| 21.50424|   18.4752960|  24.53317|        NA|
|33 |Anxiety           |1                         |            5| 20.54500|    0.7191585|  40.37084|        NA|
|31 |Anxiety           |2                         |            5| 14.05425|    4.7711805|  23.33732|        NA|
|34 |Anxiety           |3                         |            2| 22.68375|   -7.0328863|  52.40039|        NA|
|32 |Anxiety           |4                         |            4| 23.20359|    4.0320452|  42.37513|        NA|
|38 |BMI_25_30         |BMI [25-30)               |           28| 17.55254|   13.0120452|  22.09303|        NA|
|37 |BMI_25_30         |BMI <25                   |           43| 24.03088|   20.3173592|  27.74439|        NA|
|39 |BMI_25_30         |BMI >=30                  |            8| 17.64328|   12.1152123|  23.17135|        NA|
|21 |DASS_21           |ANXIETY                   |            3|  9.03000|    5.0253535|  13.03465|        NA|
|25 |DASS_21           |DEPRESSION                |            2| 34.64958| -153.3969525| 222.69612|        NA|
|20 |DASS_21           |NORMAL                    |           57| 21.12303|   17.9396406|  24.30642|        NA|
|22 |DASS_21           |STRESS                    |            4| 20.36375|   10.7198844|  30.00762|        NA|
|24 |DASS_21           |STRESS ANXIETY            |            4| 15.06875|    3.7723350|  26.36517|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |            9| 24.86812|   15.8730042|  33.86324|        NA|
|1  |Gender            |female                    |           34| 24.24387|   19.4504079|  29.03732| 0.0603411|
|2  |Gender            |male                      |           45| 18.70341|   15.7969971|  21.60983| 0.0603411|
|35 |Hypertension      |No                        |           58| 22.49433|   19.2461585|  25.74250| 0.0662656|
|36 |Hypertension      |Yes                       |           21| 17.20351|   12.8726545|  21.53437| 0.0662656|
|40 |Obesity           |No                        |           71| 21.47604|   18.5731174|  24.37896| 0.5750373|
|41 |Obesity           |Yes                       |            8| 17.64328|   12.1152123|  23.17135| 0.5750373|
|7  |Race              |Asian or Asian British    |           61| 21.42018|   18.2961183|  24.54423|        NA|
|9  |Race              |Black                     |            3| 16.23667|   -0.1541548|  32.62749|        NA|
|8  |Race              |White                     |           15| 20.70694|   14.3469523|  27.06694|        NA|
|18 |Smoking           |Non smoker                |           65| 22.52134|   19.4428233|  25.59986| 0.0204816|
|19 |Smoking           |Smoker                    |           14| 14.43269|   11.6212868|  17.24409| 0.0204816|
|26 |Stress            |0                         |           62| 20.97422|   17.8373330|  24.11111|        NA|
|27 |Stress            |1                         |           10| 22.36413|   14.8995888|  29.82866|        NA|
|28 |Stress            |2                         |            3| 19.17229|  -16.7610866|  55.10566|        NA|
|29 |Stress            |3                         |            4| 21.09625|    7.8839503|  34.30855|        NA|
|16 |Stress index      |No                        |           57| 21.12303|   17.9396406|  24.30642| 0.8999099|
|17 |Stress index      |Yes                       |           22| 20.99692|   15.8049653|  26.18888| 0.8999099|
|12 |Typer of skins    |1                         |           13| 21.35593|   13.9659494|  28.74591|        NA|
|14 |Typer of skins    |2                         |            5| 14.63700|    7.0226726|  22.25133|        NA|
|10 |Typer of skins    |3                         |           40| 21.12525|   16.9820641|  25.26844|        NA|
|11 |Typer of skins    |4                         |           11| 20.89093|   15.3323434|  26.44951|        NA|
|15 |Typer of skins    |5                         |            6| 30.68708|   18.6235994|  42.75057|        NA|
|13 |Typer of skins    |6                         |            4| 14.05000|    3.0084534|  25.09155|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.0569137|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.0061696|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.3493784|
|Age_stage      |Age <30                   |Age [40-50)               | 0.0001552|
|Age_stage      |Age <30                   |Age >=50                  | 0.7241534|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.0256450|
|Race           |Asian or Asian British    |White                     | 0.9687691|
|Race           |Asian or Asian British    |Black                     | 0.5675139|
|Race           |White                     |Black                     | 0.6544118|
|Typer of skins |3                         |4                         | 0.6926749|
|Typer of skins |3                         |1                         | 0.7361419|
|Typer of skins |3                         |6                         | 0.3108780|
|Typer of skins |3                         |2                         | 0.4490526|
|Typer of skins |3                         |5                         | 0.0695713|
|Typer of skins |4                         |1                         | 0.7329601|
|Typer of skins |4                         |6                         | 0.1377289|
|Typer of skins |4                         |2                         | 0.1149267|
|Typer of skins |4                         |5                         | 0.0982547|
|Typer of skins |1                         |6                         | 0.2016807|
|Typer of skins |1                         |2                         | 0.3359010|
|Typer of skins |1                         |5                         | 0.1273773|
|Typer of skins |6                         |2                         | 1.0000000|
|Typer of skins |6                         |5                         | 0.1142857|
|Typer of skins |2                         |5                         | 0.0822511|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.0326125|
|DASS_21        |NORMAL                    |STRESS                    | 0.7375783|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.2622437|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.4229955|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.2014242|
|DASS_21        |ANXIETY                   |STRESS                    | 0.0571429|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.0636364|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.4000000|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.2000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.6041958|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.2000000|
|DASS_21        |STRESS                    |DEPRESSION                | 0.8000000|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.1986014|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.5818182|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.5333333|
|Stress         |0                         |1                         | 0.4109122|
|Stress         |0                         |2                         | 0.7191832|
|Stress         |0                         |3                         | 0.6190739|
|Stress         |1                         |2                         | 0.5734266|
|Stress         |1                         |3                         | 0.9450549|
|Stress         |2                         |3                         | 0.8571429|
|Anxiety        |0                         |2                         | 0.1656499|
|Anxiety        |0                         |4                         | 0.6432933|
|Anxiety        |0                         |1                         | 0.6383991|
|Anxiety        |0                         |3                         | 0.5559979|
|Anxiety        |2                         |4                         | 0.4126984|
|Anxiety        |2                         |1                         | 0.5476190|
|Anxiety        |2                         |3                         | 0.1904762|
|Anxiety        |4                         |1                         | 0.9047619|
|Anxiety        |4                         |3                         | 0.8000000|
|Anxiety        |1                         |3                         | 0.5714286|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.0088580|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.1773118|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.5129149|


## Tạo bảng và Forest plot với biến δ_mean

|   |Subgroup_Category |Subgroup                  | n_δ_mean|     Mean|   CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|--------:|--------:|----------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |       33| 4.463261|  3.8386680|  5.087854|        NA|
|5  |Age_stage         |Age [40-50)               |       14| 2.806345|  1.9337929|  3.678898|        NA|
|4  |Age_stage         |Age <30                   |       26| 3.871474|  3.1760600|  4.566889|        NA|
|6  |Age_stage         |Age >=50                  |        6| 4.250000|  1.6980608|  6.801939|        NA|
|30 |Anxiety           |0                         |       63| 3.793460|  3.3486210|  4.238300|        NA|
|33 |Anxiety           |1                         |        5| 3.951000|  2.2495159|  5.652484|        NA|
|31 |Anxiety           |2                         |        5| 3.441500|  1.7572771|  5.125723|        NA|
|34 |Anxiety           |3                         |        2| 7.001250| -5.0537617| 19.056262|        NA|
|32 |Anxiety           |4                         |        4| 5.695446|  1.9509554|  9.439937|        NA|
|38 |BMI_25_30         |BMI [25-30)               |       28| 3.869468|  3.1982181|  4.540719|        NA|
|37 |BMI_25_30         |BMI <25                   |       43| 3.959798|  3.3482640|  4.571333|        NA|
|39 |BMI_25_30         |BMI >=30                  |        8| 4.264792|  3.1417748|  5.387809|        NA|
|21 |DASS_21           |ANXIETY                   |        3| 2.641667|  1.8980487|  3.385285|        NA|
|25 |DASS_21           |DEPRESSION                |        2| 5.326667| -0.5605415| 11.213875|        NA|
|20 |DASS_21           |NORMAL                    |       57| 3.636880|  3.1688049|  4.104955|        NA|
|22 |DASS_21           |STRESS                    |        4| 5.258125|  3.4094523|  7.106798|        NA|
|24 |DASS_21           |STRESS ANXIETY            |        4| 4.656250|  0.6284675|  8.684033|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |        9| 5.244087|  3.9188290|  6.569346|        NA|
|1  |Gender            |female                    |       34| 4.159636|  3.5364417|  4.782830| 0.3363251|
|2  |Gender            |male                      |       45| 3.806826|  3.2472029|  4.366449| 0.3363251|
|35 |Hypertension      |No                        |       58| 4.408200|  3.9375013|  4.878899| 0.0001260|
|36 |Hypertension      |Yes                       |       21| 2.717103|  2.1271620|  3.307044| 0.0001260|
|40 |Obesity           |No                        |       71| 3.924175|  3.4796557|  4.368695| 0.5000551|
|41 |Obesity           |Yes                       |        8| 4.264792|  3.1417748|  5.387809| 0.5000551|
|7  |Race              |Asian or Asian British    |       61| 3.647510|  3.1975694|  4.097451|        NA|
|9  |Race              |Black                     |        3| 4.826667| -1.0839935| 10.737327|        NA|
|8  |Race              |White                     |       15| 5.050444|  4.1404921|  5.960397|        NA|
|18 |Smoking           |Non smoker                |       65| 4.175707|  3.7457232|  4.605691| 0.0191251|
|19 |Smoking           |Smoker                    |       14| 2.950988|  1.8146314|  4.087345| 0.0191251|
|26 |Stress            |0                         |       62| 3.643234|  3.2027025|  4.083765|        NA|
|27 |Stress            |1                         |       10| 4.875000|  3.7674266|  5.982573|        NA|
|28 |Stress            |2                         |        3| 4.848095| -0.9906251| 10.686815|        NA|
|29 |Stress            |3                         |        4| 5.890000|  2.6668123|  9.113188|        NA|
|16 |Stress index      |No                        |       57| 3.636880|  3.1688049|  4.104955| 0.0072524|
|17 |Stress index      |Yes                       |       22| 4.792392|  4.0130370|  5.571747| 0.0072524|
|12 |Typer of skins    |1                         |       13| 4.759551|  3.8298493|  5.689253|        NA|
|14 |Typer of skins    |2                         |        5| 5.104000|  2.5187159|  7.689284|        NA|
|10 |Typer of skins    |3                         |       40| 3.212929|  2.7428353|  3.683023|        NA|
|11 |Typer of skins    |4                         |       11| 4.953723|  3.8702715|  6.037174|        NA|
|15 |Typer of skins    |5                         |        6| 4.272917|  1.3387716|  7.207062|        NA|
|13 |Typer of skins    |6                         |        4| 4.173750|  0.4489826|  7.898517|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.1682932|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.0023116|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.9244782|
|Age_stage      |Age <30                   |Age [40-50)               | 0.0586959|
|Age_stage      |Age <30                   |Age >=50                  | 0.8323953|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.1528380|
|Race           |Asian or Asian British    |White                     | 0.0046257|
|Race           |Asian or Asian British    |Black                     | 0.3248092|
|Race           |White                     |Black                     | 0.7377451|
|Typer of skins |3                         |4                         | 0.0036236|
|Typer of skins |3                         |1                         | 0.0026630|
|Typer of skins |3                         |6                         | 0.5410936|
|Typer of skins |3                         |2                         | 0.0348596|
|Typer of skins |3                         |5                         | 0.5342012|
|Typer of skins |4                         |1                         | 0.8646168|
|Typer of skins |4                         |6                         | 0.4893773|
|Typer of skins |4                         |2                         | 0.9130037|
|Typer of skins |4                         |5                         | 0.3501939|
|Typer of skins |1                         |6                         | 0.4773109|
|Typer of skins |1                         |2                         | 0.7028478|
|Typer of skins |1                         |5                         | 0.2440660|
|Typer of skins |6                         |2                         | 0.5555556|
|Typer of skins |6                         |5                         | 0.9142857|
|Typer of skins |2                         |5                         | 0.3290043|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.4353265|
|DASS_21        |NORMAL                    |STRESS                    | 0.0492215|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.0136468|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.3587348|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.1263099|
|DASS_21        |ANXIETY                   |STRESS                    | 0.0571429|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.0636364|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.4000000|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.2000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.8251748|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.8857143|
|DASS_21        |STRESS                    |DEPRESSION                | 1.0000000|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.7104895|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.9090909|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.8000000|
|Stress         |0                         |1                         | 0.0251620|
|Stress         |0                         |2                         | 0.3246948|
|Stress         |0                         |3                         | 0.0285093|
|Stress         |1                         |2                         | 0.9370629|
|Stress         |1                         |3                         | 0.3036963|
|Stress         |2                         |3                         | 0.6285714|
|Anxiety        |0                         |2                         | 0.7779719|
|Anxiety        |0                         |4                         | 0.0878498|
|Anxiety        |0                         |1                         | 0.5569198|
|Anxiety        |0                         |3                         | 0.0384258|
|Anxiety        |2                         |4                         | 0.2857143|
|Anxiety        |2                         |1                         | 0.4206349|
|Anxiety        |2                         |3                         | 0.0952381|
|Anxiety        |4                         |1                         | 0.2857143|
|Anxiety        |4                         |3                         | 0.8000000|
|Anxiety        |1                         |3                         | 0.0952381|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.7656678|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.6748524|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.3583145|


## Tạo bảng và Forest plot với biến T_mean

|   |Subgroup_Category |Subgroup                  | n_T_mean|     Mean| CI_lower| CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|--------:|--------:|--------:|--------:|---------:|
|3  |Age_stage         |Age [30-40)               |       33| 32.21173| 31.27879| 33.14468|        NA|
|5  |Age_stage         |Age [40-50)               |       14| 31.66737| 28.90384| 34.43090|        NA|
|4  |Age_stage         |Age <30                   |       26| 30.52529| 29.00575| 32.04483|        NA|
|6  |Age_stage         |Age >=50                  |        6| 29.58194| 24.20772| 34.95617|        NA|
|30 |Anxiety           |0                         |       63| 30.82449| 29.85284| 31.79615|        NA|
|33 |Anxiety           |1                         |        5| 32.84000| 29.76532| 35.91468|        NA|
|31 |Anxiety           |2                         |        5| 34.39875| 32.88407| 35.91343|        NA|
|34 |Anxiety           |3                         |        2| 32.89375| 12.61147| 53.17603|        NA|
|32 |Anxiety           |4                         |        4| 33.38879| 30.22786| 36.54971|        NA|
|38 |BMI_25_30         |BMI [25-30)               |       28| 32.39200| 31.14919| 33.63481|        NA|
|37 |BMI_25_30         |BMI <25                   |       43| 30.26352| 29.05781| 31.46923|        NA|
|39 |BMI_25_30         |BMI >=30                  |        8| 33.64651| 32.18871| 35.10431|        NA|
|21 |DASS_21           |ANXIETY                   |        3| 34.41333| 30.61487| 38.21180|        NA|
|25 |DASS_21           |DEPRESSION                |        2| 33.01000| 10.26589| 55.75411|        NA|
|20 |DASS_21           |NORMAL                    |       57| 30.64620| 29.58548| 31.70691|        NA|
|22 |DASS_21           |STRESS                    |        4| 32.27250| 31.04694| 33.49806|        NA|
|24 |DASS_21           |STRESS ANXIETY            |        4| 34.19125| 31.58687| 36.79563|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |        9| 32.83682| 31.26785| 34.40580|        NA|
|1  |Gender            |female                    |       34| 31.74163| 30.66615| 32.81712| 1.0000000|
|2  |Gender            |male                      |       45| 31.07253| 29.83676| 32.30830| 1.0000000|
|35 |Hypertension      |No                        |       58| 31.79208| 30.95194| 32.63223| 0.3716739|
|36 |Hypertension      |Yes                       |       21| 30.16851| 28.02364| 32.31339| 0.3716739|
|40 |Obesity           |No                        |       71| 31.10292| 30.20881| 31.99703| 0.0699938|
|41 |Obesity           |Yes                       |        8| 33.64651| 32.18871| 35.10431| 0.0699938|
|7  |Race              |Asian or Asian British    |       61| 30.78218| 29.78500| 31.77935|        NA|
|9  |Race              |Black                     |        3| 34.38167| 31.53377| 37.22956|        NA|
|8  |Race              |White                     |       15| 33.10811| 31.95357| 34.26266|        NA|
|18 |Smoking           |Non smoker                |       65| 31.66356| 30.85425| 32.47287| 0.4526101|
|19 |Smoking           |Smoker                    |       14| 29.95344| 26.95657| 32.95031| 0.4526101|
|26 |Stress            |0                         |       62| 30.90473| 29.89958| 31.90988|        NA|
|27 |Stress            |1                         |       10| 32.84338| 31.50169| 34.18506|        NA|
|28 |Stress            |2                         |        3| 33.91838| 29.90444| 37.93232|        NA|
|29 |Stress            |3                         |        4| 32.79937| 29.70267| 35.89608|        NA|
|16 |Stress index      |No                        |       57| 30.64620| 29.58548| 31.70691| 0.0184274|
|17 |Stress index      |Yes                       |       22| 33.21120| 32.41762| 34.00478| 0.0184274|
|12 |Typer of skins    |1                         |       13| 33.02080| 31.68484| 34.35676|        NA|
|14 |Typer of skins    |2                         |        5| 33.48900| 30.21092| 36.76708|        NA|
|10 |Typer of skins    |3                         |       40| 30.20477| 28.91238| 31.49716|        NA|
|11 |Typer of skins    |4                         |       11| 33.15895| 32.25833| 34.05957|        NA|
|15 |Typer of skins    |5                         |        6| 28.15083| 24.32469| 31.97698|        NA|
|13 |Typer of skins    |6                         |        4| 34.73000| 32.87327| 36.58673|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.0726536|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.3874213|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.3493784|
|Age_stage      |Age <30                   |Age [40-50)               | 0.1538800|
|Age_stage      |Age <30                   |Age >=50                  | 0.6546560|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.6015480|
|Race           |Asian or Asian British    |White                     | 0.0283418|
|Race           |Asian or Asian British    |Black                     | 0.0566862|
|Race           |White                     |Black                     | 0.3014706|
|Typer of skins |3                         |4                         | 0.0391518|
|Typer of skins |3                         |1                         | 0.0187088|
|Typer of skins |3                         |6                         | 0.0052891|
|Typer of skins |3                         |2                         | 0.0614999|
|Typer of skins |3                         |5                         | 0.2031633|
|Typer of skins |4                         |1                         | 0.8201386|
|Typer of skins |4                         |6                         | 0.0776557|
|Typer of skins |4                         |2                         | 0.5833333|
|Typer of skins |4                         |5                         | 0.0030705|
|Typer of skins |1                         |6                         | 0.1302521|
|Typer of skins |1                         |2                         | 0.6330532|
|Typer of skins |1                         |5                         | 0.0047177|
|Typer of skins |6                         |2                         | 0.7301587|
|Typer of skins |6                         |5                         | 0.0095238|
|Typer of skins |2                         |5                         | 0.0303030|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.0722336|
|DASS_21        |NORMAL                    |STRESS                    | 0.8497927|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.1725646|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.0602089|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.4894971|
|DASS_21        |ANXIETY                   |STRESS                    | 0.1142857|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.4818182|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.8571429|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.4000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.6041958|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.2000000|
|DASS_21        |STRESS                    |DEPRESSION                | 1.0000000|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.2601399|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 1.0000000|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.8000000|
|Stress         |0                         |1                         | 0.2788897|
|Stress         |0                         |2                         | 0.1738175|
|Stress         |0                         |3                         | 0.5102776|
|Stress         |1                         |2                         | 0.5734266|
|Stress         |1                         |3                         | 0.8391608|
|Stress         |2                         |3                         | 0.6285714|
|Anxiety        |0                         |2                         | 0.0165441|
|Anxiety        |0                         |4                         | 0.1993358|
|Anxiety        |0                         |1                         | 0.3237062|
|Anxiety        |0                         |3                         | 0.5817643|
|Anxiety        |2                         |4                         | 0.5555556|
|Anxiety        |2                         |1                         | 0.3095238|
|Anxiety        |2                         |3                         | 0.3809524|
|Anxiety        |4                         |1                         | 0.7301587|
|Anxiety        |4                         |3                         | 1.0000000|
|Anxiety        |1                         |3                         | 1.0000000|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.0076626|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.0197723|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.3993173|


## Tạo bảng và Forest plot với biến A365_mean

|   |Subgroup_Category |Subgroup                  | n_A365_mean|      Mean|    CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|-----------:|---------:|-----------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |          33|  95.87706|   84.966623| 106.78749|        NA|
|5  |Age_stage         |Age [40-50)               |          14|  77.10714|   52.897301| 101.31698|        NA|
|4  |Age_stage         |Age <30                   |          26|  81.03205|   63.109377|  98.95473|        NA|
|6  |Age_stage         |Age >=50                  |           6|  84.80556|   50.545876| 119.06523|        NA|
|30 |Anxiety           |0                         |          63|  86.60979|   77.398916|  95.82066|        NA|
|33 |Anxiety           |1                         |           5|  95.90000|   50.035261| 141.76474|        NA|
|31 |Anxiety           |2                         |           5|  93.05000|   57.206427| 128.89357|        NA|
|34 |Anxiety           |3                         |           2| 132.87500| -192.721496| 458.47150|        NA|
|32 |Anxiety           |4                         |           4|  48.04821|  -37.782081| 133.87851|        NA|
|38 |BMI_25_30         |BMI [25-30)               |          28|  84.96522|   71.440980|  98.48946|        NA|
|37 |BMI_25_30         |BMI <25                   |          43|  85.66667|   72.546659|  98.78667|        NA|
|39 |BMI_25_30         |BMI >=30                  |           8|  99.55208|   85.415946| 113.68822|        NA|
|21 |DASS_21           |ANXIETY                   |           3|  74.66667|  -16.887655| 166.22099|        NA|
|25 |DASS_21           |DEPRESSION                |           2| 100.79167|   28.260415| 173.32292|        NA|
|20 |DASS_21           |NORMAL                    |          57|  85.43129|   75.637978|  95.22459|        NA|
|22 |DASS_21           |STRESS                    |           4|  96.31250|   26.827033| 165.79797|        NA|
|24 |DASS_21           |STRESS ANXIETY            |           4| 104.00000|   28.437840| 179.56216|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |           9|  84.74365|   47.729635| 121.75767|        NA|
|1  |Gender            |female                    |          34|  86.67724|   73.113831| 100.24065| 0.9447406|
|2  |Gender            |male                      |          45|  86.93519|   75.588569|  98.28180| 0.9447406|
|35 |Hypertension      |No                        |          58|  85.27775|   74.928696|  95.62680| 0.4571462|
|36 |Hypertension      |Yes                       |          21|  91.09524|   75.391295| 106.79918| 0.4571462|
|40 |Obesity           |No                        |          71|  85.39004|   76.041921|  94.73816| 0.4846741|
|41 |Obesity           |Yes                       |           8|  99.55208|   85.415946| 113.68822| 0.4846741|
|7  |Race              |Asian or Asian British    |          61|  86.11245|   76.523937|  95.70097|        NA|
|9  |Race              |Black                     |           3|  18.83333|  -18.600844|  56.26751|        NA|
|8  |Race              |White                     |          15| 103.31667|   88.445624| 118.18771|        NA|
|18 |Smoking           |Non smoker                |          65|  87.03245|   78.025841|  96.03907| 0.8523118|
|19 |Smoking           |Smoker                    |          14|  85.85714|   59.033764| 112.68052| 0.8523118|
|26 |Stress            |0                         |          62|  85.40591|   76.215577|  94.59625|        NA|
|27 |Stress            |1                         |          10|  87.55000|   55.976583| 119.12342|        NA|
|28 |Stress            |2                         |           3|  64.98095|  -77.336533| 207.29844|        NA|
|29 |Stress            |3                         |           4| 123.37500|   85.080123| 161.66988|        NA|
|16 |Stress index      |No                        |          57|  85.43129|   75.637978|  95.22459| 0.7059216|
|17 |Stress index      |Yes                       |          22|  90.43301|   72.089887| 108.77613| 0.7059216|
|12 |Typer of skins    |1                         |          13| 101.56410|   87.641230| 115.48697|        NA|
|14 |Typer of skins    |2                         |           5|  90.70000|   22.551704| 158.84830|        NA|
|10 |Typer of skins    |3                         |          40|  94.44375|   84.879327| 104.00817|        NA|
|11 |Typer of skins    |4                         |          11|  95.18420|   72.462621| 117.90578|        NA|
|15 |Typer of skins    |5                         |           6|  33.66667|    6.190953|  61.14238|        NA|
|13 |Typer of skins    |6                         |           4|  14.62500|   -9.095925|  38.34592|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.3438253|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.2691536|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.6901766|
|Age_stage      |Age <30                   |Age [40-50)               | 0.8205324|
|Age_stage      |Age <30                   |Age >=50                  | 0.9437890|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.8411249|
|Race           |Asian or Asian British    |White                     | 0.1438121|
|Race           |Asian or Asian British    |Black                     | 0.0157774|
|Race           |White                     |Black                     | 0.0024510|
|Typer of skins |3                         |4                         | 0.7398131|
|Typer of skins |3                         |1                         | 0.4443058|
|Typer of skins |3                         |6                         | 0.0020520|
|Typer of skins |3                         |2                         | 1.0000000|
|Typer of skins |3                         |5                         | 0.0009301|
|Typer of skins |4                         |1                         | 0.3388859|
|Typer of skins |4                         |6                         | 0.0049617|
|Typer of skins |4                         |2                         | 0.7337700|
|Typer of skins |4                         |5                         | 0.0056827|
|Typer of skins |1                         |6                         | 0.0008403|
|Typer of skins |1                         |2                         | 0.6330532|
|Typer of skins |1                         |5                         | 0.0005160|
|Typer of skins |6                         |2                         | 0.0634921|
|Typer of skins |6                         |5                         | 0.2571429|
|Typer of skins |2                         |5                         | 0.1255411|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.5873261|
|DASS_21        |NORMAL                    |STRESS                    | 0.9535292|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.7507434|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.4145819|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.7534004|
|DASS_21        |ANXIETY                   |STRESS                    | 1.0000000|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.3727273|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.4000000|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.4000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.8251748|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.8857143|
|DASS_21        |STRESS                    |DEPRESSION                | 0.5333333|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.6041958|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.5818182|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 1.0000000|
|Stress         |0                         |1                         | 0.9610382|
|Stress         |0                         |2                         | 0.4252773|
|Stress         |0                         |3                         | 0.0438384|
|Stress         |1                         |2                         | 0.5734266|
|Stress         |1                         |3                         | 0.2397602|
|Stress         |2                         |3                         | 0.2285714|
|Anxiety        |0                         |2                         | 0.7069403|
|Anxiety        |0                         |4                         | 0.1153452|
|Anxiety        |0                         |1                         | 0.3910656|
|Anxiety        |0                         |3                         | 0.1334687|
|Anxiety        |2                         |4                         | 0.1904762|
|Anxiety        |2                         |1                         | 0.5476190|
|Anxiety        |2                         |3                         | 0.3809524|
|Anxiety        |4                         |1                         | 0.1111111|
|Anxiety        |4                         |3                         | 0.2666667|
|Anxiety        |1                         |3                         | 0.5714286|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.6087759|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.7265835|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.2697579|


## Tạo bảng và Forest plot với biến A460_mean

|   |Subgroup_Category |Subgroup                  | n_A460_mean|     Mean|    CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|-----------:|--------:|-----------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |          33| 62.77367|   56.057002|  69.49033|        NA|
|5  |Age_stage         |Age [40-50)               |          14| 65.74048|   48.300099|  83.18085|        NA|
|4  |Age_stage         |Age <30                   |          26| 51.74679|   42.642301|  60.85129|        NA|
|6  |Age_stage         |Age >=50                  |           6| 57.83333|   26.903553|  88.76311|        NA|
|30 |Anxiety           |0                         |          63| 61.00317|   55.038980|  66.96737|        NA|
|33 |Anxiety           |1                         |           5| 45.30000|   21.160889|  69.43911|        NA|
|31 |Anxiety           |2                         |           5| 67.35000|   58.048909|  76.65109|        NA|
|34 |Anxiety           |3                         |           2| 63.75000|  -15.663780| 143.16378|        NA|
|32 |Anxiety           |4                         |           4| 37.59107|  -11.596402|  86.77854|        NA|
|38 |BMI_25_30         |BMI [25-30)               |          28| 58.54277|   51.574542|  65.51100|        NA|
|37 |BMI_25_30         |BMI <25                   |          43| 59.07829|   50.562886|  67.59370|        NA|
|39 |BMI_25_30         |BMI >=30                  |           8| 63.09375|   49.480472|  76.70703|        NA|
|21 |DASS_21           |ANXIETY                   |           3| 54.33333|  -30.321959| 138.98863|        NA|
|25 |DASS_21           |DEPRESSION                |           2| 59.20833| -102.266352| 220.68302|        NA|
|20 |DASS_21           |NORMAL                    |          57| 60.64094|   54.266134|  67.01574|        NA|
|22 |DASS_21           |STRESS                    |           4| 67.06250|   26.356029| 107.76897|        NA|
|24 |DASS_21           |STRESS ANXIETY            |           4| 53.87500|   35.542813|  72.20719|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |           9| 51.40159|   33.301811|  69.50136|        NA|
|1  |Gender            |female                    |          34| 58.40532|   51.246258|  65.56439| 0.9093339|
|2  |Gender            |male                      |          45| 59.96741|   52.264562|  67.67025| 0.9093339|
|35 |Hypertension      |No                        |          58| 54.31720|   48.933295|  59.70111| 0.0017165|
|36 |Hypertension      |Yes                       |          21| 73.04365|   61.191586|  84.89572| 0.0017165|
|40 |Obesity           |No                        |          71| 58.86710|   53.147123|  64.58708| 0.5749977|
|41 |Obesity           |Yes                       |           8| 63.09375|   49.480472|  76.70703| 0.5749977|
|7  |Race              |Asian or Asian British    |          61| 61.92592|   55.791023|  68.06081|        NA|
|9  |Race              |Black                     |           3| 14.00000|    7.427589|  20.57241|        NA|
|8  |Race              |White                     |          15| 57.65556|   51.367696|  63.94341|        NA|
|18 |Smoking           |Non smoker                |          65| 57.85304|   52.893337|  62.81274| 0.3896294|
|19 |Smoking           |Smoker                    |          14| 65.99048|   45.445208|  86.53574| 0.3896294|
|26 |Stress            |0                         |          62| 60.28952|   54.199010|  66.38002|        NA|
|27 |Stress            |1                         |          10| 55.95000|   38.988681|  72.91132|        NA|
|28 |Stress            |2                         |           3| 42.37143|  -21.998061| 106.74092|        NA|
|29 |Stress            |3                         |           4| 64.93750|   51.441874|  78.43313|        NA|
|16 |Stress index      |No                        |          57| 60.64094|   54.266134|  67.01574| 0.6225678|
|17 |Stress index      |Yes                       |          22| 55.80823|   46.051660|  65.56479| 0.6225678|
|12 |Typer of skins    |1                         |          13| 59.14744|   53.210686|  65.08419|        NA|
|14 |Typer of skins    |2                         |           5| 53.20000|   31.929821|  74.47018|        NA|
|10 |Typer of skins    |3                         |          40| 69.09875|   62.521005|  75.67649|        NA|
|11 |Typer of skins    |4                         |          11| 60.33615|   45.696477|  74.97582|        NA|
|15 |Typer of skins    |5                         |           6| 27.79167|   13.127313|  42.45602|        NA|
|13 |Typer of skins    |6                         |           4| 13.75000|   10.221692|  17.27831|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.0930380|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.6086799|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.4834335|
|Age_stage      |Age <30                   |Age [40-50)               | 0.0971015|
|Age_stage      |Age <30                   |Age >=50                  | 0.7905541|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.2315445|
|Race           |Asian or Asian British    |White                     | 0.4849927|
|Race           |Asian or Asian British    |Black                     | 0.0057143|
|Race           |White                     |Black                     | 0.0024510|
|Typer of skins |3                         |4                         | 0.1877550|
|Typer of skins |3                         |1                         | 0.0880029|
|Typer of skins |3                         |6                         | 0.0011656|
|Typer of skins |3                         |2                         | 0.1202452|
|Typer of skins |3                         |5                         | 0.0002417|
|Typer of skins |4                         |1                         | 0.8646168|
|Typer of skins |4                         |6                         | 0.0014652|
|Typer of skins |4                         |2                         | 0.7426740|
|Typer of skins |4                         |5                         | 0.0071105|
|Typer of skins |1                         |6                         | 0.0008403|
|Typer of skins |1                         |2                         | 0.5662932|
|Typer of skins |1                         |5                         | 0.0005160|
|Typer of skins |6                         |2                         | 0.0158730|
|Typer of skins |6                         |5                         | 0.0666667|
|Typer of skins |2                         |5                         | 0.0519481|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.9459060|
|DASS_21        |NORMAL                    |STRESS                    | 0.7265644|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.5190986|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.5026940|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.9498932|
|DASS_21        |ANXIETY                   |STRESS                    | 1.0000000|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.3727273|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.6285714|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.8000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.6041958|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.3428571|
|DASS_21        |STRESS                    |DEPRESSION                | 1.0000000|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 1.0000000|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.9090909|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.8000000|
|Stress         |0                         |1                         | 0.5306759|
|Stress         |0                         |2                         | 0.2409454|
|Stress         |0                         |3                         | 0.5724575|
|Stress         |1                         |2                         | 0.4685315|
|Stress         |1                         |3                         | 0.3036963|
|Stress         |2                         |3                         | 0.2285714|
|Anxiety        |0                         |2                         | 0.3179055|
|Anxiety        |0                         |4                         | 0.1491786|
|Anxiety        |0                         |1                         | 0.1451116|
|Anxiety        |0                         |3                         | 0.7323949|
|Anxiety        |2                         |4                         | 0.1904762|
|Anxiety        |2                         |1                         | 0.0317460|
|Anxiety        |2                         |3                         | 0.8571429|
|Anxiety        |4                         |1                         | 0.5555556|
|Anxiety        |4                         |3                         | 0.5333333|
|Anxiety        |1                         |3                         | 0.3809524|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.9624584|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.6317932|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.5552805|


## Tạo bảng và Forest plot với biến Anadn_mean

|   |Subgroup_Category |Subgroup                  | n_Anadn_mean|      Mean|   CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|------------:|---------:|----------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |           33| 0.7790195|  0.6275641| 0.9304748|        NA|
|5  |Age_stage         |Age [40-50)               |           14| 1.5417381|  0.5205539| 2.5629223|        NA|
|4  |Age_stage         |Age <30                   |           26| 1.0597436|  0.6177187| 1.5017685|        NA|
|6  |Age_stage         |Age >=50                  |            6| 0.7679167|  0.5896037| 0.9462296|        NA|
|30 |Anxiety           |0                         |           63| 0.9801614|  0.7326360| 1.2276868|        NA|
|33 |Anxiety           |1                         |            5| 0.5850000|  0.2688020| 0.9011980|        NA|
|31 |Anxiety           |2                         |            5| 0.7995000|  0.3690480| 1.2299520|        NA|
|34 |Anxiety           |3                         |            2| 0.5125000| -1.1075411| 2.1325411|        NA|
|32 |Anxiety           |4                         |            4| 2.4387857| -0.7725927| 5.6501641|        NA|
|38 |BMI_25_30         |BMI [25-30)               |           28| 0.9588146|  0.5754893| 1.3421399|        NA|
|37 |BMI_25_30         |BMI <25                   |           43| 1.0973101|  0.7457093| 1.4489109|        NA|
|39 |BMI_25_30         |BMI >=30                  |            8| 0.6777083|  0.5250894| 0.8303272|        NA|
|21 |DASS_21           |ANXIETY                   |            3| 0.8483333|  0.4126639| 1.2840027|        NA|
|25 |DASS_21           |DEPRESSION                |            2| 0.8679167|  0.5132018| 1.2226315|        NA|
|20 |DASS_21           |NORMAL                    |           57| 1.0091111|  0.7361999| 1.2820223|        NA|
|22 |DASS_21           |STRESS                    |            4| 0.6237500|  0.3902162| 0.8572838|        NA|
|24 |DASS_21           |STRESS ANXIETY            |            4| 0.6625000| -0.0969236| 1.4219236|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |            9| 1.3897381|  0.1691178| 2.6103584|        NA|
|1  |Gender            |female                    |           34| 1.0693669|  0.6623175| 1.4764164| 0.2158163|
|2  |Gender            |male                      |           45| 0.9576519|  0.6800430| 1.2352607| 0.2158163|
|35 |Hypertension      |No                        |           58| 0.9225053|  0.6872354| 1.1577753| 0.0584671|
|36 |Hypertension      |Yes                       |           21| 1.2355952|  0.6285004| 1.8426901| 0.0584671|
|40 |Obesity           |No                        |           71| 1.0426922|  0.7872429| 1.2981414| 0.4026261|
|41 |Obesity           |Yes                       |            8| 0.6777083|  0.5250894| 0.8303272| 0.4026261|
|7  |Race              |Asian or Asian British    |           61| 1.0563029|  0.7771207| 1.3354850|        NA|
|9  |Race              |Black                     |            3| 1.9366667| -2.2033062| 6.0766395|        NA|
|8  |Race              |White                     |           15| 0.6138889|  0.4805006| 0.7472772|        NA|
|18 |Smoking           |Non smoker                |           65| 0.9155150|  0.7010017| 1.1300284| 0.0743164|
|19 |Smoking           |Smoker                    |           14| 1.4245952|  0.5219594| 2.3272310| 0.0743164|
|26 |Stress            |0                         |           62| 0.9967769|  0.7461467| 1.2474070|        NA|
|27 |Stress            |1                         |           10| 0.9692500|  0.2148150| 1.7236850|        NA|
|28 |Stress            |2                         |            3| 1.9200476| -3.6022885| 7.4423837|        NA|
|29 |Stress            |3                         |            4| 0.5500000|  0.3303766| 0.7696234|        NA|
|16 |Stress index      |No                        |           57| 1.0091111|  0.7361999| 1.2820223| 0.2645886|
|17 |Stress index      |Yes                       |           22| 0.9969762|  0.5281831| 1.4657693| 0.2645886|
|12 |Typer of skins    |1                         |           13| 0.6382692|  0.4881427| 0.7883957|        NA|
|14 |Typer of skins    |2                         |            5| 1.1490000|  0.0564380| 2.2415620|        NA|
|10 |Typer of skins    |3                         |           40| 0.9509000|  0.6525815| 1.2492185|        NA|
|11 |Typer of skins    |4                         |           11| 0.6649372|  0.5428830| 0.7869915|        NA|
|15 |Typer of skins    |5                         |            6| 1.6275000| -0.4066713| 3.6616713|        NA|
|13 |Typer of skins    |6                         |            4| 2.5737500| -0.3925575| 5.5400575|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.6359821|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.0212780|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.5302550|
|Age_stage      |Age <30                   |Age [40-50)               | 0.0593252|
|Age_stage      |Age <30                   |Age >=50                  | 0.6121610|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.2834393|
|Race           |Asian or Asian British    |White                     | 0.0030502|
|Race           |Asian or Asian British    |Black                     | 0.0420663|
|Race           |White                     |Black                     | 0.0098039|
|Typer of skins |3                         |4                         | 0.1878549|
|Typer of skins |3                         |1                         | 0.0332219|
|Typer of skins |3                         |6                         | 0.0095265|
|Typer of skins |3                         |2                         | 0.7588402|
|Typer of skins |3                         |5                         | 0.1559279|
|Typer of skins |4                         |1                         | 0.4340304|
|Typer of skins |4                         |6                         | 0.0029304|
|Typer of skins |4                         |2                         | 0.5096154|
|Typer of skins |4                         |5                         | 0.0365223|
|Typer of skins |1                         |6                         | 0.0033613|
|Typer of skins |1                         |2                         | 0.2887488|
|Typer of skins |1                         |5                         | 0.0066342|
|Typer of skins |6                         |2                         | 0.1904762|
|Typer of skins |6                         |5                         | 0.1714286|
|Typer of skins |2                         |5                         | 0.6623377|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.5192739|
|DASS_21        |NORMAL                    |STRESS                    | 0.1849166|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.4548065|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.1225204|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.4635423|
|DASS_21        |ANXIETY                   |STRESS                    | 0.2285714|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.3727273|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.4000000|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.8000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.9398601|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.4857143|
|DASS_21        |STRESS                    |DEPRESSION                | 0.1333333|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.1986014|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.3272727|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.5333333|
|Stress         |0                         |1                         | 0.1383880|
|Stress         |0                         |2                         | 0.9128598|
|Stress         |0                         |3                         | 0.0424555|
|Stress         |1                         |2                         | 0.4685315|
|Stress         |1                         |3                         | 0.6353646|
|Stress         |2                         |3                         | 0.2285714|
|Anxiety        |0                         |2                         | 0.8325109|
|Anxiety        |0                         |4                         | 0.2285441|
|Anxiety        |0                         |1                         | 0.0884514|
|Anxiety        |0                         |3                         | 0.0984289|
|Anxiety        |2                         |4                         | 0.1904762|
|Anxiety        |2                         |1                         | 0.2222222|
|Anxiety        |2                         |3                         | 0.3809524|
|Anxiety        |4                         |1                         | 0.0634921|
|Anxiety        |4                         |3                         | 0.1333333|
|Anxiety        |1                         |3                         | 0.8571429|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.9718423|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.4295151|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.4429047|


## Tạo bảng và Forest plot với biến POM_mean

|   |Subgroup_Category |Subgroup                  | n_POM_mean|      Mean|     CI_lower|   CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|----------:|---------:|------------:|----------:|---------:|
|3  |Age_stage         |Age [30-40)               |         33| 10.855431|    8.7368205|  12.974042|        NA|
|5  |Age_stage         |Age [40-50)               |         14|  6.256202|    3.8375625|   8.674842|        NA|
|4  |Age_stage         |Age <30                   |         26|  7.607596|    5.3435948|   9.871598|        NA|
|6  |Age_stage         |Age >=50                  |          6|  7.775833|    2.3574457|  13.194221|        NA|
|30 |Anxiety           |0                         |         63|  8.080082|    6.7738681|   9.386296|        NA|
|33 |Anxiety           |1                         |          5| 14.081000|    6.5291492|  21.632851|        NA|
|31 |Anxiety           |2                         |          5|  8.431750|    5.2559964|  11.607504|        NA|
|34 |Anxiety           |3                         |          2| 19.820000| -101.3971932| 141.037193|        NA|
|32 |Anxiety           |4                         |          4|  7.254911|   -2.5263293|  17.036151|        NA|
|38 |BMI_25_30         |BMI [25-30)               |         28| 10.129571|    7.6708049|  12.588336|        NA|
|37 |BMI_25_30         |BMI <25                   |         43|  7.445760|    5.7829588|   9.108561|        NA|
|39 |BMI_25_30         |BMI >=30                  |          8| 10.809115|    7.8083117|  13.809917|        NA|
|21 |DASS_21           |ANXIETY                   |          3| 11.660000|    1.5197343|  21.800266|        NA|
|25 |DASS_21           |DEPRESSION                |          2| 10.120000|  -77.1716265|  97.411626|        NA|
|20 |DASS_21           |NORMAL                    |         57|  7.703863|    6.3744005|   9.033325|        NA|
|22 |DASS_21           |STRESS                    |          4| 12.421250|    4.4246020|  20.417898|        NA|
|24 |DASS_21           |STRESS ANXIETY            |          4| 16.432500|   -0.1626486|  33.027649|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |          9|  8.945932|    4.6948737|  13.196991|        NA|
|1  |Gender            |female                    |         34|  8.332820|    6.3195473|  10.346094| 0.5187614|
|2  |Gender            |male                      |         45|  9.043393|    7.3164950|  10.770290| 0.5187614|
|35 |Hypertension      |No                        |         58|  9.833862|    8.2670420|  11.400681| 0.0035789|
|36 |Hypertension      |Yes                       |         21|  5.709742|    4.0187991|   7.400685| 0.0035789|
|40 |Obesity           |No                        |         71|  8.504164|    7.1084772|   9.899851| 0.1206767|
|41 |Obesity           |Yes                       |          8| 10.809115|    7.8083117|  13.809917| 0.1206767|
|7  |Race              |Asian or Asian British    |         61|  7.599321|    6.3288575|   8.869784|        NA|
|9  |Race              |Black                     |          3|  8.375000|   -9.3892944|  26.139294|        NA|
|8  |Race              |White                     |         15| 13.439000|    9.8976206|  16.980379|        NA|
|18 |Smoking           |Non smoker                |         65|  8.930411|    7.6495999|  10.211222| 0.1522790|
|19 |Smoking           |Smoker                    |         14|  7.842274|    3.2049095|  12.479638| 0.1522790|
|26 |Stress            |0                         |         62|  7.973229|    6.6776140|   9.268843|        NA|
|27 |Stress            |1                         |         10|  9.694875|    5.5256978|  13.864052|        NA|
|28 |Stress            |2                         |          3| 11.207381|   -9.7064030|  32.121165|        NA|
|29 |Stress            |3                         |          4| 16.339375|    2.3402860|  30.338464|        NA|
|16 |Stress index      |No                        |         57|  7.703863|    6.3744005|   9.033325| 0.0106560|
|17 |Stress index      |Yes                       |         22| 11.415836|    8.4532130|  14.378459| 0.0106560|
|12 |Typer of skins    |1                         |         13| 11.498237|    8.6778789|  14.318595|        NA|
|14 |Typer of skins    |2                         |          5| 15.332000|    2.9536743|  27.710326|        NA|
|10 |Typer of skins    |3                         |         40|  6.905462|    5.4848898|   8.326035|        NA|
|11 |Typer of skins    |4                         |         11| 12.142771|    8.8245205|  15.461021|        NA|
|15 |Typer of skins    |5                         |          6|  4.540417|    0.9836002|   8.097233|        NA|
|13 |Typer of skins    |6                         |          4|  6.775000|   -3.8197345|  17.369734|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.0245119|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.0052795|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.1841702|
|Age_stage      |Age <30                   |Age [40-50)               | 0.5847069|
|Age_stage      |Age <30                   |Age >=50                  | 0.8692882|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.4441692|
|Race           |Asian or Asian British    |White                     | 0.0005702|
|Race           |Asian or Asian British    |Black                     | 0.9240876|
|Race           |White                     |Black                     | 0.2500000|
|Typer of skins |3                         |4                         | 0.0023686|
|Typer of skins |3                         |1                         | 0.0019539|
|Typer of skins |3                         |6                         | 0.5947949|
|Typer of skins |3                         |2                         | 0.0314874|
|Typer of skins |3                         |5                         | 0.2276480|
|Typer of skins |4                         |1                         | 0.7762108|
|Typer of skins |4                         |6                         | 0.1377289|
|Typer of skins |4                         |2                         | 0.7426740|
|Typer of skins |4                         |5                         | 0.0030705|
|Typer of skins |1                         |6                         | 0.1302521|
|Typer of skins |1                         |2                         | 0.6330532|
|Typer of skins |1                         |5                         | 0.0032434|
|Typer of skins |6                         |2                         | 0.1111111|
|Typer of skins |6                         |5                         | 1.0000000|
|Typer of skins |2                         |5                         | 0.0519481|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.1187082|
|DASS_21        |NORMAL                    |STRESS                    | 0.0602089|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.4217103|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.0492215|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.6600844|
|DASS_21        |ANXIETY                   |STRESS                    | 1.0000000|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.6000000|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.6285714|
|DASS_21        |ANXIETY                   |DEPRESSION                | 1.0000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.4139860|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.6857143|
|DASS_21        |STRESS                    |DEPRESSION                | 0.8000000|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.1482517|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.9090909|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.5333333|
|Stress         |0                         |1                         | 0.2861824|
|Stress         |0                         |2                         | 0.4436768|
|Stress         |0                         |3                         | 0.0215788|
|Stress         |1                         |2                         | 0.6923077|
|Stress         |1                         |3                         | 0.0539461|
|Stress         |2                         |3                         | 0.8571429|
|Anxiety        |0                         |2                         | 0.5258090|
|Anxiety        |0                         |4                         | 0.7608824|
|Anxiety        |0                         |1                         | 0.0288732|
|Anxiety        |0                         |3                         | 0.0839162|
|Anxiety        |2                         |4                         | 1.0000000|
|Anxiety        |2                         |1                         | 0.1507937|
|Anxiety        |2                         |3                         | 0.1904762|
|Anxiety        |4                         |1                         | 0.0634921|
|Anxiety        |4                         |3                         | 0.5333333|
|Anxiety        |1                         |3                         | 0.8571429|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.0540043|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.0403912|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.5374172|



## Tạo bảng và Forest plot với biến A-E_mean

|   |Subgroup_Category |Subgroup                  | n_A-E_mean|     Mean|   CI_lower| CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|----------:|--------:|----------:|--------:|---------:|
|3  |Age_stage         |Age [30-40)               |         33| 1.687170|  1.4225196| 1.951820|        NA|
|5  |Age_stage         |Age [40-50)               |         14| 1.060762|  0.6679014| 1.453622|        NA|
|4  |Age_stage         |Age <30                   |         26| 1.398237|  1.1228389| 1.673636|        NA|
|6  |Age_stage         |Age >=50                  |          6| 1.826944|  0.3438377| 3.310051|        NA|
|30 |Anxiety           |0                         |         63| 1.477246|  1.2699050| 1.684587|        NA|
|33 |Anxiety           |1                         |          5| 1.137000|  0.5753169| 1.698683|        NA|
|31 |Anxiety           |2                         |          5| 1.391250|  0.6030638| 2.179436|        NA|
|34 |Anxiety           |3                         |          2| 2.361250| -5.1830591| 9.905559|        NA|
|32 |Anxiety           |4                         |          4| 1.853214|  0.4511301| 3.255298|        NA|
|38 |BMI_25_30         |BMI [25-30)               |         28| 1.429537|  1.1306870| 1.728386|        NA|
|37 |BMI_25_30         |BMI <25                   |         43| 1.458000|  1.2056854| 1.710315|        NA|
|39 |BMI_25_30         |BMI >=30                  |          8| 1.890260|  1.2185406| 2.561980|        NA|
|21 |DASS_21           |ANXIETY                   |          3| 1.010000| -0.3025442| 2.322544|        NA|
|25 |DASS_21           |DEPRESSION                |          2| 2.175833|  1.4875806| 2.864086|        NA|
|20 |DASS_21           |NORMAL                    |         57| 1.442015|  1.2170064| 1.667023|        NA|
|22 |DASS_21           |STRESS                    |          4| 1.630000|  0.9147456| 2.345254|        NA|
|24 |DASS_21           |STRESS ANXIETY            |          4| 1.706250|  0.1994760| 3.213024|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |          9| 1.657956|  1.1280665| 2.187846|        NA|
|1  |Gender            |female                    |         34| 1.466224|  1.2802464| 1.652201| 0.5724904|
|2  |Gender            |male                      |         45| 1.510922|  1.2216150| 1.800229| 0.5724904|
|35 |Hypertension      |No                        |         58| 1.635793|  1.4276423| 1.843945| 0.0056259|
|36 |Hypertension      |Yes                       |         21| 1.093671|  0.7723999| 1.414941| 0.0056259|
|40 |Obesity           |No                        |         71| 1.446775|  1.2585150| 1.635035| 0.1024263|
|41 |Obesity           |Yes                       |          8| 1.890260|  1.2185406| 2.561980| 0.1024263|
|7  |Race              |Asian or Asian British    |         61| 1.374313|  1.1815818| 1.567045|        NA|
|9  |Race              |Black                     |          3| 1.458333| -0.1865210| 3.103188|        NA|
|8  |Race              |White                     |         15| 1.975667|  1.4847146| 2.466619|        NA|
|18 |Smoking           |Non smoker                |         65| 1.591499|  1.4015277| 1.781470| 0.0061233|
|19 |Smoking           |Smoker                    |         14| 1.028262|  0.5493677| 1.507156| 0.0061233|
|26 |Stress            |0                         |         62| 1.444782|  1.2328791| 1.656685|        NA|
|27 |Stress            |1                         |         10| 1.601125|  1.2516204| 1.950630|        NA|
|28 |Stress            |2                         |          3| 1.277619| -1.2881681| 3.843406|        NA|
|29 |Stress            |3                         |          4| 2.105625|  0.9579921| 3.253258|        NA|
|16 |Stress index      |No                        |         57| 1.442015|  1.2170064| 1.667023| 0.1715849|
|17 |Stress index      |Yes                       |         22| 1.620376|  1.3231169| 1.917635| 0.1715849|
|12 |Typer of skins    |1                         |         13| 1.970481|  1.4585989| 2.482363|        NA|
|14 |Typer of skins    |2                         |          5| 1.866000|  0.7416306| 2.990369|        NA|
|10 |Typer of skins    |3                         |         40| 1.208621|  0.9987070| 1.418535|        NA|
|11 |Typer of skins    |4                         |         11| 1.846320|  1.4452738| 2.247367|        NA|
|15 |Typer of skins    |5                         |          6| 1.549583|  0.2270473| 2.872119|        NA|
|13 |Typer of skins    |6                         |          4| 1.236250|  0.1228793| 2.349621|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.1106028|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.0094922|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.9844714|
|Age_stage      |Age <30                   |Age [40-50)               | 0.1538800|
|Age_stage      |Age <30                   |Age >=50                  | 0.7597551|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.3118679|
|Race           |Asian or Asian British    |White                     | 0.0109306|
|Race           |Asian or Asian British    |Black                     | 0.6113142|
|Race           |White                     |Black                     | 0.3602941|
|Typer of skins |3                         |4                         | 0.0023686|
|Typer of skins |3                         |1                         | 0.0018052|
|Typer of skins |3                         |6                         | 0.7980346|
|Typer of skins |3                         |2                         | 0.1041066|
|Typer of skins |3                         |5                         | 0.5992374|
|Typer of skins |4                         |1                         | 0.7762108|
|Typer of skins |4                         |6                         | 0.1772894|
|Typer of skins |4                         |2                         | 0.9130037|
|Typer of skins |4                         |5                         | 0.1489981|
|Typer of skins |1                         |6                         | 0.1630252|
|Typer of skins |1                         |2                         | 1.0000000|
|Typer of skins |1                         |5                         | 0.1791243|
|Typer of skins |6                         |2                         | 0.1904762|
|Typer of skins |6                         |5                         | 0.7619048|
|Typer of skins |2                         |5                         | 0.5367965|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.4555517|
|DASS_21        |NORMAL                    |STRESS                    | 0.3820712|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.2784829|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.4935383|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.1484450|
|DASS_21        |ANXIETY                   |STRESS                    | 0.2285714|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.1454545|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.2285714|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.2000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.9398601|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 1.0000000|
|DASS_21        |STRESS                    |DEPRESSION                | 0.2666667|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.9398601|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.3272727|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.5333333|
|Stress         |0                         |1                         | 0.2543628|
|Stress         |0                         |2                         | 0.6502993|
|Stress         |0                         |3                         | 0.0879188|
|Stress         |1                         |2                         | 0.5734266|
|Stress         |1                         |3                         | 0.3736264|
|Stress         |2                         |3                         | 0.4000000|
|Anxiety        |0                         |2                         | 0.9625178|
|Anxiety        |0                         |4                         | 0.3210194|
|Anxiety        |0                         |1                         | 0.4243469|
|Anxiety        |0                         |3                         | 0.1239302|
|Anxiety        |2                         |4                         | 0.2857143|
|Anxiety        |2                         |1                         | 0.6904762|
|Anxiety        |2                         |3                         | 0.3809524|
|Anxiety        |4                         |1                         | 0.2857143|
|Anxiety        |4                         |3                         | 0.8000000|
|Anxiety        |1                         |3                         | 0.1904762|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.9250099|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.1123554|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.1453846|


## Tạo bảng và Forest plot với biến A-N_mean

|   |Subgroup_Category |Subgroup                  | n_A-N_mean|     Mean|   CI_lower| CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|----------:|--------:|----------:|--------:|---------:|
|3  |Age_stage         |Age [30-40)               |         33| 1.593297|  1.3343856| 1.852209|        NA|
|5  |Age_stage         |Age [40-50)               |         14| 1.189452|  0.7215728| 1.657332|        NA|
|4  |Age_stage         |Age <30                   |         26| 1.386506|  1.1087227| 1.664290|        NA|
|6  |Age_stage         |Age >=50                  |          6| 1.678472|  0.4469334| 2.910011|        NA|
|30 |Anxiety           |0                         |         63| 1.419468|  1.2305287| 1.608408|        NA|
|33 |Anxiety           |1                         |          5| 1.223000|  0.4837457| 1.962254|        NA|
|31 |Anxiety           |2                         |          5| 1.337500|  0.5025733| 2.172427|        NA|
|34 |Anxiety           |3                         |          2| 2.455000| -3.2627921| 8.172792|        NA|
|32 |Anxiety           |4                         |          4| 2.053036|  0.2217600| 3.884311|        NA|
|38 |BMI_25_30         |BMI [25-30)               |         28| 1.459571|  1.1603465| 1.758795|        NA|
|37 |BMI_25_30         |BMI <25                   |         43| 1.395306|  1.1573773| 1.633235|        NA|
|39 |BMI_25_30         |BMI >=30                  |          8| 1.810625|  1.1785520| 2.442698|        NA|
|21 |DASS_21           |ANXIETY                   |          3| 0.885000| -0.1803592| 1.950359|        NA|
|25 |DASS_21           |DEPRESSION                |          2| 2.127083|  1.0735272| 3.180639|        NA|
|20 |DASS_21           |NORMAL                    |         57| 1.403067|  1.1977798| 1.608355|        NA|
|22 |DASS_21           |STRESS                    |          4| 1.299375|  0.8084286| 1.790321|        NA|
|24 |DASS_21           |STRESS ANXIETY            |          4| 1.710000|  0.0884221| 3.331578|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |          9| 1.825516|  1.1928255| 2.458206|        NA|
|1  |Gender            |female                    |         34| 1.440602|  1.2317389| 1.649466| 0.7104068|
|2  |Gender            |male                      |         45| 1.474904|  1.2088786| 1.740929| 0.7104068|
|35 |Hypertension      |No                        |         58| 1.592620|  1.3967444| 1.788496| 0.0052540|
|36 |Hypertension      |Yes                       |         21| 1.094246|  0.7584454| 1.430047| 0.0052540|
|40 |Obesity           |No                        |         71| 1.420650|  1.2389468| 1.602353| 0.1880664|
|41 |Obesity           |Yes                       |          8| 1.810625|  1.1785520| 2.442698| 0.1880664|
|7  |Race              |Asian or Asian British    |         61| 1.307833|  1.1269228| 1.488743|        NA|
|9  |Race              |Black                     |          3| 1.970000| -0.7994515| 4.739452|        NA|
|8  |Race              |White                     |         15| 1.977556|  1.5665373| 2.388574|        NA|
|18 |Smoking           |Non smoker                |         65| 1.534366|  1.3545240| 1.714209| 0.0226720|
|19 |Smoking           |Smoker                    |         14| 1.115524|  0.5938598| 1.637188| 0.0226720|
|26 |Stress            |0                         |         62| 1.401355|  1.2069245| 1.595785|        NA|
|27 |Stress            |1                         |         10| 1.662000|  1.1883031| 2.135697|        NA|
|28 |Stress            |2                         |          3| 1.377381| -1.7026127| 4.457375|        NA|
|29 |Stress            |3                         |          4| 1.928750|  0.6139051| 3.243595|        NA|
|16 |Stress index      |No                        |         57| 1.403067|  1.1977798| 1.608355| 0.2716902|
|17 |Stress index      |Yes                       |         22| 1.608014|  1.2706521| 1.945376| 0.2716902|
|12 |Typer of skins    |1                         |         13| 1.963269|  1.5562435| 2.370295|        NA|
|14 |Typer of skins    |2                         |          5| 1.956000|  0.8811051| 3.030895|        NA|
|10 |Typer of skins    |3                         |         40| 1.167683|  0.9671601| 1.368207|        NA|
|11 |Typer of skins    |4                         |         11| 1.684665|  1.2307360| 2.138593|        NA|
|15 |Typer of skins    |5                         |          6| 1.403333|  0.3263973| 2.480269|        NA|
|13 |Typer of skins    |6                         |          4| 1.597500| -0.2742175| 3.469218|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.4053471|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.0579639|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.9534353|
|Age_stage      |Age <30                   |Age [40-50)               | 0.3917727|
|Age_stage      |Age <30                   |Age >=50                  | 0.6890791|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.3530444|
|Race           |Asian or Asian British    |White                     | 0.0042612|
|Race           |Asian or Asian British    |Black                     | 0.2662794|
|Race           |White                     |Black                     | 1.0000000|
|Typer of skins |3                         |4                         | 0.0185432|
|Typer of skins |3                         |1                         | 0.0009343|
|Typer of skins |3                         |6                         | 0.7084147|
|Typer of skins |3                         |2                         | 0.0467097|
|Typer of skins |3                         |5                         | 0.7869508|
|Typer of skins |4                         |1                         | 0.2766683|
|Typer of skins |4                         |6                         | 0.8512821|
|Typer of skins |4                         |2                         | 0.5833333|
|Typer of skins |4                         |5                         | 0.3010666|
|Typer of skins |1                         |6                         | 0.6235294|
|Typer of skins |1                         |2                         | 0.8435541|
|Typer of skins |1                         |5                         | 0.1273773|
|Typer of skins |6                         |2                         | 0.5555556|
|Typer of skins |6                         |5                         | 1.0000000|
|Typer of skins |2                         |5                         | 0.4285714|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.2488196|
|DASS_21        |NORMAL                    |STRESS                    | 0.8497908|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.1449922|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.6101329|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.1870324|
|DASS_21        |ANXIETY                   |STRESS                    | 0.2285714|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.1000000|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.2285714|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.2000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.2601399|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 1.0000000|
|DASS_21        |STRESS                    |DEPRESSION                | 0.1333333|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 1.0000000|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.3272727|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 1.0000000|
|Stress         |0                         |1                         | 0.1983124|
|Stress         |0                         |2                         | 0.6959302|
|Stress         |0                         |3                         | 0.2317387|
|Stress         |1                         |2                         | 0.4685315|
|Stress         |1                         |3                         | 0.6353646|
|Stress         |2                         |3                         | 0.4000000|
|Anxiety        |0                         |2                         | 0.8508946|
|Anxiety        |0                         |4                         | 0.2389535|
|Anxiety        |0                         |1                         | 0.5970201|
|Anxiety        |0                         |3                         | 0.0984436|
|Anxiety        |2                         |4                         | 0.5555556|
|Anxiety        |2                         |1                         | 1.0000000|
|Anxiety        |2                         |3                         | 0.0952381|
|Anxiety        |4                         |1                         | 0.4126984|
|Anxiety        |4                         |3                         | 0.8000000|
|Anxiety        |1                         |3                         | 0.1904762|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.8784353|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.1532241|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.3414341|


## Tạo bảng và Forest plot với biến A-M_mean

|   |Subgroup_Category |Subgroup                  | n_A-M_mean|      Mean|   CI_lower| CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|----------:|---------:|----------:|--------:|---------:|
|3  |Age_stage         |Age [30-40)               |         33| 1.2711530|  1.0596429| 1.482663|        NA|
|5  |Age_stage         |Age [40-50)               |         14| 0.9285714|  0.5785816| 1.278561|        NA|
|4  |Age_stage         |Age <30                   |         26| 1.1463462|  0.9204643| 1.372228|        NA|
|6  |Age_stage         |Age >=50                  |          6| 1.2611111|  0.4676743| 2.054548|        NA|
|30 |Anxiety           |0                         |         63| 1.1326984|  0.9848573| 1.280539|        NA|
|33 |Anxiety           |1                         |          5| 1.0540000|  0.4288311| 1.679169|        NA|
|31 |Anxiety           |2                         |          5| 1.0150000|  0.4896352| 1.540365|        NA|
|34 |Anxiety           |3                         |          2| 1.8512500| -2.1988528| 5.901353|        NA|
|32 |Anxiety           |4                         |          4| 1.7280536|  0.3317575| 3.124350|        NA|
|38 |BMI_25_30         |BMI [25-30)               |         28| 1.1954065|  0.9515220| 1.439291|        NA|
|37 |BMI_25_30         |BMI <25                   |         43| 1.1317054|  0.9440730| 1.319338|        NA|
|39 |BMI_25_30         |BMI >=30                  |          8| 1.2731250|  0.8736046| 1.672645|        NA|
|21 |DASS_21           |ANXIETY                   |          3| 0.7516667|  0.1021783| 1.401155|        NA|
|25 |DASS_21           |DEPRESSION                |          2| 1.6187500|  0.2687157| 2.968784|        NA|
|20 |DASS_21           |NORMAL                    |         57| 1.1073246|  0.9475050| 1.267144|        NA|
|22 |DASS_21           |STRESS                    |          4| 1.2512500|  0.6278446| 1.874655|        NA|
|24 |DASS_21           |STRESS ANXIETY            |          4| 1.4112500|  0.2271979| 2.595302|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |          9| 1.4510794|  0.9545638| 1.947595|        NA|
|1  |Gender            |female                    |         34| 1.1708249|  0.9909812| 1.350669| 0.8006618|
|2  |Gender            |male                      |         45| 1.1669259|  0.9680019| 1.365850| 0.8006618|
|35 |Hypertension      |No                        |         58| 1.2917911|  1.1371486| 1.446433| 0.0020347|
|36 |Hypertension      |Yes                       |         21| 0.8283730|  0.6000964| 1.056650| 0.0020347|
|40 |Obesity           |No                        |         71| 1.1568270|  1.0115730| 1.302081| 0.5262217|
|41 |Obesity           |Yes                       |          8| 1.2731250|  0.8736046| 1.672645| 0.5262217|
|7  |Race              |Asian or Asian British    |         61| 1.0695172|  0.9179422| 1.221092|        NA|
|9  |Race              |Black                     |          3| 1.4416667| -0.2229064| 3.106240|        NA|
|8  |Race              |White                     |         15| 1.5169444|  1.2400191| 1.793870|        NA|
|18 |Smoking           |Non smoker                |         65| 1.2305341|  1.0901183| 1.370950| 0.0204801|
|19 |Smoking           |Smoker                    |         14| 0.8810714|  0.4856000| 1.276543| 0.0204801|
|26 |Stress            |0                         |         62| 1.1066129|  0.9562716| 1.256954|        NA|
|27 |Stress            |1                         |         10| 1.3405000|  1.0175030| 1.663497|        NA|
|28 |Stress            |2                         |          3| 1.2690714| -1.3888316| 3.926975|        NA|
|29 |Stress            |3                         |          4| 1.6243750|  0.6351662| 2.613584|        NA|
|16 |Stress index      |No                        |         57| 1.1073246|  0.9475050| 1.267144| 0.1230418|
|17 |Stress index      |Yes                       |         22| 1.3273734|  1.0719034| 1.582843| 0.1230418|
|12 |Typer of skins    |1                         |         13| 1.4678846|  1.1782660| 1.757503|        NA|
|14 |Typer of skins    |2                         |          5| 1.5710000|  0.8799300| 2.262070|        NA|
|10 |Typer of skins    |3                         |         40| 0.9471667|  0.7720734| 1.122260|        NA|
|11 |Typer of skins    |4                         |         11| 1.4355043|  1.0827910| 1.788218|        NA|
|15 |Typer of skins    |5                         |          6| 1.1533333|  0.3044416| 2.002225|        NA|
|13 |Typer of skins    |6                         |          4| 1.1962500|  0.0266672| 2.365833|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.4361800|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.0595264|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.9848769|
|Age_stage      |Age <30                   |Age [40-50)               | 0.2543006|
|Age_stage      |Age <30                   |Age >=50                  | 0.8692882|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.3118679|
|Race           |Asian or Asian British    |White                     | 0.0048174|
|Race           |Asian or Asian British    |Black                     | 0.3406493|
|Race           |White                     |Black                     | 1.0000000|
|Typer of skins |3                         |4                         | 0.0117598|
|Typer of skins |3                         |1                         | 0.0024571|
|Typer of skins |3                         |6                         | 0.6981274|
|Typer of skins |3                         |2                         | 0.0263379|
|Typer of skins |3                         |5                         | 0.5681321|
|Typer of skins |4                         |1                         | 0.7329601|
|Typer of skins |4                         |6                         | 0.7531136|
|Typer of skins |4                         |2                         | 0.6611722|
|Typer of skins |4                         |5                         | 0.1489981|
|Typer of skins |1                         |6                         | 0.6235294|
|Typer of skins |1                         |2                         | 0.5662932|
|Typer of skins |1                         |5                         | 0.1517765|
|Typer of skins |6                         |2                         | 0.2857143|
|Typer of skins |6                         |5                         | 1.0000000|
|Typer of skins |2                         |5                         | 0.2467532|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.2777513|
|DASS_21        |NORMAL                    |STRESS                    | 0.4843781|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.1209313|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.3148009|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.2014176|
|DASS_21        |ANXIETY                   |STRESS                    | 0.1142857|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.1454545|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.2285714|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.2000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.6041958|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.6857143|
|DASS_21        |STRESS                    |DEPRESSION                | 0.2666667|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.8251748|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.9090909|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 1.0000000|
|Stress         |0                         |1                         | 0.1384007|
|Stress         |0                         |2                         | 0.9376976|
|Stress         |0                         |3                         | 0.0983819|
|Stress         |1                         |2                         | 0.6923077|
|Stress         |1                         |3                         | 0.3036963|
|Stress         |2                         |3                         | 0.8571429|
|Anxiety        |0                         |2                         | 0.7779678|
|Anxiety        |0                         |4                         | 0.1348679|
|Anxiety        |0                         |1                         | 0.9625174|
|Anxiety        |0                         |3                         | 0.1239261|
|Anxiety        |2                         |4                         | 0.2857143|
|Anxiety        |2                         |1                         | 1.0000000|
|Anxiety        |2                         |3                         | 0.1904762|
|Anxiety        |4                         |1                         | 0.2857143|
|Anxiety        |4                         |3                         | 1.0000000|
|Anxiety        |1                         |3                         | 0.1904762|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.7821702|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.4448167|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.7319891|

## Tạo bảng và Forest plot với biến A-R_mean

|   |Subgroup_Category |Subgroup                  | n_A-R_mean|      Mean|   CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|----------:|---------:|----------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |         33| 0.7331418|  0.6259639| 0.8403197|        NA|
|5  |Age_stage         |Age [40-50)               |         14| 0.6227381|  0.4384387| 0.8070375|        NA|
|4  |Age_stage         |Age <30                   |         26| 0.6820192|  0.5818995| 0.7821389|        NA|
|6  |Age_stage         |Age >=50                  |          6| 0.8145833|  0.4497840| 1.1793827|        NA|
|30 |Anxiety           |0                         |         63| 0.6844180|  0.6122603| 0.7565757|        NA|
|33 |Anxiety           |1                         |          5| 0.8690000|  0.3807402| 1.3572598|        NA|
|31 |Anxiety           |2                         |          5| 0.5572500|  0.4323466| 0.6821534|        NA|
|34 |Anxiety           |3                         |          2| 1.1012500| -1.8052943| 4.0077943|        NA|
|32 |Anxiety           |4                         |          4| 0.7699821|  0.4255343| 1.1144299|        NA|
|38 |BMI_25_30         |BMI [25-30)               |         28| 0.7634201|  0.6507693| 0.8760708|        NA|
|37 |BMI_25_30         |BMI <25                   |         43| 0.6471512|  0.5622957| 0.7320066|        NA|
|39 |BMI_25_30         |BMI >=30                  |          8| 0.7910938|  0.5041723| 1.0780152|        NA|
|21 |DASS_21           |ANXIETY                   |          3| 0.5300000|  0.2575930| 0.8024070|        NA|
|25 |DASS_21           |DEPRESSION                |          2| 1.0112500|  0.0741674| 1.9483326|        NA|
|20 |DASS_21           |NORMAL                    |         57| 0.6613743|  0.5853139| 0.7374346|        NA|
|22 |DASS_21           |STRESS                    |          4| 0.8493750|  0.5254400| 1.1733100|        NA|
|24 |DASS_21           |STRESS ANXIETY            |          4| 1.0575000|  0.3281508| 1.7868492|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |          9| 0.7326310|  0.6026725| 0.8625895|        NA|
|1  |Gender            |female                    |         34| 0.7251572|  0.6269389| 0.8233756| 0.8275483|
|2  |Gender            |male                      |         45| 0.6861481|  0.5961281| 0.7761682| 0.8275483|
|35 |Hypertension      |No                        |         58| 0.7573838|  0.6837370| 0.8310307| 0.0037059|
|36 |Hypertension      |Yes                       |         21| 0.5525595|  0.4288956| 0.6762234| 0.0037059|
|40 |Obesity           |No                        |         71| 0.6930037|  0.6254546| 0.7605528| 0.6143986|
|41 |Obesity           |Yes                       |          8| 0.7910938|  0.5041723| 1.0780152| 0.6143986|
|7  |Race              |Asian or Asian British    |         61| 0.6571505|  0.5858760| 0.7284249|        NA|
|9  |Race              |Black                     |          3| 0.7883333|  0.4919669| 1.0846997|        NA|
|8  |Race              |White                     |         15| 0.8720556|  0.7006882| 1.0434229|        NA|
|18 |Smoking           |Non smoker                |         65| 0.7296720|  0.6621857| 0.7971583| 0.0807770|
|19 |Smoking           |Smoker                    |         14| 0.5788095|  0.3771885| 0.7804306| 0.0807770|
|26 |Stress            |0                         |         62| 0.6663038|  0.5940959| 0.7385116|        NA|
|27 |Stress            |1                         |         10| 0.8453750|  0.6313640| 1.0593860|        NA|
|28 |Stress            |2                         |          3| 0.7474762|  0.0946604| 1.4002920|        NA|
|29 |Stress            |3                         |          4| 0.8812500|  0.3778881| 1.3846119|        NA|
|16 |Stress index      |No                        |         57| 0.6613743|  0.5853139| 0.7374346| 0.0614357|
|17 |Stress index      |Yes                       |         22| 0.8106218|  0.6867370| 0.9345065| 0.0614357|
|12 |Typer of skins    |1                         |         13| 0.8410577|  0.6544881| 1.0276273|        NA|
|14 |Typer of skins    |2                         |          5| 0.9130000|  0.5073491| 1.3186509|        NA|
|10 |Typer of skins    |3                         |         40| 0.5681667|  0.4941772| 0.6421561|        NA|
|11 |Typer of skins    |4                         |         11| 0.8908268|  0.7325203| 1.0491334|        NA|
|15 |Typer of skins    |5                         |          6| 0.7695833|  0.3799776| 1.1591891|        NA|
|13 |Typer of skins    |6                         |          4| 0.7225000|  0.4618841| 0.9831159|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.7717352|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.3401702|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.4576410|
|Age_stage      |Age <30                   |Age [40-50)               | 0.4695872|
|Age_stage      |Age <30                   |Age >=50                  | 0.3813739|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.2740454|
|Race           |Asian or Asian British    |White                     | 0.0157540|
|Race           |Asian or Asian British    |Black                     | 0.3406106|
|Race           |White                     |Black                     | 1.0000000|
|Typer of skins |3                         |4                         | 0.0008964|
|Typer of skins |3                         |1                         | 0.0040576|
|Typer of skins |3                         |6                         | 0.1913715|
|Typer of skins |3                         |2                         | 0.0288675|
|Typer of skins |3                         |5                         | 0.1758435|
|Typer of skins |4                         |1                         | 0.4940332|
|Typer of skins |4                         |6                         | 0.2256410|
|Typer of skins |4                         |2                         | 1.0000000|
|Typer of skins |4                         |5                         | 0.6874914|
|Typer of skins |1                         |6                         | 0.7033613|
|Typer of skins |1                         |2                         | 0.6330532|
|Typer of skins |1                         |5                         | 0.9660917|
|Typer of skins |6                         |2                         | 0.4126984|
|Typer of skins |6                         |5                         | 0.6095238|
|Typer of skins |2                         |5                         | 0.5367965|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.3088457|
|DASS_21        |NORMAL                    |STRESS                    | 0.1754477|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.3549723|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.0642779|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.0897946|
|DASS_21        |ANXIETY                   |STRESS                    | 0.1142857|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.0636364|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.1142857|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.2000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.3300699|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.6857143|
|DASS_21        |STRESS                    |DEPRESSION                | 0.5333333|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.2601399|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.0727273|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 1.0000000|
|Stress         |0                         |1                         | 0.0967170|
|Stress         |0                         |2                         | 0.6059010|
|Stress         |0                         |3                         | 0.1663245|
|Stress         |1                         |2                         | 0.5734266|
|Stress         |1                         |3                         | 0.8391608|
|Stress         |2                         |3                         | 0.6285714|
|Anxiety        |0                         |2                         | 0.2544121|
|Anxiety        |0                         |4                         | 0.5604208|
|Anxiety        |0                         |1                         | 0.2957123|
|Anxiety        |0                         |3                         | 0.0984289|
|Anxiety        |2                         |4                         | 0.1904762|
|Anxiety        |2                         |1                         | 0.0555556|
|Anxiety        |2                         |3                         | 0.0952381|
|Anxiety        |4                         |1                         | 0.9047619|
|Anxiety        |4                         |3                         | 0.2666667|
|Anxiety        |1                         |3                         | 0.3809524|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.1261139|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.3926743|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.9544726|


## Tạo bảng và Forest plot với biến A-C_mean

|   |Subgroup_Category |Subgroup                  | n_A-C_mean|      Mean|  CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|----------:|---------:|---------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |         33| 0.9474264| 0.8518189| 1.0430339|        NA|
|5  |Age_stage         |Age [40-50)               |         14| 0.8450357| 0.5883589| 1.1017126|        NA|
|4  |Age_stage         |Age <30                   |         26| 0.9086859| 0.7323884| 1.0849834|        NA|
|6  |Age_stage         |Age >=50                  |          6| 1.0769444| 0.6675533| 1.4863356|        NA|
|30 |Anxiety           |0                         |         63| 0.9061190| 0.8096778| 1.0025603|        NA|
|33 |Anxiety           |1                         |          5| 0.8990000| 0.5619334| 1.2360666|        NA|
|31 |Anxiety           |2                         |          5| 0.9365000| 0.6057095| 1.2672905|        NA|
|34 |Anxiety           |3                         |          2| 1.2375000| 1.0151414| 1.4598586|        NA|
|32 |Anxiety           |4                         |          4| 1.1112679| 0.3766830| 1.8458527|        NA|
|38 |BMI_25_30         |BMI [25-30)               |         28| 0.9880383| 0.8424838| 1.1335927|        NA|
|37 |BMI_25_30         |BMI <25                   |         43| 0.8748760| 0.7586193| 0.9911326|        NA|
|39 |BMI_25_30         |BMI >=30                  |          8| 0.9872917| 0.7379414| 1.2366419|        NA|
|21 |DASS_21           |ANXIETY                   |          3| 0.7650000| 0.3843915| 1.1456085|        NA|
|25 |DASS_21           |DEPRESSION                |          2| 0.8941667| 0.3117989| 1.4765344|        NA|
|20 |DASS_21           |NORMAL                    |         57| 0.8917047| 0.7875230| 0.9958864|        NA|
|22 |DASS_21           |STRESS                    |          4| 1.1175000| 0.6461155| 1.5888845|        NA|
|24 |DASS_21           |STRESS ANXIETY            |          4| 1.1275000| 0.8937743| 1.3612257|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |          9| 1.0325079| 0.7474459| 1.3175699|        NA|
|1  |Gender            |female                    |         34| 0.9387766| 0.8117019| 1.0658513| 0.9565689|
|2  |Gender            |male                      |         45| 0.9169926| 0.8034509| 1.0305343| 0.9565689|
|35 |Hypertension      |No                        |         58| 0.9933576| 0.9028081| 1.0839070| 0.0011700|
|36 |Hypertension      |Yes                       |         21| 0.7413492| 0.5670732| 0.9156252| 0.0011700|
|40 |Obesity           |No                        |         71| 0.9195034| 0.8299735| 1.0090333| 0.4305904|
|41 |Obesity           |Yes                       |          8| 0.9872917| 0.7379414| 1.2366419| 0.4305904|
|7  |Race              |Asian or Asian British    |         61| 0.8604055| 0.7682199| 0.9525912|        NA|
|9  |Race              |Black                     |          3| 1.2400000| 0.2349982| 2.2450018|        NA|
|8  |Race              |White                     |         15| 1.1318889| 0.9582887| 1.3054891|        NA|
|18 |Smoking           |Non smoker                |         65| 0.9576549| 0.8685247| 1.0467852| 0.1903315|
|19 |Smoking           |Smoker                    |         14| 0.7811071| 0.5528922| 1.0093220| 0.1903315|
|26 |Stress            |0                         |         62| 0.8856532| 0.7895795| 0.9817270|        NA|
|27 |Stress            |1                         |         10| 1.1252500| 0.8869014| 1.3635986|        NA|
|28 |Stress            |2                         |          3| 0.9008571| 0.0567356| 1.7449787|        NA|
|29 |Stress            |3                         |          4| 1.0793750| 0.7659677| 1.3927823|        NA|
|16 |Stress index      |No                        |         57| 0.8917047| 0.7875230| 0.9958864| 0.0606901|
|17 |Stress index      |Yes                       |         22| 1.0161775| 0.8866781| 1.1456769| 0.0606901|
|12 |Typer of skins    |1                         |         13| 1.1328846| 0.9531647| 1.3126045|        NA|
|14 |Typer of skins    |2                         |          5| 0.9160000| 0.6906371| 1.1413629|        NA|
|10 |Typer of skins    |3                         |         40| 0.7970542| 0.6808958| 0.9132125|        NA|
|11 |Typer of skins    |4                         |         11| 1.1298550| 0.8861358| 1.3735741|        NA|
|15 |Typer of skins    |5                         |          6| 0.8658333| 0.4973086| 1.2343581|        NA|
|13 |Typer of skins    |6                         |          4| 1.0925000| 0.3877809| 1.7972191|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.2490106|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.3268910|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.6128216|
|Age_stage      |Age <30                   |Age [40-50)               | 0.9096853|
|Age_stage      |Age <30                   |Age >=50                  | 0.2565033|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.3118679|
|Race           |Asian or Asian British    |White                     | 0.0074624|
|Race           |Asian or Asian British    |Black                     | 0.1018773|
|Race           |White                     |Black                     | 0.5534122|
|Typer of skins |3                         |4                         | 0.0050221|
|Typer of skins |3                         |1                         | 0.0017354|
|Typer of skins |3                         |6                         | 0.1589518|
|Typer of skins |3                         |2                         | 0.2866406|
|Typer of skins |3                         |5                         | 0.5904249|
|Typer of skins |4                         |1                         | 0.8166960|
|Typer of skins |4                         |6                         | 0.9494505|
|Typer of skins |4                         |2                         | 0.2211538|
|Typer of skins |4                         |5                         | 0.0982547|
|Typer of skins |1                         |6                         | 0.8650528|
|Typer of skins |1                         |2                         | 0.0758604|
|Typer of skins |1                         |5                         | 0.1045318|
|Typer of skins |6                         |2                         | 0.7301587|
|Typer of skins |6                         |5                         | 0.3923303|
|Typer of skins |2                         |5                         | 0.5367965|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.6964801|
|DASS_21        |NORMAL                    |STRESS                    | 0.1372776|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.2622288|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.0731451|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.6906828|
|DASS_21        |ANXIETY                   |STRESS                    | 0.0571429|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.3727273|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.0571429|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.4000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.6041958|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.8857143|
|DASS_21        |STRESS                    |DEPRESSION                | 0.2666667|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.7104895|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.9090909|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.1333333|
|Stress         |0                         |1                         | 0.0207626|
|Stress         |0                         |2                         | 0.9625930|
|Stress         |0                         |3                         | 0.1430089|
|Stress         |1                         |2                         | 0.3706294|
|Stress         |1                         |3                         | 0.8391608|
|Stress         |2                         |3                         | 0.6285714|
|Anxiety        |0                         |2                         | 0.6051898|
|Anxiety        |0                         |4                         | 0.3897474|
|Anxiety        |0                         |1                         | 0.8971684|
|Anxiety        |0                         |3                         | 0.1064164|
|Anxiety        |2                         |4                         | 0.7301587|
|Anxiety        |2                         |1                         | 0.8412698|
|Anxiety        |2                         |3                         | 0.3809524|
|Anxiety        |4                         |1                         | 0.5555556|
|Anxiety        |4                         |3                         | 1.0000000|
|Anxiety        |1                         |3                         | 0.3809524|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.2977400|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.2709728|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.8342189|


## Tạo bảng và Forest plot với biến F-E_mean

|   |Subgroup_Category |Subgroup                  | n_F-E_mean|      Mean|   CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|----------:|---------:|----------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |         33| 0.0148832|  0.0140432| 0.0157231|        NA|
|5  |Age_stage         |Age [40-50)               |         14| 0.0151702|  0.0135718| 0.0167687|        NA|
|4  |Age_stage         |Age <30                   |         26| 0.0148526|  0.0137123| 0.0159929|        NA|
|6  |Age_stage         |Age >=50                  |          6| 0.0157083|  0.0131799| 0.0182368|        NA|
|30 |Anxiety           |0                         |         63| 0.0149228|  0.0142797| 0.0155658|        NA|
|33 |Anxiety           |1                         |          5| 0.0168000|  0.0126446| 0.0209554|        NA|
|31 |Anxiety           |2                         |          5| 0.0143750|  0.0124427| 0.0163073|        NA|
|34 |Anxiety           |3                         |          2| 0.0158750|  0.0047571| 0.0269929|        NA|
|32 |Anxiety           |4                         |          4| 0.0140464|  0.0091842| 0.0189087|        NA|
|38 |BMI_25_30         |BMI [25-30)               |         28| 0.0150721|  0.0139292| 0.0162150|        NA|
|37 |BMI_25_30         |BMI <25                   |         43| 0.0148849|  0.0141374| 0.0156324|        NA|
|39 |BMI_25_30         |BMI >=30                  |          8| 0.0152344|  0.0135510| 0.0169178|        NA|
|21 |DASS_21           |ANXIETY                   |          3| 0.0146667|  0.0089298| 0.0204035|        NA|
|25 |DASS_21           |DEPRESSION                |          2| 0.0150833| -0.0113879| 0.0415546|        NA|
|20 |DASS_21           |NORMAL                    |         57| 0.0150257|  0.0143391| 0.0157124|        NA|
|22 |DASS_21           |STRESS                    |          4| 0.0133750|  0.0104427| 0.0163073|        NA|
|24 |DASS_21           |STRESS ANXIETY            |          4| 0.0146250|  0.0117656| 0.0174844|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |          9| 0.0157012|  0.0132451| 0.0181573|        NA|
|1  |Gender            |female                    |         34| 0.0148988|  0.0140248| 0.0157729| 0.6990139|
|2  |Gender            |male                      |         45| 0.0150530|  0.0142628| 0.0158431| 0.6990139|
|35 |Hypertension      |No                        |         58| 0.0150687|  0.0143976| 0.0157399| 0.6973449|
|36 |Hypertension      |Yes                       |         21| 0.0147599|  0.0135598| 0.0159600| 0.6973449|
|40 |Obesity           |No                        |         71| 0.0149587|  0.0143370| 0.0155804| 0.7448559|
|41 |Obesity           |Yes                       |          8| 0.0152344|  0.0135510| 0.0169178| 0.7448559|
|7  |Race              |Asian or Asian British    |         61| 0.0147846|  0.0140963| 0.0154729|        NA|
|9  |Race              |Black                     |          3| 0.0140000|  0.0083081| 0.0196919|        NA|
|8  |Race              |White                     |         15| 0.0160056|  0.0149907| 0.0170204|        NA|
|18 |Smoking           |Non smoker                |         65| 0.0148394|  0.0141855| 0.0154933| 0.2579447|
|19 |Smoking           |Smoker                    |         14| 0.0156702|  0.0144480| 0.0168924| 0.2579447|
|26 |Stress            |0                         |         62| 0.0150102|  0.0143642| 0.0156563|        NA|
|27 |Stress            |1                         |         10| 0.0144875|  0.0126713| 0.0163037|        NA|
|28 |Stress            |2                         |          3| 0.0175619|  0.0106000| 0.0245239|        NA|
|29 |Stress            |3                         |          4| 0.0139375|  0.0102005| 0.0176745|        NA|
|16 |Stress index      |No                        |         57| 0.0150257|  0.0143391| 0.0157124| 0.6693154|
|17 |Stress index      |Yes                       |         22| 0.0148853|  0.0137549| 0.0160158| 0.6693154|
|12 |Typer of skins    |1                         |         13| 0.0155737|  0.0146295| 0.0165180|        NA|
|14 |Typer of skins    |2                         |          5| 0.0168000|  0.0132444| 0.0203556|        NA|
|10 |Typer of skins    |3                         |         40| 0.0147700|  0.0138326| 0.0157074|        NA|
|11 |Typer of skins    |4                         |         11| 0.0145623|  0.0129008| 0.0162239|        NA|
|15 |Typer of skins    |5                         |          6| 0.0150000|  0.0131748| 0.0168252|        NA|
|13 |Typer of skins    |6                         |          4| 0.0141250|  0.0111216| 0.0171284|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.8784296|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.9072836|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.3102874|
|Age_stage      |Age <30                   |Age [40-50)               | 0.7015149|
|Age_stage      |Age <30                   |Age >=50                  | 0.3840353|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.6798239|
|Race           |Asian or Asian British    |White                     | 0.0822015|
|Race           |Asian or Asian British    |Black                     | 0.6676734|
|Race           |White                     |Black                     | 0.1717382|
|Typer of skins |3                         |4                         | 0.7136218|
|Typer of skins |3                         |1                         | 0.3409367|
|Typer of skins |3                         |6                         | 0.7280117|
|Typer of skins |3                         |2                         | 0.1686856|
|Typer of skins |3                         |5                         | 0.8316975|
|Typer of skins |4                         |1                         | 0.2107025|
|Typer of skins |4                         |6                         | 0.8958470|
|Typer of skins |4                         |2                         | 0.1558299|
|Typer of skins |4                         |5                         | 0.6139967|
|Typer of skins |1                         |6                         | 0.2115414|
|Typer of skins |1                         |2                         | 0.4008865|
|Typer of skins |1                         |5                         | 0.5374648|
|Typer of skins |6                         |2                         | 0.1904762|
|Typer of skins |6                         |5                         | 0.3923303|
|Typer of skins |2                         |5                         | 0.2722293|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.8251904|
|DASS_21        |NORMAL                    |STRESS                    | 0.1701376|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.6806136|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.7151948|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.8338348|
|DASS_21        |ANXIETY                   |STRESS                    | 0.3680655|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.7803858|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.7110254|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.7670969|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.1884438|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.3807457|
|DASS_21        |STRESS                    |DEPRESSION                | 0.8143375|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.8770350|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.9059727|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.8000000|
|Stress         |0                         |1                         | 0.3829740|
|Stress         |0                         |2                         | 0.1411050|
|Stress         |0                         |3                         | 0.3530826|
|Stress         |1                         |2                         | 0.1266154|
|Stress         |1                         |3                         | 0.9434416|
|Stress         |2                         |3                         | 0.2117984|
|Anxiety        |0                         |2                         | 0.5883490|
|Anxiety        |0                         |4                         | 0.4581124|
|Anxiety        |0                         |1                         | 0.1915358|
|Anxiety        |0                         |3                         | 0.6343778|
|Anxiety        |2                         |4                         | 0.8057008|
|Anxiety        |2                         |1                         | 0.1666074|
|Anxiety        |2                         |3                         | 0.3809524|
|Anxiety        |4                         |1                         | 0.2148469|
|Anxiety        |4                         |3                         | 0.5333333|
|Anxiety        |1                         |3                         | 0.8436689|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.8366298|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.6780857|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.8939301|

## Tạo bảng và Forest plot với biến F-N_mean

|   |Subgroup_Category |Subgroup                  | n_F-N_mean|      Mean|   CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|----------:|---------:|----------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |         33| 0.0325071|  0.0296913| 0.0353229|        NA|
|5  |Age_stage         |Age [40-50)               |         14| 0.0324595|  0.0278273| 0.0370917|        NA|
|4  |Age_stage         |Age <30                   |         26| 0.0374455|  0.0339923| 0.0408987|        NA|
|6  |Age_stage         |Age >=50                  |          6| 0.0366250|  0.0281256| 0.0451244|        NA|
|30 |Anxiety           |0                         |         63| 0.0335981|  0.0315855| 0.0356108|        NA|
|33 |Anxiety           |1                         |          5| 0.0361000|  0.0259612| 0.0462388|        NA|
|31 |Anxiety           |2                         |          5| 0.0364250|  0.0211784| 0.0516716|        NA|
|34 |Anxiety           |3                         |          2| 0.0365000| -0.0143248| 0.0873248|        NA|
|32 |Anxiety           |4                         |          4| 0.0420482|  0.0268926| 0.0572038|        NA|
|38 |BMI_25_30         |BMI [25-30)               |         28| 0.0357569|  0.0324403| 0.0390734|        NA|
|37 |BMI_25_30         |BMI <25                   |         43| 0.0338318|  0.0312964| 0.0363672|        NA|
|39 |BMI_25_30         |BMI >=30                  |          8| 0.0330677|  0.0256815| 0.0404540|        NA|
|21 |DASS_21           |ANXIETY                   |          3| 0.0391667|  0.0000004| 0.0783329|        NA|
|25 |DASS_21           |DEPRESSION                |          2| 0.0252917| -0.0101798| 0.0607632|        NA|
|20 |DASS_21           |NORMAL                    |         57| 0.0335675|  0.0314676| 0.0356675|        NA|
|22 |DASS_21           |STRESS                    |          4| 0.0381875|  0.0247506| 0.0516244|        NA|
|24 |DASS_21           |STRESS ANXIETY            |          4| 0.0402500|  0.0349925| 0.0455075|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |          9| 0.0361464|  0.0290114| 0.0432815|        NA|
|1  |Gender            |female                    |         34| 0.0343647|  0.0313047| 0.0374248| 0.6774221|
|2  |Gender            |male                      |         45| 0.0344911|  0.0320465| 0.0369357| 0.6774221|
|35 |Hypertension      |No                        |         58| 0.0347364|  0.0325900| 0.0368828| 0.6135026|
|36 |Hypertension      |Yes                       |         21| 0.0336091|  0.0294951| 0.0377232| 0.6135026|
|40 |Obesity           |No                        |         71| 0.0345910|  0.0326129| 0.0365690| 0.4595295|
|41 |Obesity           |Yes                       |          8| 0.0330677|  0.0256815| 0.0404540| 0.4595295|
|7  |Race              |Asian or Asian British    |         61| 0.0348989|  0.0326259| 0.0371720|        NA|
|9  |Race              |Black                     |          3| 0.0378333|  0.0245523| 0.0511144|        NA|
|8  |Race              |White                     |         15| 0.0318778|  0.0284948| 0.0352608|        NA|
|18 |Smoking           |Non smoker                |         65| 0.0342318|  0.0321324| 0.0363312| 0.4602425|
|19 |Smoking           |Smoker                    |         14| 0.0353881|  0.0307414| 0.0400348| 0.4602425|
|26 |Stress            |0                         |         62| 0.0335715|  0.0314514| 0.0356916|        NA|
|27 |Stress            |1                         |         10| 0.0368375|  0.0322057| 0.0414693|        NA|
|28 |Stress            |2                         |          3| 0.0344810|  0.0072693| 0.0616926|        NA|
|29 |Stress            |3                         |          4| 0.0418125|  0.0269657| 0.0566593|        NA|
|16 |Stress index      |No                        |         57| 0.0335675|  0.0314676| 0.0356675| 0.1614113|
|17 |Stress index      |Yes                       |         22| 0.0366887|  0.0325961| 0.0407813| 0.1614113|
|12 |Typer of skins    |1                         |         13| 0.0320609|  0.0288211| 0.0353006|        NA|
|14 |Typer of skins    |2                         |          5| 0.0348000|  0.0198962| 0.0497038|        NA|
|10 |Typer of skins    |3                         |         40| 0.0336067|  0.0308605| 0.0363529|        NA|
|11 |Typer of skins    |4                         |         11| 0.0366312|  0.0299479| 0.0433144|        NA|
|15 |Typer of skins    |5                         |          6| 0.0377500|  0.0297853| 0.0457147|        NA|
|13 |Typer of skins    |6                         |          4| 0.0390000|  0.0311238| 0.0468762|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.0357501|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.8706003|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.2350260|
|Age_stage      |Age <30                   |Age [40-50)               | 0.0784666|
|Age_stage      |Age <30                   |Age >=50                  | 0.9614645|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.2306654|
|Race           |Asian or Asian British    |White                     | 0.2963495|
|Race           |Asian or Asian British    |Black                     | 0.4552507|
|Race           |White                     |Black                     | 0.1384369|
|Typer of skins |3                         |4                         | 0.4705359|
|Typer of skins |3                         |1                         | 0.6417374|
|Typer of skins |3                         |6                         | 0.1413499|
|Typer of skins |3                         |2                         | 0.6386093|
|Typer of skins |3                         |5                         | 0.2150190|
|Typer of skins |4                         |1                         | 0.3389910|
|Typer of skins |4                         |6                         | 0.4325990|
|Typer of skins |4                         |2                         | 0.8649650|
|Typer of skins |4                         |5                         | 0.8075307|
|Typer of skins |1                         |6                         | 0.0539504|
|Typer of skins |1                         |2                         | 0.7028478|
|Typer of skins |1                         |5                         | 0.1244894|
|Typer of skins |6                         |2                         | 0.7121545|
|Typer of skins |6                         |5                         | 0.9148486|
|Typer of skins |2                         |5                         | 0.9307359|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.4154479|
|DASS_21        |NORMAL                    |STRESS                    | 0.3819012|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.3696264|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.0730426|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.1261714|
|DASS_21        |ANXIETY                   |STRESS                    | 0.8571429|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.7105631|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.8571429|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.8000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.9398601|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.5613632|
|DASS_21        |STRESS                    |DEPRESSION                | 0.1333333|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.2601399|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.1454545|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.1333333|
|Stress         |0                         |1                         | 0.2097798|
|Stress         |0                         |2                         | 0.8634180|
|Stress         |0                         |3                         | 0.0695913|
|Stress         |1                         |2                         | 1.0000000|
|Stress         |1                         |3                         | 0.2288198|
|Stress         |2                         |3                         | 0.6285714|
|Anxiety        |0                         |2                         | 0.5969255|
|Anxiety        |0                         |4                         | 0.0783444|
|Anxiety        |0                         |1                         | 0.3844683|
|Anxiety        |0                         |3                         | 0.4139470|
|Anxiety        |2                         |4                         | 0.5555556|
|Anxiety        |2                         |1                         | 1.0000000|
|Anxiety        |2                         |3                         | 0.8571429|
|Anxiety        |4                         |1                         | 0.6227533|
|Anxiety        |4                         |3                         | 0.8000000|
|Anxiety        |1                         |3                         | 1.0000000|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.2560397|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.5952784|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.3511150|


## Tạo bảng và Forest plot với biến F-M_mean

|   |Subgroup_Category |Subgroup                  | n_F-M_mean|      Mean|   CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|----------:|---------:|----------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |         33| 0.0780331|  0.0701771| 0.0858891|        NA|
|5  |Age_stage         |Age [40-50)               |         14| 0.0815310|  0.0692610| 0.0938009|        NA|
|4  |Age_stage         |Age <30                   |         26| 0.0849519|  0.0741573| 0.0957466|        NA|
|6  |Age_stage         |Age >=50                  |          6| 0.0866806|  0.0575458| 0.1158153|        NA|
|30 |Anxiety           |0                         |         63| 0.0818971|  0.0756860| 0.0881082|        NA|
|33 |Anxiety           |1                         |          5| 0.0798000|  0.0635833| 0.0960167|        NA|
|31 |Anxiety           |2                         |          5| 0.0767000|  0.0573066| 0.0960934|        NA|
|34 |Anxiety           |3                         |          2| 0.0706250| -0.0326129| 0.1738629|        NA|
|32 |Anxiety           |4                         |          4| 0.0905232|  0.0327555| 0.1482909|        NA|
|38 |BMI_25_30         |BMI [25-30)               |         28| 0.0798009|  0.0709299| 0.0886719|        NA|
|37 |BMI_25_30         |BMI <25                   |         43| 0.0841380|  0.0761726| 0.0921034|        NA|
|39 |BMI_25_30         |BMI >=30                  |          8| 0.0741250|  0.0637707| 0.0844793|        NA|
|21 |DASS_21           |ANXIETY                   |          3| 0.0748333|  0.0246818| 0.1249848|        NA|
|25 |DASS_21           |DEPRESSION                |          2| 0.0678750| -0.0194802| 0.1552302|        NA|
|20 |DASS_21           |NORMAL                    |         57| 0.0834915|  0.0767597| 0.0902234|        NA|
|22 |DASS_21           |STRESS                    |          4| 0.0661875|  0.0601337| 0.0722413|        NA|
|24 |DASS_21           |STRESS ANXIETY            |          4| 0.0783750|  0.0591880| 0.0975620|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |          9| 0.0830937|  0.0638975| 0.1022898|        NA|
|1  |Gender            |female                    |         34| 0.0822111|  0.0737556| 0.0906665| 0.6729848|
|2  |Gender            |male                      |         45| 0.0811152|  0.0739894| 0.0882409| 0.6729848|
|35 |Hypertension      |No                        |         58| 0.0795881|  0.0738570| 0.0853192| 0.5404319|
|36 |Hypertension      |Yes                       |         21| 0.0871071|  0.0741505| 0.1000638| 0.5404319|
|40 |Obesity           |No                        |         71| 0.0824276|  0.0765894| 0.0882658| 0.6896596|
|41 |Obesity           |Yes                       |          8| 0.0741250|  0.0637707| 0.0844793| 0.6896596|
|7  |Race              |Asian or Asian British    |         61| 0.0836521|  0.0772053| 0.0900988|        NA|
|9  |Race              |Black                     |          3| 0.0630000|  0.0573081| 0.0686919|        NA|
|8  |Race              |White                     |         15| 0.0769056|  0.0669738| 0.0868373|        NA|
|18 |Smoking           |Non smoker                |         65| 0.0794989|  0.0740052| 0.0849925| 0.2023817|
|19 |Smoking           |Smoker                    |         14| 0.0912810|  0.0744115| 0.1081504| 0.2023817|
|26 |Stress            |0                         |         62| 0.0825688|  0.0762625| 0.0888751|        NA|
|27 |Stress            |1                         |         10| 0.0697750|  0.0641749| 0.0753751|        NA|
|28 |Stress            |2                         |          3| 0.1047810|  0.0170408| 0.1925212|        NA|
|29 |Stress            |3                         |          4| 0.0785000|  0.0604652| 0.0965348|        NA|
|16 |Stress index      |No                        |         57| 0.0834915|  0.0767597| 0.0902234| 0.5536230|
|17 |Stress index      |Yes                       |         22| 0.0766519|  0.0683482| 0.0849557| 0.5536230|
|12 |Typer of skins    |1                         |         13| 0.0766987|  0.0660323| 0.0873651|        NA|
|14 |Typer of skins    |2                         |          5| 0.0690000|  0.0488492| 0.0891508|        NA|
|10 |Typer of skins    |3                         |         40| 0.0845358|  0.0765351| 0.0925366|        NA|
|11 |Typer of skins    |4                         |         11| 0.0770539|  0.0637053| 0.0904025|        NA|
|15 |Typer of skins    |5                         |          6| 0.0903750|  0.0605113| 0.1202387|        NA|
|13 |Typer of skins    |6                         |          4| 0.0830000|  0.0192815| 0.1467185|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.3779267|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.2485226|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.4828568|
|Age_stage      |Age <30                   |Age [40-50)               | 1.0000000|
|Age_stage      |Age <30                   |Age >=50                  | 0.9419530|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.9014649|
|Race           |Asian or Asian British    |White                     | 0.6898204|
|Race           |Asian or Asian British    |Black                     | 0.0715067|
|Race           |White                     |Black                     | 0.1221770|
|Typer of skins |3                         |4                         | 0.3458901|
|Typer of skins |3                         |1                         | 0.5902133|
|Typer of skins |3                         |6                         | 0.4239510|
|Typer of skins |3                         |2                         | 0.1060453|
|Typer of skins |3                         |5                         | 0.6349394|
|Typer of skins |4                         |1                         | 0.7498334|
|Typer of skins |4                         |6                         | 0.6465253|
|Typer of skins |4                         |2                         | 0.2775400|
|Typer of skins |4                         |5                         | 0.3917856|
|Typer of skins |1                         |6                         | 0.4609176|
|Typer of skins |1                         |2                         | 0.0927726|
|Typer of skins |1                         |5                         | 0.3568859|
|Typer of skins |6                         |2                         | 0.5261685|
|Typer of skins |6                         |5                         | 0.5211659|
|Typer of skins |2                         |5                         | 0.1660106|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.5069437|
|DASS_21        |NORMAL                    |STRESS                    | 0.1439012|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.6940471|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.6402549|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.3661630|
|DASS_21        |ANXIETY                   |STRESS                    | 1.0000000|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.5770953|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.8571429|
|DASS_21        |ANXIETY                   |DEPRESSION                | 1.0000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.0887518|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.2000000|
|DASS_21        |STRESS                    |DEPRESSION                | 1.0000000|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.8167139|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.4774915|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.2666667|
|Stress         |0                         |1                         | 0.2458292|
|Stress         |0                         |2                         | 0.1321247|
|Stress         |0                         |3                         | 0.5712657|
|Stress         |1                         |2                         | 0.0341146|
|Stress         |1                         |3                         | 0.1781525|
|Stress         |2                         |3                         | 0.4000000|
|Anxiety        |0                         |2                         | 0.9435969|
|Anxiety        |0                         |4                         | 0.5500392|
|Anxiety        |0                         |1                         | 0.5018217|
|Anxiety        |0                         |3                         | 0.7896106|
|Anxiety        |2                         |4                         | 0.8057008|
|Anxiety        |2                         |1                         | 0.5283593|
|Anxiety        |2                         |3                         | 0.8571429|
|Anxiety        |4                         |1                         | 1.0000000|
|Anxiety        |4                         |3                         | 0.8000000|
|Anxiety        |1                         |3                         | 0.5714286|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.4788044|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.5502094|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.9695549|


## Tạo bảng và Forest plot với biến F-R_mean

|   |Subgroup_Category |Subgroup                  | n_F-R_mean|      Mean|   CI_lower|  CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|----------:|---------:|----------:|---------:|---------:|
|3  |Age_stage         |Age [30-40)               |         33| 0.3298952|  0.2963657| 0.3634247|        NA|
|5  |Age_stage         |Age [40-50)               |         14| 0.3646333|  0.3060989| 0.4231678|        NA|
|4  |Age_stage         |Age <30                   |         26| 0.2850160|  0.2392095| 0.3308226|        NA|
|6  |Age_stage         |Age >=50                  |          6| 0.3829444|  0.3181712| 0.4477177|        NA|
|30 |Anxiety           |0                         |         63| 0.3184741|  0.2942526| 0.3426956|        NA|
|33 |Anxiety           |1                         |          5| 0.3470000|  0.1824713| 0.5115287|        NA|
|31 |Anxiety           |2                         |          5| 0.3977750|  0.2187519| 0.5767981|        NA|
|34 |Anxiety           |3                         |          2| 0.2726250| -0.2117991| 0.7570491|        NA|
|32 |Anxiety           |4                         |          4| 0.3416250|  0.0869188| 0.5963312|        NA|
|38 |BMI_25_30         |BMI [25-30)               |         28| 0.3414762|  0.3008319| 0.3821205|        NA|
|37 |BMI_25_30         |BMI <25                   |         43| 0.3081384|  0.2771944| 0.3390824|        NA|
|39 |BMI_25_30         |BMI >=30                  |          8| 0.3610260|  0.2644824| 0.4575697|        NA|
|21 |DASS_21           |ANXIETY                   |          3| 0.5103333|  0.3666322| 0.6540345|        NA|
|25 |DASS_21           |DEPRESSION                |          2| 0.3380833| -1.1368953| 1.8130619|        NA|
|20 |DASS_21           |NORMAL                    |         57| 0.3212140|  0.2959425| 0.3464855|        NA|
|22 |DASS_21           |STRESS                    |          4| 0.2696250|  0.1164546| 0.4227954|        NA|
|24 |DASS_21           |STRESS ANXIETY            |          4| 0.3051250|  0.1480817| 0.4621683|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |          9| 0.3204583|  0.2232571| 0.4176596|        NA|
|1  |Gender            |female                    |         34| 0.3165380|  0.2783456| 0.3547303| 0.2934331|
|2  |Gender            |male                      |         45| 0.3319378|  0.3017300| 0.3621455| 0.2934331|
|35 |Hypertension      |No                        |         58| 0.3073555|  0.2825425| 0.3321684| 0.0136383|
|36 |Hypertension      |Yes                       |         21| 0.3748988|  0.3223180| 0.4274796| 0.0136383|
|40 |Obesity           |No                        |         71| 0.3212857|  0.2969474| 0.3456239| 0.3999399|
|41 |Obesity           |Yes                       |          8| 0.3610260|  0.2644824| 0.4575697| 0.3999399|
|7  |Race              |Asian or Asian British    |         61| 0.3293209|  0.3020468| 0.3565950|        NA|
|9  |Race              |Black                     |          3| 0.3523333|  0.0254041| 0.6792626|        NA|
|8  |Race              |White                     |         15| 0.3035944|  0.2524357| 0.3547532|        NA|
|18 |Smoking           |Non smoker                |         65| 0.3200942|  0.2942955| 0.3458930| 0.2752173|
|19 |Smoking           |Smoker                    |         14| 0.3495262|  0.2893817| 0.4096707| 0.2752173|
|26 |Stress            |0                         |         62| 0.3309091|  0.3048223| 0.3569960|        NA|
|27 |Stress            |1                         |         10| 0.2799375|  0.2165368| 0.3433382|        NA|
|28 |Stress            |2                         |          3| 0.4083333| -0.0368082| 0.8534748|        NA|
|29 |Stress            |3                         |          4| 0.2896875|  0.1666626| 0.4127124|        NA|
|16 |Stress index      |No                        |         57| 0.3212140|  0.2959425| 0.3464855| 0.7455609|
|17 |Stress index      |Yes                       |         22| 0.3359223|  0.2800583| 0.3917864| 0.7455609|
|12 |Typer of skins    |1                         |         13| 0.3011763|  0.2505336| 0.3518190|        NA|
|14 |Typer of skins    |2                         |          5| 0.3417000|  0.2064444| 0.4769556|        NA|
|10 |Typer of skins    |3                         |         40| 0.3295071|  0.2970577| 0.3619565|        NA|
|11 |Typer of skins    |4                         |         11| 0.3235606|  0.2326381| 0.4144832|        NA|
|15 |Typer of skins    |5                         |          6| 0.2887083|  0.2148959| 0.3625207|        NA|
|13 |Typer of skins    |6                         |          4| 0.4010000|  0.1702964| 0.6317036|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.0542286|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.2974146|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.2645738|
|Age_stage      |Age <30                   |Age [40-50)               | 0.0331639|
|Age_stage      |Age <30                   |Age >=50                  | 0.0236520|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.8688310|
|Race           |Asian or Asian British    |White                     | 0.2676100|
|Race           |Asian or Asian British    |Black                     | 0.8857982|
|Race           |White                     |Black                     | 0.5460639|
|Typer of skins |3                         |4                         | 0.7040141|
|Typer of skins |3                         |1                         | 0.1419300|
|Typer of skins |3                         |6                         | 0.3661353|
|Typer of skins |3                         |2                         | 0.8701516|
|Typer of skins |3                         |5                         | 0.4221199|
|Typer of skins |4                         |1                         | 0.8826892|
|Typer of skins |4                         |6                         | 0.5100891|
|Typer of skins |4                         |2                         | 0.6086082|
|Typer of skins |4                         |5                         | 0.9598232|
|Typer of skins |1                         |6                         | 0.1477178|
|Typer of skins |1                         |2                         | 0.2722117|
|Typer of skins |1                         |5                         | 1.0000000|
|Typer of skins |6                         |2                         | 0.7086241|
|Typer of skins |6                         |5                         | 0.2849576|
|Typer of skins |2                         |5                         | 0.3108629|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.0078696|
|DASS_21        |NORMAL                    |STRESS                    | 0.4462744|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.7350267|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.6814605|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.6585615|
|DASS_21        |ANXIETY                   |STRESS                    | 0.0571429|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.0625935|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.0497460|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.2000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.7543299|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 1.0000000|
|DASS_21        |STRESS                    |DEPRESSION                | 0.5333333|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 1.0000000|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.9053250|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.8143375|
|Stress         |0                         |1                         | 0.1176681|
|Stress         |0                         |2                         | 0.3708397|
|Stress         |0                         |3                         | 0.6177461|
|Stress         |1                         |2                         | 0.2577040|
|Stress         |1                         |3                         | 0.6151259|
|Stress         |2                         |3                         | 0.6285714|
|Anxiety        |0                         |2                         | 0.2670477|
|Anxiety        |0                         |4                         | 0.9047157|
|Anxiety        |0                         |1                         | 0.7676541|
|Anxiety        |0                         |3                         | 0.7169853|
|Anxiety        |2                         |4                         | 0.7109920|
|Anxiety        |2                         |1                         | 0.5958831|
|Anxiety        |2                         |3                         | 0.3809524|
|Anxiety        |4                         |1                         | 1.0000000|
|Anxiety        |4                         |3                         | 1.0000000|
|Anxiety        |1                         |3                         | 0.8450785|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.1084364|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.2444964|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.8043432|


## Tạo bảng và Forest plot với biến F-C_mean

|   |Subgroup_Category |Subgroup                  | n_F-C_mean|     Mean|   CI_lower| CI_upper|   P_Value|
|:--|:-----------------|:-------------------------|----------:|--------:|----------:|--------:|---------:|
|3  |Age_stage         |Age [30-40)               |         33| 1.167598|  1.1170159| 1.218180|        NA|
|5  |Age_stage         |Age [40-50)               |         14| 1.135479|  1.0289407| 1.242016|        NA|
|4  |Age_stage         |Age <30                   |         26| 1.121894|  1.0489713| 1.194817|        NA|
|6  |Age_stage         |Age >=50                  |          6| 1.026972|  0.8094663| 1.244478|        NA|
|30 |Anxiety           |0                         |         63| 1.139191|  1.0949107| 1.183471|        NA|
|33 |Anxiety           |1                         |          5| 1.031900|  0.9085805| 1.155220|        NA|
|31 |Anxiety           |2                         |          5| 1.153325|  0.9464807| 1.360169|        NA|
|34 |Anxiety           |3                         |          2| 1.198375| -0.9410322| 3.337782|        NA|
|32 |Anxiety           |4                         |          4| 1.166650|  0.9800513| 1.353249|        NA|
|38 |BMI_25_30         |BMI [25-30)               |         28| 1.115498|  1.0580494| 1.172946|        NA|
|37 |BMI_25_30         |BMI <25                   |         43| 1.141937|  1.0861733| 1.197700|        NA|
|39 |BMI_25_30         |BMI >=30                  |          8| 1.177661|  1.0247484| 1.330574|        NA|
|21 |DASS_21           |ANXIETY                   |          3| 1.085833|  0.8242478| 1.347419|        NA|
|25 |DASS_21           |DEPRESSION                |          2| 1.007375| -0.6269606| 2.641711|        NA|
|20 |DASS_21           |NORMAL                    |         57| 1.144224|  1.0967846| 1.191664|        NA|
|22 |DASS_21           |STRESS                    |          4| 1.133375|  0.9138406| 1.352909|        NA|
|24 |DASS_21           |STRESS ANXIETY            |          4| 0.997625|  0.8379053| 1.157345|        NA|
|23 |DASS_21           |STRESS ANXIETY DEPRESSION |          9| 1.193497|  1.0884740| 1.298520|        NA|
|1  |Gender            |female                    |         34| 1.129004|  1.0700456| 1.187963| 0.9368096|
|2  |Gender            |male                      |         45| 1.141608|  1.0902144| 1.193002| 0.9368096|
|35 |Hypertension      |No                        |         58| 1.122861|  1.0826914| 1.163032| 0.1280938|
|36 |Hypertension      |Yes                       |         21| 1.172978|  1.0783786| 1.267578| 0.1280938|
|40 |Obesity           |No                        |         71| 1.131510|  1.0916674| 1.171353| 0.3753868|
|41 |Obesity           |Yes                       |          8| 1.177661|  1.0247484| 1.330574| 0.3753868|
|7  |Race              |Asian or Asian British    |         61| 1.153603|  1.1091798| 1.198025|        NA|
|9  |Race              |Black                     |          3| 1.111500|  0.8641224| 1.358878|        NA|
|8  |Race              |White                     |         15| 1.070283|  0.9862346| 1.154332|        NA|
|18 |Smoking           |Non smoker                |         65| 1.121989|  1.0812269| 1.162752| 0.2221834|
|19 |Smoking           |Smoker                    |         14| 1.202086|  1.0974389| 1.306733| 0.2221834|
|26 |Stress            |0                         |         62| 1.136984|  1.0922855| 1.181683|        NA|
|27 |Stress            |1                         |         10| 1.102963|  0.9882734| 1.217652|        NA|
|28 |Stress            |2                         |          3| 1.188533|  0.9026340| 1.474433|        NA|
|29 |Stress            |3                         |          4| 1.167563|  0.9387396| 1.396385|        NA|
|16 |Stress index      |No                        |         57| 1.144224|  1.0967846| 1.191664| 0.5148447|
|17 |Stress index      |Yes                       |         22| 1.115351|  1.0519382| 1.178764| 0.5148447|
|12 |Typer of skins    |1                         |         13| 1.097644|  0.9887242| 1.206564|        NA|
|14 |Typer of skins    |2                         |          5| 1.135200|  1.0326080| 1.237792|        NA|
|10 |Typer of skins    |3                         |         40| 1.136161|  1.0796270| 1.192695|        NA|
|11 |Typer of skins    |4                         |         11| 1.122721|  1.0593569| 1.186086|        NA|
|15 |Typer of skins    |5                         |          6| 1.227625|  0.9373798| 1.517870|        NA|
|13 |Typer of skins    |6                         |          4| 1.162750|  0.9545646| 1.370935|        NA|
###Wilcox pairwise test cho các sub group có >2 level

```
## Group Gender does not have more than 2 unique levels. Skipping.
```

```
## Group Stress index does not have more than 2 unique levels. Skipping.
```

```
## Group Smoking does not have more than 2 unique levels. Skipping.
```

```
## Group Hypertension does not have more than 2 unique levels. Skipping.
```

```
## Group Obesity does not have more than 2 unique levels. Skipping.
```



|Group          |Group1                    |Group2                    |   P_Value|
|:--------------|:-------------------------|:-------------------------|---------:|
|Age_stage      |Age [30-40)               |Age <30                   | 0.2743406|
|Age_stage      |Age [30-40)               |Age [40-50)               | 0.3884978|
|Age_stage      |Age [30-40)               |Age >=50                  | 0.0827614|
|Age_stage      |Age <30                   |Age [40-50)               | 0.8759498|
|Age_stage      |Age <30                   |Age >=50                  | 0.3843847|
|Age_stage      |Age [40-50)               |Age >=50                  | 0.2149831|
|Race           |Asian or Asian British    |White                     | 0.0582146|
|Race           |Asian or Asian British    |Black                     | 0.5778788|
|Race           |White                     |Black                     | 0.5532072|
|Typer of skins |3                         |4                         | 0.7135907|
|Typer of skins |3                         |1                         | 0.5345167|
|Typer of skins |3                         |6                         | 0.6675528|
|Typer of skins |3                         |2                         | 0.8991698|
|Typer of skins |3                         |5                         | 0.1968083|
|Typer of skins |4                         |1                         | 0.4007612|
|Typer of skins |4                         |6                         | 0.5135147|
|Typer of skins |4                         |2                         | 0.9096697|
|Typer of skins |4                         |5                         | 0.1801875|
|Typer of skins |1                         |6                         | 0.5710636|
|Typer of skins |1                         |2                         | 0.4594955|
|Typer of skins |1                         |5                         | 0.2192893|
|Typer of skins |6                         |2                         | 1.0000000|
|Typer of skins |6                         |5                         | 0.4761905|
|Typer of skins |2                         |5                         | 0.2467532|
|DASS_21        |NORMAL                    |ANXIETY                   | 0.5078503|
|DASS_21        |NORMAL                    |STRESS                    | 0.9534812|
|DASS_21        |NORMAL                    |STRESS ANXIETY DEPRESSION | 0.3545399|
|DASS_21        |NORMAL                    |STRESS ANXIETY            | 0.0752199|
|DASS_21        |NORMAL                    |DEPRESSION                | 0.2849571|
|DASS_21        |ANXIETY                   |STRESS                    | 0.7212767|
|DASS_21        |ANXIETY                   |STRESS ANXIETY DEPRESSION | 0.2818182|
|DASS_21        |ANXIETY                   |STRESS ANXIETY            | 0.4755327|
|DASS_21        |ANXIETY                   |DEPRESSION                | 0.8000000|
|DASS_21        |STRESS                    |STRESS ANXIETY DEPRESSION | 0.5365338|
|DASS_21        |STRESS                    |STRESS ANXIETY            | 0.2453835|
|DASS_21        |STRESS                    |DEPRESSION                | 0.5333333|
|DASS_21        |STRESS ANXIETY DEPRESSION |STRESS ANXIETY            | 0.0445685|
|DASS_21        |STRESS ANXIETY DEPRESSION |DEPRESSION                | 0.2181818|
|DASS_21        |STRESS ANXIETY            |DEPRESSION                | 0.8000000|
|Stress         |0                         |1                         | 0.5962763|
|Stress         |0                         |2                         | 0.5416853|
|Stress         |0                         |3                         | 0.7673080|
|Stress         |1                         |2                         | 0.3518798|
|Stress         |1                         |3                         | 0.3558476|
|Stress         |2                         |3                         | 1.0000000|
|Anxiety        |0                         |2                         | 0.8231545|
|Anxiety        |0                         |4                         | 0.6620936|
|Anxiety        |0                         |1                         | 0.1124105|
|Anxiety        |0                         |3                         | 0.6077261|
|Anxiety        |2                         |4                         | 1.0000000|
|Anxiety        |2                         |1                         | 0.4019654|
|Anxiety        |2                         |3                         | 0.5577377|
|Anxiety        |4                         |1                         | 0.1111111|
|Anxiety        |4                         |3                         | 1.0000000|
|Anxiety        |1                         |3                         | 0.5714286|
|BMI_25_30      |BMI <25                   |BMI [25-30)               | 0.8183524|
|BMI_25_30      |BMI <25                   |BMI >=30                  | 0.5003727|
|BMI_25_30      |BMI [25-30)               |BMI >=30                  | 0.2861549|



