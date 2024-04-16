---
title: "Phân tích mô tả các subgroup"
author: "Minh"
date: "2024-02-28"
output:
  html_document:
    keep_md: yes
  word_document: default
  pdf_document: default
params:
  warning: no
---




```r
options(warn = -1)
```

## Load bộ số liệu và các packages


```r
library(tidyverse)
library(gtsummary)
library(rstatix)
library(readxl)
library(boot)
library(forestplot)
d <- read_excel("C:/Users/Admin/OneDrive/NC_Quangpho/Data_regardless_sleep_18_03.xlsx")
View(d)

d$BMI_25_30 <- ifelse(d$BMI_index < 25, 1, 
                         ifelse(d$BMI_index >= 25 & d$BMI_index < 30, 2, 3))
d$Age_stage <- ifelse(d$Age <= 30, 1, 
                         ifelse(d$Age >= 30 & d$Age < 40, 2, ifelse(d$Age >= 40 & d$Age < 50, 3,4)))
d$Gender <- ifelse(d$Gender == 0, "female", ifelse(d$Gender == 1, "male", NA))
d$Race <- d$`6. Race`
d <- d %>%
  mutate(Age_stage = case_when(
    Age_stage == 1 ~ "Age <30",
    Age_stage == 2 ~ "Age [30-40)",
    Age_stage == 3 ~ "Age [40-50)",
    Age_stage == 4 ~ "Age >=50",
    TRUE ~ NA_character_  # This line handles any unexpected values
  ))
d$Hypertension <- ifelse(d$Hypertension == 0, "No", ifelse(d$Hypertension == 1, "Yes", NA))
d$`Stress index` <- ifelse(d$`Stress index` == 0, "No", ifelse(d$`Stress index` == 1, "Yes", NA))
d$Obesity <- ifelse(d$Obesity == 0, "No", ifelse(d$Obesity == 1, "Yes", NA))
d <- d %>%
  mutate(BMI_25_30 = case_when(
    BMI_25_30 == 1 ~ "BMI <25",
    BMI_25_30 == 2 ~ "BMI [25-30)",
    BMI_25_30 == 3 ~ "BMI >=30",
    TRUE ~ NA_character_  # This line handles any unexpected values
  ))
d$Smoking <- ifelse(d$Smoking == "Do not smoke", "Non smoker", ifelse(d$Smoking == "Cigarettes, pipe tobacco...", "Smoker", NA))
```



```r
variables <- c("M_mean", "Kv100_mean", "δ_mean", "T_mean", "A365_mean", "A460_mean", "Anadn_mean", "POM_mean", "A-E_mean", "A-N_mean", "A-M_mean", "A-R_mean", "A-C_mean", "F-E_mean", "F-N_mean", "F-M_mean", "F-R_mean", "F-C_mean")

subgroups <- c("Gender", "Age_stage", "Race", "Typer of skins", "Stress index", "Smoking", "Hypertension","BMI_25_30", "Obesity")
```


```r
Tab1 <- d %>% select("Gender", "Age_stage", "Race", "Typer of skins", "Stress index", "Smoking", "Hypertension","BMI_25_30", "Obesity") %>% 
  tbl_summary(
    digits = list(all_categorical() ~ c(0, 1))
  )
Tab1
```

