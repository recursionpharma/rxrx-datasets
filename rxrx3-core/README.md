# RxRx3-core

At Recursion, we build maps of biology and chemistry to explore uncharted areas of disease biology, unravel its complexity, and industrialize drug discovery. Just as a map helps to navigate the physical world, our maps are designed to help us understand as much as we can about the connectedness of human biology so we can navigate the path to new medicines more efficiently.

Previously, we released [RxRx3](./../rxrx3/) a publicly available map of biology that contains images and deep learning-based embeddings for 17,063 genetic knockouts, as well as 1,674 known chemical entities at 8 doses each. RxRx3 is over 100Tb and 16,328 of the genes are anonymized, making it difficult to leverage as a benchmarking task for the research community. With this goal in mind, we're releasing **RxRx3-core**, a compressed subset of RxRx3 containing only unblinded perturbations (735 genetic knockouts and all 1,674 known chemical entities) along with a set of associated benchmarking tasks available on [github](https://github.com/recursionpharma/EFAAR_benchmarking). 

**RxRx3-core is only 18GB and easily accesible via [Hugging Face](https://huggingface.co/datasets/recursionpharma/rxrx3-core)**.

If you'd like to understand more about how to get access to unblinded genes please email [info@rxrx.ai](mailto:info@rxrx.ai).

## Metadata

The metadata can be found in `metadata_rxrx3_core.csv` and downloaded [from here](https://huggingface.co/datasets/recursionpharma/rxrx3-core/blob/main/metadata_rxrx3_core.csv). The schema of the metadata is as follows:

| Attribute         | Description                                                                                                           |
|-------------------|-----------------------------------------------------------------------------------------------------------------------|
| well_id           | Experiment Name - Plate - Well (compound-004_1_AA04 or gene-088_9_Z43) |
| experiment_name   | Experiment Name: Experiment number (compound-004 or gene-088) 
| plate	            | Plate number in the experiment (1-48)                                         |                              |
| address           | Well location on the plate - "A01" to "AF48".                                     |
| gene              | Unblinded or anonymized gene name, or a control	      |
| treatment         | Compound synonym or gene-name - guide-number (Narlaprevir or <gene_name>_guide_1)       
| SMILES            | Canonical SMILES or blank for non-compounds
| concentration     | Compound concentration tested (in uM)                                   |	
| perturbation_type	| CRISPR or COMPOUND                                     |
| cell_type	        | HUVEC                                        |                                 |


### Metadata Example

To help understand the metadata, we have included some samples that some some of the more complex parts of the format to allow parser testing and validation

    well_id,experiment_name,plate,address,gene,treatment,SMILES,concentration,perturbation_type,cell_type
    gene-079_8_H29,gene-079,8,H29,RPLP2,RPLP2_guide_4,,,CRISPR,HUVEC
    gene-045_4_AD27,gene-045,4,AD27,RXRX3-43938,RXRX3-43938_guide_6,,,CRISPR,HUVEC
    gene-060_9_P28,gene-060,9,P28,EMPTY_control,EMPTY_control,,,CRISPR,HUVEC
    compound-001_19_D20,compound-001,19,D20,,Dequalinium,"CC1=[N+](CCCCCCCCCC[N+]2=C(C)C=C(N)C3=CC=CC=C23)C2=CC=CC=C2C(N)=C1 |c:1,13,21,29,31,35,t:16,19,23,27|",0.25,COMPOUND,HUVEC
    compound-001_11_U08,compound-001,11,U08,,EMPTY_control,,,COMPOUND,HUVEC
    compound-004_43_B08,compound-004,43,B08,,CRISPR_control,,,COMPOUND,HUVEC

## Images

The images are found in [Hugging Face](https://huggingface.co/datasets/recursionpharma/rxrx3-core/tree/main/data) using the [WebDataset](https://huggingface.co/docs/hub/en/datasets-webdataset#streaming) format.
The image data were compressed from their original format to 512x512 (center crops) 8-bit `jp2` files. The image file names, such as `AA02_s1_3.jp2`, can be read as:

Well location on plate (column AA, row 2)
Site (1)
Channel (3) 

All six channels (`1` - `6`) make up an single image of a given `site`. Note there is one site only for every well address.

Physical resolution: 0.65 micron/pixel.

## Deep Learning Embeddings

The deep learning embeddings are provided as `OpenPhenom_rxrx3_core_embeddings.parquet` and can be downloaded [from here](https://huggingface.co/datasets/recursionpharma/rxrx3-core/blob/main/OpenPhenom_rxrx3_core_embeddings.parquet) (this is ~ 532 MB).

Each row in the parquet file has a `well_id` as described in the metadata schema. The remaining 384 columns are the embedding for that respective well

## Accessing RxRx3-core through Hugging Face API

Loading the RxRx3-core image dataset. 
An example of running inference on this dataset with OpenPhenom is provided [here](https://huggingface.co/recursionpharma/OpenPhenom/blob/main/RxRx3-core_inference.ipynb).
```
from datasets import load_dataset
rxrx3_core = load_dataset("recursionpharma/rxrx3-core")
```
Loading OpenPhenom embeddings and metadata for RxRx3-core
```
from huggingface_hub import hf_hub_download
import pandas as pd

file_path_metadata = hf_hub_download("recursionpharma/rxrx3-core", filename="metadata_rxrx3_core.csv",repo_type="dataset")
file_path_embs = hf_hub_download("recursionpharma/rxrx3-core", filename="OpenPhenom_rxrx3_core_embeddings.parquet",repo_type="dataset")

open_phenom_embeddings = pd.read_parquet(file_path_embs)
rxrx3_core_metadata = pd.read_csv(file_path_metadata)
```
Benchmarking code for this dataset is provided in the [EFAAR benchmarking repo](https://github.com/recursionpharma/EFAAR_benchmarking/tree/trunk).



## Changelog:
- Nov 2024: initial release

## License

This work is licensed under <a rel="license" href="https://rxrx3.rxrx.ai/static/">Recursion Non-Commercial End User License Agreement</a>

[github]: https://github.com/recursionpharma/rxrx-datasets/
[rxrx]: https://rxrx.ai
[rxrx3]: https://rxrx.ai/rxrx3
[recursion]: https://recursion.com
[download]: https://rxrx3.rxrx.ai/downloads
