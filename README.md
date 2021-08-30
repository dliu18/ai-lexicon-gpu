# A New AI Lexicon: Power
by David M. Liu and Sarah Sakha 

This repository contains the code necessary to replicate the figures, tables, and GPU statistics in our (A New AI Lexicon)[https://medium.com/a-new-ai-lexicon] submission. 

For our piece, we measure the prevalence of GPUs in publications at ICML, NeurIPS, and IJCAI over the past decade. The code is divided into two parts: 1) Scraping (`Scrape_{Conference Name}.ipynb`) and 2) Lexical Analysis (`Analysis.ipynb`. To replicate our findings, execute the Scraping notebooks and then the Analysis notebook.


## Scraping Research Papers
We scrape all PDFs included in the Proceedings for each of the three conferences. The proceedings can be found at the following links:
* (ICML)[http://proceedings.mlr.press]
* (IJCAI)[https://www.ijcai.org/proceedings]
* (NeurIPS)[https://proceedings.neurips.cc]

In the process of scraping, the notebooks will use the `papers/` and `supplemental` directories for intermediate storage; the notebooks delete the files after usage to optimize for storage.

For debugging purposes, all three scraping notebooks pickle the metadata associated with all papers scraped. These pickled outputs are stored in `pickles/` and contain a list of metadata dictionaries. The metadata for each paper follows the following schema:
```
{
    "title": "Paper title",
    "year": Year paper was published,
    "paper_link": "Link to main paper PDF",
    "supplemental_link": "Link to Supplemental Materials (if applicable)"
}
```

When assessing whether a paper mentions a "GPU" we check both the main PDF as well as the supplemental materials, especially since authors frequently specify the computing environment in the supplement. 

## Miscellaneous Notes 
* For a small handful of papers the PDFs could not be retrieved from the proceedings website. These paper titles are printed out in each of the three notebooks during the scraping process. 
* We use the package `pdftotext` to extract the text from camera-ready PDFs. 
* We scrape all papers contained in the conference proceedings and do not differentiate by the type of submission. For instance, the IJCAI proceedings also contain "Demo" and "Doctoral Consortium" submissions which are substantially shorter than the Main Track full paper submissions. 