```{=html}
<div id="gxaopqchpd" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#gxaopqchpd table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#gxaopqchpd thead, #gxaopqchpd tbody, #gxaopqchpd tfoot, #gxaopqchpd tr, #gxaopqchpd td, #gxaopqchpd th {
  border-style: none;
}

#gxaopqchpd p {
  margin: 0;
  padding: 0;
}

#gxaopqchpd .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#gxaopqchpd .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#gxaopqchpd .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#gxaopqchpd .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#gxaopqchpd .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gxaopqchpd .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gxaopqchpd .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gxaopqchpd .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#gxaopqchpd .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#gxaopqchpd .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#gxaopqchpd .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#gxaopqchpd .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#gxaopqchpd .gt_spanner_row {
  border-bottom-style: hidden;
}

#gxaopqchpd .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#gxaopqchpd .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#gxaopqchpd .gt_from_md > :first-child {
  margin-top: 0;
}

#gxaopqchpd .gt_from_md > :last-child {
  margin-bottom: 0;
}

#gxaopqchpd .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#gxaopqchpd .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#gxaopqchpd .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#gxaopqchpd .gt_row_group_first td {
  border-top-width: 2px;
}

#gxaopqchpd .gt_row_group_first th {
  border-top-width: 2px;
}

#gxaopqchpd .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gxaopqchpd .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#gxaopqchpd .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#gxaopqchpd .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gxaopqchpd .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gxaopqchpd .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#gxaopqchpd .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}

#gxaopqchpd .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#gxaopqchpd .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gxaopqchpd .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gxaopqchpd .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#gxaopqchpd .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gxaopqchpd .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#gxaopqchpd .gt_left {
  text-align: left;
}

#gxaopqchpd .gt_center {
  text-align: center;
}

#gxaopqchpd .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#gxaopqchpd .gt_font_normal {
  font-weight: normal;
}

#gxaopqchpd .gt_font_bold {
  font-weight: bold;
}

#gxaopqchpd .gt_font_italic {
  font-style: italic;
}

#gxaopqchpd .gt_super {
  font-size: 65%;
}

#gxaopqchpd .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}

#gxaopqchpd .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#gxaopqchpd .gt_indent_1 {
  text-indent: 5px;
}

#gxaopqchpd .gt_indent_2 {
  text-indent: 10px;
}

#gxaopqchpd .gt_indent_3 {
  text-indent: 15px;
}

#gxaopqchpd .gt_indent_4 {
  text-indent: 20px;
}

#gxaopqchpd .gt_indent_5 {
  text-indent: 25px;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="&lt;strong&gt;Characteristic&lt;/strong&gt;"><strong>Characteristic</strong></th>
      <th class="gt_col_heading gt_columns_bottom_border gt_center" rowspan="1" colspan="1" scope="col" id="&lt;strong&gt;N = 79&lt;/strong&gt;&lt;span class=&quot;gt_footnote_marks&quot; style=&quot;white-space:nowrap;font-style:italic;font-weight:normal;&quot;&gt;&lt;sup&gt;1&lt;/sup&gt;&lt;/span&gt;"><strong>N = 79</strong><span class="gt_footnote_marks" style="white-space:nowrap;font-style:italic;font-weight:normal;"><sup>1</sup></span></th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="label" class="gt_row gt_left">Gender</td>
<td headers="stat_0" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    female</td>
<td headers="stat_0" class="gt_row gt_center">34 (43.0%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    male</td>
<td headers="stat_0" class="gt_row gt_center">45 (57.0%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Age_stage</td>
<td headers="stat_0" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Age [30-40)</td>
<td headers="stat_0" class="gt_row gt_center">33 (41.8%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Age [40-50)</td>
<td headers="stat_0" class="gt_row gt_center">14 (17.7%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Age &lt;30</td>
<td headers="stat_0" class="gt_row gt_center">26 (32.9%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Age &gt;=50</td>
<td headers="stat_0" class="gt_row gt_center">6 (7.6%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Race</td>
<td headers="stat_0" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Asian or Asian British</td>
<td headers="stat_0" class="gt_row gt_center">61 (77.2%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Black</td>
<td headers="stat_0" class="gt_row gt_center">3 (3.8%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    White</td>
<td headers="stat_0" class="gt_row gt_center">15 (19.0%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Typer of skins</td>
<td headers="stat_0" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    1</td>
<td headers="stat_0" class="gt_row gt_center">13 (16.5%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    2</td>
<td headers="stat_0" class="gt_row gt_center">5 (6.3%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    3</td>
<td headers="stat_0" class="gt_row gt_center">40 (50.6%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    4</td>
<td headers="stat_0" class="gt_row gt_center">11 (13.9%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    5</td>
<td headers="stat_0" class="gt_row gt_center">6 (7.6%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    6</td>
<td headers="stat_0" class="gt_row gt_center">4 (5.1%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Stress index</td>
<td headers="stat_0" class="gt_row gt_center">22 (27.8%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Smoking</td>
<td headers="stat_0" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Non smoker</td>
<td headers="stat_0" class="gt_row gt_center">65 (82.3%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    Smoker</td>
<td headers="stat_0" class="gt_row gt_center">14 (17.7%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Hypertension</td>
<td headers="stat_0" class="gt_row gt_center">21 (26.6%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">BMI_25_30</td>
<td headers="stat_0" class="gt_row gt_center"><br /></td></tr>
    <tr><td headers="label" class="gt_row gt_left">    BMI [25-30)</td>
<td headers="stat_0" class="gt_row gt_center">28 (35.4%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    BMI &lt;25</td>
<td headers="stat_0" class="gt_row gt_center">43 (54.4%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">    BMI &gt;=30</td>
<td headers="stat_0" class="gt_row gt_center">8 (10.1%)</td></tr>
    <tr><td headers="label" class="gt_row gt_left">Obesity</td>
<td headers="stat_0" class="gt_row gt_center">8 (10.1%)</td></tr>
  </tbody>
  
  <tfoot class="gt_footnotes">
    <tr>
      <td class="gt_footnote" colspan="2"><span class="gt_footnote_marks" style="white-space:nowrap;font-style:italic;font-weight:normal;"><sup>1</sup></span> n (%)</td>
    </tr>
  </tfoot>
</table>
</div>
```



