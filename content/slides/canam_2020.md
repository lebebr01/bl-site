---
title: "Evolution of Statistical Software and Quantitative Methods"
author: "Brandon LeBeau & Ariel M. Aloe"
date: "2020-04-24"
slug: "canam2020"
tags: [slides, software, analysis]
---

<h1>Evolution of Statistical Software and Quantitative Methods</h1>
<h2>Brandon LeBeau & Ariel M. Aloe</h2>
<h3>University of Iowa</h3>



# Rationale
- Extension of work done by Robert Muenchen (http://r4stats.com/articles/popularity/). 
    + Focus is on statistical software
    + Addition of quantitative methods
    + Particularly interested in the interaction.
- Questions of Interest:
    + Exploring which software is popular in published research. 
    + How many empirical analyses cite software?
    + Any patterns in software use with quantitative methods?




# Methods
- Research synthesis methods were used
- Web of Knowledge was used to pull in citations for 12 social science journals
    - 1995 to 2018
- EndNote's "Find Text" feature was used to pull in PDFs of all articles from the journals
- `pdfsearch` R package was used to perform keyword searching.




# `pdfsearch`
- Converts lines of text into sentences
- Removes multiple columns into a single column
- Identifies location of keyword found within document.




# `pdfsearch`
- Short live code demo




# Software Keywords
| Keyword Group | Keywords | 
|---------------|----------|
| AMOS          | AMOS     |
| IRT           | BILOG; BILOG-MG; IRT PRO; MULTILOG; PARSCALE | 
| R             | CRAN; R-project; R Project; R Core Team; R software; RStudio | 
| HLM           | HLM [0-9]; HLM[0-9] | 
| Java          | Java  |
| SAS           | SAS; SAS Institute; JMP |
| LISREL        | LISREL |
| Mplus         | Mplus; M-Plus |
| Python        | Python |
| SPSS          | SPSS; SPSS Statistics | 
| STATA         | STATA |
| Other         | Matlab; Scala; Systat; Statistica; Tableau; Minitab |




# Method Keywords 
| Keyword Group | Keywords | 
|---------------|----------|
| ANOVA         | Analysis of Variance; ANOVA; Analysis of Covariance; ANCOVA; MANOVA; Multivariate Analysis of Variance; Repeated Measures Analysis of Variance; RM-ANOVA | 
| IRT           | IRT; Item Response Theory |
| CFA           | CFA; Confirmatory Factor Analysis |
| Chi-Square    | Chi-square( analysis)?; Nonparametric Analysis | 
| Cluster Analysis | Cluster Analysis; Hierarchical Cluster Analysis | 
| t-test        | Dependent Samples t-test; one-sample t-test; two-sample t-test | 
| EFA           | EFA; Exploratory Factor Analysis | 
| GAM           | GAM; Generalized additive models | 




# Method Keywords Continued
| Keyword Group | Keywords | 
|---------------|----------|
| Linear Mixed Model | LMM; HLM; Multilevel Model; Multi-level Model; Hierarchical Linear Model; General(ized)? Linear Mixed Model | 
| Linear Model | Linear Regression; Multiple Linear Regression; Multiple Regression; General(ized)? Linear Model |
| Growth       | Growth Model; Latent Growth Model; LGM | 
| SEM          | Latent Variable Modeling; SEM; Structural Equation Modeling | 
| Logistic Regression | Logistic Regression; Multinomial Regression; Multinomial Logistic Regression; Ordinal Regression | 
| meta-analysis | meta-analysis; meta analysis |
| Non-Linear Regression | Non-Linear Regression; Nonlinear Regression |
| Propensity Score | Propensity Score Analysis; Propensity score matching |




# Journals Sampled
* American Economic Journal (AEJ)
* American Educational Research Journal (AERJ)
* American Journal of Political Science (AJPS)
* Economic Journal (EJ)
* Educational Evaluation and Policy Analysis (EEPA)
* Educational Researcher (ER)
* Higher Education (HE)
* Journal of Experimental Education (JEE)
* Journal of Public Policy (JPP)
* Political Science Quarterly (PSQ)
* Public Policy Administration (PPA)
* Sociology of Education (SE)




# How many articles obtained?
![](/figs/pdf-time-1.png)




# Software Counts
![](/figs/count-software-1.png)




# Software Keywords by Discipline
![](/figs/discipline-software-1.png)




# Number of software keywords
<table>
 <thead>
  <tr>
   <th style="text-align:left;"> Discipline </th>
   <th style="text-align:right;"> Avg Keywords </th>
   <th style="text-align:right;"> Min Keywords </th>
   <th style="text-align:right;"> Max Keywords </th>
   <th style="text-align:right;"> Prop. Uniq </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Economics </td>
   <td style="text-align:right;"> 1.08 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:right;"> 0.16 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Education </td>
   <td style="text-align:right;"> 1.67 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 7 </td>
   <td style="text-align:right;"> 0.21 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Political Science </td>
   <td style="text-align:right;"> 1.14 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:right;"> 0.10 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Public Policy </td>
   <td style="text-align:right;"> 1.00 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 0.19 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Sociology </td>
   <td style="text-align:right;"> 1.22 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 6 </td>
   <td style="text-align:right;"> 0.28 </td>
  </tr>
</tbody>
</table>




# Analysis keywords
![](/figs/model-discipline-1.png)




# Number of analysis keywords
<table>
 <thead>
  <tr>
   <th style="text-align:left;"> Discipline </th>
   <th style="text-align:right;"> Avg Keywords </th>
   <th style="text-align:right;"> Min Keywords </th>
   <th style="text-align:right;"> Max Keywords </th>
   <th style="text-align:right;"> Prop. Uniq </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Economics </td>
   <td style="text-align:right;"> 1.38 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:right;"> 0.59 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Education </td>
   <td style="text-align:right;"> 3.36 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 12 </td>
   <td style="text-align:right;"> 0.27 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Political Science </td>
   <td style="text-align:right;"> 1.62 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 5 </td>
   <td style="text-align:right;"> 0.23 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Public Policy </td>
   <td style="text-align:right;"> 1.43 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:right;"> 0.25 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Sociology </td>
   <td style="text-align:right;"> 2.39 </td>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:right;"> 7 </td>
   <td style="text-align:right;"> 0.74 </td>
  </tr>
</tbody>
</table>




# General Software Keyword Percentages by Year - Education
![](/figs/software-year-at1-1.png)




# Specialty Software Keyword Percentages by Year - Education
![](/figs/software-year-spec-1.png)




# Analysis Keyword Percentages by Year - Education
![](/figs/model-year-at1-1.png)





# Analysis Keyword Percentages by Year - Education
![](/figs/model-year-other-1.png)




# Interaction between Software and Analysis - Education
![s](/figs/software-statmethods-1.png)



# Interaction between Software and Analysis by Year - Education
![](/figs/software-statmethods-year-1.png)



# Interaction between Software and Analysis by Year - Education
![](/figs/software-statmethods-year2-1.png)



# Conclusions
- Cite the software you use!
    + It benefits the software developer
    + It benefits the reproducibility
    + It benefits the replicability
- There are discipline/journal differences in methods and software used.



# Connect
- slides: https://brandonlebeau.org/slides/canam2020/
- twitter: blebeau11
