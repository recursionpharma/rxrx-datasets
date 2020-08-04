# RxRx19b

RxRx19b is the second component of the RxRx19 dataset series released by [Recursion][recursion] sharing data
from a high-dimensional human cellular assay for COVID-19 associated disease. RxRx19b models the COVID-19-associated
cytokine storm. For more information about RxRx19b please visit [RxRx.ai][rxrx19b] and the associated preprint,
[Functional immune mapping with deep-learning enabled phenomics applied to immunomodulatory and COVID-19 drug discovery][paper2].

RxRx19b is part of a larger set of Recursion datasets that can be found at [RxRx.ai][rxrx] and on [GitHub][github].


## Metadata

The metadata can be found in `metadata.csv` and downloaded [from here][download]. The schema of the metadata is as follows:

| Attribute         | Description                                                                                                           |
|-------------------|-----------------------------------------------------------------------------------------------------------------------|
| site_id           | Unique identifier of a given site                                                                                     |
| well_id           | Unique identifier of a given well                                                                                     |
| cell_type         | Cell type tested                                                                                                      |
| experiment        | Experiment identifier                                                                                                 |
| plate             | Plate number within the experiment                                                                                    |
| well              | Location on the plate                                                                                                 |
| site              | Indication of the location in the well where image was taken (always 1 in RxRx19b)                                    |
| disease_condition | The disease condition tested in the well (healthy cytokine cocktail, severe cytokine storm cocktail, or no cytokines) |
| treatment         | Compound tested in the well (if any)                                                                                  |
| treatment_conc    | Compound concentration tested (in uM)                                                                                 |
| SMILES            | Formula of tested compound (as CXSMILES/ChemAxon Extended SMILES)                                                     |


## Images

The images are found in `images/*` and can be downloaded [from here][download] (*n.b.* this is 409GB).
The image data are 2048x2048 8-bit `png` files. The image paths, such as `HUVEC-1/Plate1/AA02_s1_w3.png`, can be read as:

Experiment Name: Cell type and experiment number (HUVEC experiment 1)
Plate Number (1)
Well location on plate (column AA, row 2)
Site (1)
Channel (3) 

All six channels (`w1` - `w6`) make up an single image of a given `site`.


## Deep Learning Embeddings


The deep learning embeddings can be found in `embeddings.csv` and downloaded [from here][download] (*n.b.* this is 41MB).

Each row in the csv has a `site_id` as described in the metadata schema. The remaining 128 columns are the embedding for that respective site.

## Changelog:
- August 2020: initial release

## License


<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a>

This work is licensed under the Creative Commons Attribution 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.

[github]: https://github.com/recursionpharma/rxrx-datasets/
[paper2]: https://doi.org/10.1101/2020.08.02.233064
[rxrx]: http://rxrx.ai
[rxrx19b]: https://rxrx.ai/rxrx19b
[recursion]: http://recursionpharma.com
[download]: https://rxrx.ai/rxrx19b#Download