```r
library(dplyr)
library(tidyr)
library(purrr)

describe_subgroup <- function(data, subgroup, variables) {
  # Convert list columns to numeric if they are meant to be included in the variables
  for (variable in variables) {
    if (is.list(data[[variable]])) {
      data[[variable]] <- unlist(data[[variable]])
    }
  }
  
  map_dfr(variables, function(variable) {
    data %>%
      group_by(.data[[subgroup]]) %>%
      summarise(
        subgroup = subgroup,
        variable = variable,
        mean = mean(.data[[variable]], na.rm = TRUE),
        CI_lower = quantile(.data[[variable]], probs = 0.025, na.rm = TRUE),
        CI_upper = quantile(.data[[variable]], probs = 0.975, na.rm = TRUE),
        .groups = 'drop'
      ) %>%
      mutate(mean_CI = sprintf("%s (%s - %s)", round(mean, 2), round(CI_lower, 2), round(CI_upper, 2))) %>%
      select(-mean, -CI_lower, -CI_upper)
  }) %>%
  pivot_wider(names_from = variable, values_from = mean_CI, names_sep = "_") %>%
  select(subgroup, everything()) %>% rename_at(2, ~ "Level") %>% mutate(Level = as.character(Level))
}



variables <- c("M_mean", "Kv100_mean", "δ_mean", "T_mean", "A365_mean", "A460_mean", "Anadn_mean", "POM_mean", "A-E_mean", "A-N_mean", "A-M_mean", "A-R_mean", "A-C_mean", "F-E_mean", "F-N_mean", "F-M_mean", "F-R_mean", "F-C_mean")

subgroups <- c("Gender", "Age_stage", "Race", "Typer of skins", "Stress index", "Smoking", "Hypertension","BMI_25_30", "Obesity")

describe_subgroup(d, "Age_stage",variables)
```

```
## # A tibble: 4 × 20
##   subgroup  Level M_mean Kv100_mean δ_mean T_mean A365_mean A460_mean Anadn_mean
##   <chr>     <chr> <chr>  <chr>      <chr>  <chr>  <chr>     <chr>     <chr>     
## 1 Age_stage Age … 19.42… 25.59 (7.… 3.87 … 30.53… 81.03 (2… 51.75 (1… 1.06 (0.4…
## 2 Age_stage Age … 18.3 … 28.59 (9.… 4.25 … 29.58… 84.81 (3… 57.83 (1… 0.77 (0.5…
## 3 Age_stage Age … 25.23… 19.9 (6.3… 4.46 … 32.21… 95.88 (3… 62.77 (2… 0.78 (0.4…
## 4 Age_stage Age … 23.82… 12.3 (7 -… 2.81 … 31.67… 77.11 (5… 65.74 (1… 1.54 (0.5…
## # ℹ 11 more variables: POM_mean <chr>, `A-E_mean` <chr>, `A-N_mean` <chr>,
## #   `A-M_mean` <chr>, `A-R_mean` <chr>, `A-C_mean` <chr>, `F-E_mean` <chr>,
## #   `F-N_mean` <chr>, `F-M_mean` <chr>, `F-R_mean` <chr>, `F-C_mean` <chr>
```



