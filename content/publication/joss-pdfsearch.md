---
abstract: "PDF files are common formats for reports, journal articles, briefs, and many other documents. PDFs are lightweight, portable, and easily viewed across operating systems. Even though PDF files are ubiquitous, extracting and finding text within a PDF can be time consuming and not easily reproducible. The pdftools R package (Ooms 2017), which uses the poppler C++ library to extract text from PDF documents, aids in the ability to import text data from PDF files to manipulate in R. The pdfsearch package (LeBeau 2018) is an R package (R Core Team 2016) that extends the text extraction of pdftools to allow for keyword searching within a single PDF or a directory of PDF files.

The pdfsearch package can aid users in manipulation of text data from PDF files in R and may also improve the reproducibility of the extraction and manipulation tasks. Users can search for keywords within PDF files where the location of the match and the raw text from the match are returned. This aspect of searching for keywords may be most useful for those conducting research syntheses or meta-analyses (Cooper 2017) that are more reproducible and less time consuming than current practice. Current research synthesis or meta-analysis practice involves the reading of each document to search for the presence of certain terms, phrases, or statistical effect size information to answer specific research questions. The improved workflow with the pdfsearch package would allow those conducting research syntheses, the ability to narrow down relevant portions of text based on the keyword matches returned by the package instead of looking at the entire text of the document. In addition, regular expressions could be written to search and extract statistical information needed to compute effect sizes automatically. 

As an example, the package is currently being used to explore the evolution of statistical software and quantitative methods used in published social science research (LeBeau and Aloe 2018). This process involves getting PDF files from published research articles and using pdfsearch to search for specific software and quantitative methods keywords within the research articles. The results of the keyword matches will be explored using research synthesis methods (Cooper 2017).

The package vignette includes more information on this package. Included in the vignette are keyword searches within PDF documents and an exploration of the output from the package. The vignette also discusses limitations of the package. Below is example output of the package searching for the phrase “repeated measures” from Guo and Deng (2015)."
authors: 
- Brandon LeBeau
date: 2018-07-09
image: ""
image_preview: ""
math: false
publication: In *Journal of Open Source Software*, 3 (27)
title: "pdfsearch: Search Tools for PDF Files"
url_code: "https://github.com/lebebr01/pdfsearch"
url_custom:
- name: Link to JOSS
  url: http://joss.theoj.org/papers/10.21105/joss.00668
url_dataset: ""
url_pdf: "https://www.theoj.org/joss-papers/joss.00668/10.21105.joss.00668.pdf"
url_project: ""
url_slides: ""
url_video: ""
---
  

