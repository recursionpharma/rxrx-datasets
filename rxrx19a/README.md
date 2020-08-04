# RxRx19a

RxRx19a is the first component of the RxRx19 dataset series released by [Recursion][recursion] sharing data
from a high-dimensional human cellular assay for COVID-19 associated disease. RxRx19a models active SARS-CoV-2
infection in both human renal cortical epithelial cells as well as Vero cells. For more information about RxRx19a
please visit [RxRx.ai][rxrx19] and the associated preprints,
[Identification of potential treatments for COVID-19 through artificial intelligence-enabled phenomic analysis of human cells infected with SARS-CoV-2][paper]
and
[Functional immune mapping with deep-learning enabled phenomics applied to immunomodulatory and COVID-19 drug discovery][paper2].


RxRx19a is part of a larger set of [Recursion][recursion] datasets that can be found at [RxRx.ai][rxrx] and on [GitHub][github]. For questions about this dataset and others please email [info@rxrx.ai](mailto:info@rxrx.ai).

## Metadata

The metadata can be found in `metadata.csv` and downloaded [from here][download]. The schema of the metadata is as follows:

| Attribute         | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| site_id           | Unique identifier of a given site                                           |
| well_id           | Unique identifier of a given well                                           |
| cell_type         | Cell type tested                                                            |
| experiment        | Experiment identifier                                                       |
| plate             | Plate number within the experiment                                          |
| well              | Location on the plate                                                       |
| site              | Indication of the location in the well where image was taken (1, 2, 3 or 4) |
| disease_condition | The disease condition tested in the well (mock, irradiated or viral)        |
| treatment         | Compound tested in the well                                                 |
| treatment_conc    | Compound concentration tested (in uM)                                       |
| SMILES            | Formula of tested compound (as CXSMILES/ChemAxon Extended SMILES)           |


## Images

The images are found in `images/*` and can be downloaded [from here][download] (*n.b.* this is 445GB).
The image data are 1024x1024 8-bit `png` files. The image paths, such as `HRCE-1/Plate1/AA02_s2_w3.png`, can be read as:

Experiment Name: Cell type and experiment number (HRCE experiment 1)       
Plate Number (1)               
Well location on plate (column AA, row 2)           
Site (2)            
Channel (3)                  

All five channels (`w1` - `w5`) make up an single image of a given `site`.


## Deep Learning Embeddings


The deep learning embeddings can be found in `embeddings.csv` and downloaded [from here][download] (*n.b.* this is 1.4GB).

Each row in the csv has a `site_id` as described in the metadata schema. The remaining 1024 columns are the embedding for that respective site.

## Changelog

- April 2020: initial release
- August 2020: updated to correct metadata errors in compound mapping and add SMILES to metadata

## License


<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a>

This work is licensed under the Creative Commons Attribution 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.


[github]: https://github.com/recursionpharma/rxrx-datasets/
[paper]: https://doi.org/10.1101/2020.04.21.054387
[paper2]: https://doi.org/10.1101/2020.08.02.233064
[rxrx]: http://rxrx.ai
[rxrx19]: https://rxrx.ai/rxrx19
[recursion]: http://recursionpharma.com
[download]: https://rxrx.ai/rxrx19#Download