```r
final_table <- map_dfr(subgroups, ~ describe_subgroup(d, .x, variables))
final_table %>% knitr::kable()
```



|subgroup       |Level                  |M_mean                |Kv100_mean           |δ_mean             |T_mean                |A365_mean              |A460_mean              |Anadn_mean         |POM_mean             |A-E_mean           |A-N_mean           |A-M_mean           |A-R_mean           |A-C_mean           |F-E_mean           |F-N_mean           |F-M_mean           |F-R_mean           |F-C_mean           |
|:--------------|:----------------------|:---------------------|:--------------------|:------------------|:---------------------|:----------------------|:----------------------|:------------------|:--------------------|:------------------|:------------------|:------------------|:------------------|:------------------|:------------------|:------------------|:------------------|:------------------|:------------------|
|Gender         |female                 |21.36 (4.73 - 31.35)  |24.24 (6.91 - 51.79) |4.16 (1.82 - 6.93) |31.74 (24.43 - 35.9)  |86.68 (5.89 - 134.23)  |58.41 (21.73 - 90.54)  |1.07 (0.4 - 4.2)   |8.33 (0.89 - 22.2)   |1.47 (0.65 - 2.41) |1.44 (0.6 - 2.83)  |1.17 (0.52 - 2.09) |0.73 (0.32 - 1.24) |0.94 (0.51 - 1.71) |0.01 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.08 (0.06 - 0.14) |0.32 (0.21 - 0.51) |1.13 (0.84 - 1.38) |
|Gender         |male                   |23.43 (5.25 - 37.35)  |18.7 (6.94 - 40.1)   |3.81 (0.86 - 7.86) |31.07 (22.54 - 35.67) |86.94 (5.75 - 155.8)   |59.97 (13.2 - 106.95)  |0.96 (0.4 - 4.18)  |9.04 (1.84 - 18.4)   |1.51 (0.34 - 3.46) |1.47 (0.29 - 2.99) |1.17 (0.27 - 2.38) |0.69 (0.19 - 1.28) |0.92 (0.27 - 1.64) |0.02 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.08 (0.06 - 0.13) |0.33 (0.21 - 0.51) |1.14 (0.89 - 1.49) |
|Age_stage      |Age <30                |19.42 (4.73 - 36.16)  |25.59 (7.57 - 50.18) |3.87 (1.77 - 7.04) |30.53 (22.99 - 35.49) |81.03 (2.62 - 141.44)  |51.75 (11.31 - 87.56)  |1.06 (0.4 - 4.09)  |7.61 (0.94 - 19.62)  |1.4 (0.53 - 2.8)   |1.39 (0.5 - 2.7)   |1.15 (0.42 - 2.27) |0.68 (0.24 - 1.15) |0.91 (0.41 - 1.74) |0.01 (0.01 - 0.02) |0.04 (0.02 - 0.05) |0.08 (0.06 - 0.14) |0.29 (0.21 - 0.56) |1.12 (0.86 - 1.46) |
|Age_stage      |Age >=50               |18.3 (6.08 - 29.85)   |28.59 (9.63 - 51.94) |4.25 (1.4 - 7.01)  |29.58 (22.94 - 35.62) |84.81 (38.06 - 120.15) |57.83 (19.62 - 101.52) |0.77 (0.56 - 1.01) |7.78 (1.94 - 15.25)  |1.83 (0.39 - 3.46) |1.68 (0.35 - 2.99) |1.26 (0.36 - 2.22) |0.81 (0.37 - 1.27) |1.08 (0.73 - 1.72) |0.02 (0.01 - 0.02) |0.04 (0.03 - 0.05) |0.09 (0.07 - 0.13) |0.38 (0.29 - 0.45) |1.03 (0.76 - 1.32) |
|Age_stage      |Age [30-40)            |25.23 (12.47 - 37.4)  |19.9 (6.34 - 43.8)   |4.46 (2.28 - 8.21) |32.21 (25.97 - 35.37) |95.88 (31.5 - 159.05)  |62.77 (29.5 - 103.3)   |0.78 (0.4 - 1.72)  |10.86 (2.34 - 23.57) |1.69 (0.67 - 3.17) |1.59 (0.62 - 3)    |1.27 (0.52 - 2.53) |0.73 (0.28 - 1.38) |0.95 (0.53 - 1.53) |0.01 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.08 (0.06 - 0.14) |0.33 (0.21 - 0.49) |1.17 (0.89 - 1.39) |
|Age_stage      |Age [40-50)            |23.82 (5.1 - 32.87)   |12.3 (7 - 19.75)     |2.81 (0.55 - 5.02) |31.67 (22.33 - 35.84) |77.11 (5.15 - 122.96)  |65.74 (16.98 - 120.6)  |1.54 (0.55 - 5.72) |6.26 (0.83 - 14.1)   |1.06 (0.21 - 2.31) |1.19 (0.17 - 2.59) |0.93 (0.15 - 2.02) |0.62 (0.13 - 1.14) |0.85 (0.19 - 1.63) |0.02 (0.01 - 0.02) |0.03 (0.02 - 0.04) |0.08 (0.06 - 0.13) |0.36 (0.21 - 0.51) |1.14 (0.85 - 1.49) |
|Race           |Asian or Asian British |21.07 (4.73 - 35.67)  |21.42 (6.74 - 48.49) |3.65 (1.02 - 6.78) |30.78 (22.73 - 35.78) |86.11 (5.5 - 146)      |61.93 (16 - 106.75)    |1.06 (0.41 - 5.03) |7.6 (0.87 - 18.92)   |1.37 (0.34 - 2.84) |1.31 (0.31 - 2.74) |1.07 (0.29 - 2.44) |0.66 (0.2 - 1.15)  |0.86 (0.32 - 1.63) |0.01 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.08 (0.06 - 0.14) |0.33 (0.21 - 0.53) |1.15 (0.83 - 1.49) |
|Race           |Black                  |29.87 (24.44 - 35.16) |16.24 (9.2 - 20.74)  |4.83 (2.77 - 7.24) |34.38 (33.69 - 35.61) |18.83 (3.88 - 32.38)   |14 (11.2 - 15.95)      |1.94 (0.93 - 3.72) |8.38 (2.19 - 15.62)  |1.46 (0.76 - 1.97) |1.97 (0.86 - 2.97) |1.44 (0.73 - 1.95) |0.79 (0.66 - 0.88) |1.24 (0.89 - 1.65) |0.01 (0.01 - 0.02) |0.04 (0.03 - 0.04) |0.06 (0.06 - 0.07) |0.35 (0.22 - 0.46) |1.11 (1.03 - 1.22) |
|Race           |White                  |27.05 (17.35 - 36.86) |20.71 (8.69 - 46.87) |5.05 (2.44 - 7.64) |33.11 (28.9 - 35.59)  |103.32 (55.3 - 148)    |57.66 (34.51 - 72.71)  |0.61 (0.39 - 1.17) |13.44 (5.49 - 26.96) |1.98 (0.75 - 3.43) |1.98 (0.85 - 2.99) |1.52 (0.74 - 2.25) |0.87 (0.57 - 1.48) |1.13 (0.78 - 1.73) |0.02 (0.01 - 0.02) |0.03 (0.02 - 0.04) |0.08 (0.06 - 0.12) |0.3 (0.21 - 0.45)  |1.07 (0.88 - 1.36) |
|Typer of skins |1                      |25.2 (17.02 - 29.31)  |21.36 (8.61 - 47.84) |4.76 (2.42 - 6.96) |33.02 (28.84 - 35.63) |101.56 (53.9 - 126)    |59.15 (41.05 - 72.92)  |0.64 (0.42 - 1.2)  |11.5 (5.32 - 21.26)  |1.97 (0.75 - 3.44) |1.96 (0.86 - 2.99) |1.47 (0.74 - 2.18) |0.84 (0.57 - 1.48) |1.13 (0.82 - 1.72) |0.02 (0.01 - 0.02) |0.03 (0.02 - 0.04) |0.08 (0.06 - 0.12) |0.3 (0.21 - 0.4)   |1.1 (0.88 - 1.36)  |
|Typer of skins |2                      |31.27 (27.17 - 37.75) |14.64 (6.03 - 20.3)  |5.1 (2.72 - 7.73)  |33.49 (29.6 - 35.95)  |90.7 (19.85 - 154.05)  |53.2 (29.4 - 71.45)    |1.15 (0.4 - 2.45)  |15.33 (4.03 - 28.27) |1.87 (0.83 - 2.89) |1.96 (0.9 - 2.87)  |1.57 (0.89 - 2.15) |0.91 (0.52 - 1.31) |0.92 (0.77 - 1.19) |0.02 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.07 (0.06 - 0.09) |0.34 (0.22 - 0.46) |1.14 (1.04 - 1.24) |
|Typer of skins |3                      |19.6 (4.7 - 37.23)    |21.13 (6.87 - 49.5)  |3.21 (0.81 - 6.35) |30.2 (22.47 - 35.2)   |94.44 (13.81 - 132.22) |69.1 (33.98 - 107.6)   |0.95 (0.4 - 3.62)  |6.91 (0.74 - 15.97)  |1.21 (0.33 - 2.47) |1.17 (0.29 - 2.51) |0.95 (0.27 - 2.2)  |0.57 (0.19 - 1.01) |0.8 (0.25 - 1.65)  |0.01 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.08 (0.06 - 0.14) |0.33 (0.21 - 0.5)  |1.14 (0.84 - 1.49) |
|Typer of skins |4                      |26.43 (20.44 - 31.86) |20.89 (7.92 - 33.38) |4.95 (2.37 - 6.81) |33.16 (31.52 - 35.54) |95.18 (44.06 - 149.81) |60.34 (30.44 - 98.88)  |0.66 (0.43 - 0.97) |12.14 (6.48 - 21.58) |1.85 (0.81 - 2.62) |1.68 (0.62 - 2.7)  |1.44 (0.57 - 2.31) |0.89 (0.5 - 1.16)  |1.13 (0.6 - 1.62)  |0.01 (0.01 - 0.02) |0.04 (0.02 - 0.05) |0.08 (0.06 - 0.12) |0.32 (0.21 - 0.56) |1.12 (0.99 - 1.27) |
|Typer of skins |5                      |17.05 (5.33 - 32.41)  |30.69 (15.07 - 40.1) |4.27 (1.88 - 8.73) |28.15 (23.39 - 32.28) |33.67 (6.06 - 75.75)   |27.79 (12.44 - 49.69)  |1.63 (0.68 - 5)    |4.54 (1.4 - 9.68)    |1.55 (0.74 - 3.72) |1.4 (0.62 - 3.14)  |1.15 (0.49 - 2.52) |0.77 (0.27 - 1.16) |0.87 (0.57 - 1.45) |0.01 (0.01 - 0.02) |0.04 (0.03 - 0.05) |0.09 (0.06 - 0.13) |0.29 (0.21 - 0.38) |1.23 (0.78 - 1.48) |
|Typer of skins |6                      |29.87 (24.58 - 35.03) |14.05 (7.58 - 20.7)  |4.17 (2.25 - 7.16) |34.73 (33.69 - 35.77) |14.62 (2.08 - 32.06)   |13.75 (11.15 - 15.93)  |2.57 (0.93 - 4.44) |6.78 (1.93 - 15.4)   |1.24 (0.58 - 1.96) |1.6 (0.5 - 2.95)   |1.2 (0.48 - 1.94)  |0.72 (0.53 - 0.88) |1.09 (0.67 - 1.64) |0.01 (0.01 - 0.02) |0.04 (0.03 - 0.04) |0.08 (0.06 - 0.14) |0.4 (0.22 - 0.54)  |1.16 (1.03 - 1.31) |
|Stress index   |No                     |21.02 (4.73 - 35.59)  |21.12 (6.71 - 48.75) |3.64 (0.98 - 6.93) |30.65 (22.68 - 35.6)  |85.43 (9.5 - 130.9)    |60.64 (17.2 - 106.8)   |1.01 (0.41 - 4.77) |7.7 (0.85 - 20.43)   |1.44 (0.34 - 3.42) |1.4 (0.31 - 2.99)  |1.11 (0.29 - 2.35) |0.66 (0.2 - 1.18)  |0.89 (0.31 - 1.74) |0.02 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.08 (0.06 - 0.14) |0.32 (0.21 - 0.5)  |1.14 (0.82 - 1.49) |
|Stress index   |Yes                    |26.49 (8.59 - 36.71)  |21 (7.56 - 48.44)    |4.79 (2.25 - 7.65) |33.21 (30.14 - 35.82) |90.43 (2.52 - 159.81)  |55.81 (12.05 - 88.06)  |1 (0.39 - 4.16)    |11.42 (1.95 - 24.42) |1.62 (0.64 - 2.7)  |1.61 (0.49 - 2.96) |1.33 (0.5 - 2.32)  |0.81 (0.47 - 1.44) |1.02 (0.58 - 1.61) |0.01 (0.01 - 0.02) |0.04 (0.02 - 0.05) |0.08 (0.06 - 0.12) |0.34 (0.21 - 0.56) |1.12 (0.87 - 1.36) |
|Smoking        |Non smoker             |22.85 (5.03 - 37.28)  |22.52 (6.77 - 50.23) |4.18 (1.81 - 7.18) |31.66 (23.91 - 35.82) |87.03 (11 - 142.2)     |57.85 (14.2 - 91.5)    |0.92 (0.4 - 3.68)  |8.93 (1.18 - 20.82)  |1.59 (0.6 - 3.4)   |1.53 (0.61 - 3)    |1.23 (0.5 - 2.43)  |0.73 (0.25 - 1.22) |0.96 (0.42 - 1.73) |0.01 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.08 (0.06 - 0.14) |0.32 (0.21 - 0.5)  |1.12 (0.83 - 1.4)  |
|Smoking        |Smoker                 |21.11 (4.6 - 34.09)   |14.43 (7.88 - 21.47) |2.95 (0.55 - 7.05) |29.95 (21.91 - 35.75) |85.86 (2.81 - 149.72)  |65.99 (13.65 - 123.2)  |1.42 (0.41 - 5.22) |7.84 (1.1 - 25.04)   |1.03 (0.21 - 2.79) |1.12 (0.16 - 2.84) |0.88 (0.15 - 2.18) |0.58 (0.13 - 1.25) |0.78 (0.19 - 1.51) |0.02 (0.01 - 0.02) |0.04 (0.02 - 0.04) |0.09 (0.06 - 0.14) |0.35 (0.21 - 0.52) |1.2 (1.02 - 1.56)  |
|Hypertension   |No                     |23.59 (4.94 - 37.31)  |22.49 (7.24 - 50.57) |4.41 (1.8 - 7.71)  |31.79 (23.64 - 35.8)  |85.28 (8.54 - 159.65)  |54.32 (12.99 - 93.9)   |0.92 (0.4 - 3.73)  |9.83 (1.56 - 22.35)  |1.64 (0.59 - 3.42) |1.59 (0.61 - 3.01) |1.29 (0.5 - 2.44)  |0.76 (0.26 - 1.31) |0.99 (0.46 - 1.75) |0.02 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.08 (0.06 - 0.14) |0.31 (0.21 - 0.48) |1.12 (0.87 - 1.47) |
|Hypertension   |Yes                    |19.63 (4.51 - 31.4)   |17.2 (7.07 - 37.09)  |2.72 (0.62 - 4.89) |30.17 (22.06 - 35.78) |91.1 (4.25 - 127.25)   |73.04 (23.5 - 119)     |1.24 (0.53 - 5.14) |5.71 (0.87 - 11.87)  |1.09 (0.24 - 2.4)  |1.09 (0.19 - 2.46) |0.83 (0.18 - 1.75) |0.55 (0.14 - 1.07) |0.74 (0.21 - 1.63) |0.01 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.09 (0.06 - 0.14) |0.37 (0.21 - 0.56) |1.17 (0.77 - 1.48) |
|BMI_25_30      |BMI <25                |19.34 (4.73 - 33.05)  |24.03 (7.55 - 49.35) |3.96 (0.84 - 7.37) |30.26 (22.51 - 35.77) |85.67 (3.07 - 159.05)  |59.08 (13.1 - 106.98)  |1.1 (0.4 - 4.45)   |7.45 (0.77 - 19.85)  |1.46 (0.34 - 3.44) |1.4 (0.29 - 3.02)  |1.13 (0.27 - 2.28) |0.65 (0.19 - 1.08) |0.87 (0.26 - 1.67) |0.01 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.08 (0.06 - 0.14) |0.31 (0.21 - 0.49) |1.14 (0.87 - 1.49) |
|BMI_25_30      |BMI >=30               |26.37 (20.85 - 30.15) |17.64 (7.83 - 24.97) |4.26 (2.35 - 5.92) |33.65 (31.39 - 35.66) |99.55 (72.49 - 118.18) |63.09 (39.01 - 85.58)  |0.68 (0.41 - 0.95) |10.81 (6.59 - 17.38) |1.89 (0.77 - 3.2)  |1.81 (0.59 - 2.84) |1.27 (0.56 - 1.88) |0.79 (0.49 - 1.44) |0.99 (0.6 - 1.32)  |0.02 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.07 (0.06 - 0.1)  |0.36 (0.22 - 0.56) |1.18 (0.89 - 1.36) |
|BMI_25_30      |BMI [25-30)            |26.36 (5.75 - 37.61)  |17.55 (6.79 - 44.5)  |3.87 (1.98 - 7.14) |32.39 (24.3 - 35.41)  |84.97 (13.59 - 139.26) |58.54 (19.94 - 89.92)  |0.96 (0.43 - 2.9)  |10.13 (1.77 - 24.74) |1.43 (0.64 - 2.98) |1.46 (0.61 - 2.83) |1.2 (0.48 - 2.42)  |0.76 (0.25 - 1.23) |0.99 (0.49 - 1.7)  |0.02 (0.01 - 0.02) |0.04 (0.02 - 0.05) |0.08 (0.06 - 0.14) |0.34 (0.21 - 0.5)  |1.12 (0.78 - 1.31) |
|Obesity        |No                     |22.11 (4.73 - 37.26)  |21.48 (6.81 - 49.94) |3.92 (1.13 - 7.53) |31.1 (22.85 - 35.8)   |85.39 (4.12 - 159)     |58.87 (12.62 - 106.62) |1.04 (0.4 - 4.76)  |8.5 (0.94 - 22.22)   |1.45 (0.34 - 3.14) |1.42 (0.32 - 3)    |1.16 (0.3 - 2.41)  |0.69 (0.21 - 1.2)  |0.92 (0.36 - 1.71) |0.01 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.08 (0.06 - 0.14) |0.32 (0.21 - 0.5)  |1.13 (0.83 - 1.49) |
|Obesity        |Yes                    |26.37 (20.85 - 30.15) |17.64 (7.83 - 24.97) |4.26 (2.35 - 5.92) |33.65 (31.39 - 35.66) |99.55 (72.49 - 118.18) |63.09 (39.01 - 85.58)  |0.68 (0.41 - 0.95) |10.81 (6.59 - 17.38) |1.89 (0.77 - 3.2)  |1.81 (0.59 - 2.84) |1.27 (0.56 - 1.88) |0.79 (0.49 - 1.44) |0.99 (0.6 - 1.32)  |0.02 (0.01 - 0.02) |0.03 (0.02 - 0.05) |0.07 (0.06 - 0.1)  |0.36 (0.22 - 0.56) |1.18 (0.89 - 1.36) |

