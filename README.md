# Krona charts in R

This repo provides a function for creating [Krona charts](https://github.com/marbl/Krona/wiki) in R.

## Features

- The interactive charts can be explored directly within R-Markdown documents in RStudio and will be embedded into documents rendered to *HTML* webpages.
- For document formats like PDF, DOCX, ODT, etc., snapshot images will be inserted.
- Support for [phyloseq](https://github.com/joey711/phyloseq) objects.
- Flexible grouping into multiple datasets explored within the same chart
- Custom coloring schemes

## Example

The following snapshot image of a Krona chart gives an overview of the taxa in the GlobalPatterns dataset from [phyloseq](https://joey711.github.io/phyloseq/index.html) package. It was generated in the [example analysis](example.md).

![GlobalPatterns Krona chart](krona/global_patterns.png)

## Tutorial

A small tutorial is provided in the [example R-Markdown document](example.Rmd). Two rendered versions can be downloaded:

- A [*HTML* webpage](example.html) with embedded interactive charts
- A [*PDF* document](example.pdf)

For a documentation of all possible options for `plot_krona` see the [R script](embed_krona.R). 

## Output format notes

Whether interactive charts or static snapshots are embedded depends on whether the `plot_krona` function is executed from within R-Markdown chunks, in the R console or rendered to [different R-Markdown document formats](https://rmarkdown.rstudio.com/formats.html). Snapshots can be enforced with `snapshot=TRUE`.



|  	| **interactive chart** 	| **snapshot image\*** 	| **remarks** 	|
|---	|---	|---	|---	|
| Inline view below R-Markdown chunks (Rstudio) 	| yes 	| yes (png) 	| (1) interactive chart size can be changed with *iframe_width* / *iframe_height*, but this just adds scrollbars, the viewport does not change. (2) Snapshots (with snapshot=TRUE) can appear too large  since expanded to 100% width. (3) ‘krona_opts’ have no effect.(4) out.width/out.height chunk options have no effect 	|
| R console 	| yes (in browser) 	| (yes) 	| (1) snapshot images are produced but not displayed; (2) ‘krona_opts’ have no effect 	|
| HTML (html_document) 	| yes 	| yes (png) 	| (1) interactive chart: *iframe_height* modifies the height; (2) snapshots may appear small with default size, either increase snapshot_dim or resize set out.width (e.g. to ’100%’) to zoom in. 	|
| PDF (pdf_document) 	| - 	| yes (png, pdf) 	| adjusting *snapshot_dim* works well 	|
| DOCX (word_document) 	| - 	| yes (png, pdf) 	| Figures always have the same (incorrect) size 	|
| OpenDocument Text (odt_document) 	| - 	| yes (png, pdf) 	| Set out.width to same value as width in *snapshot_dim* (e.g.: *out.width=’6in’*). Otherwise, the figure will be huge. 	|
| RTF text (rtf_document) 	| - 	| yes (png) 	| see ODT 	|
| Github Markdown (github_document) 	| yes 	| yes 	| see HTML 	|
