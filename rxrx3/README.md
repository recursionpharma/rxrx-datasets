# RxRx3

At Recursion, we build maps of biology and chemistry to explore uncharted areas of disease biology, unravel its complexity, and industrialize drug discovery. Just as a map helps to navigate the physical world, our maps are designed to help us understand as much as we can about the connectedness of human biology so we can navigate the path to new medicines more efficiently.

Our maps are built using image-based high-dimensional data generated in-house. We conduct up to 2.2 million experiments every week in our highly automated labs, where we use deep learning models to embed high dimensional representations of billions of images of human cells that have been manipulated by CRISPR/Cas9-mediated gene knockouts, compounds, or other reagents. This allows us to create representations that can be compared and contrasted to predict trillions of relationships across biology and chemistry — even without physically testing all of the possible combinations. Recursion's Maps and associated applications help navigate complex biology and chemistry by revealing relationships across genes and chemical compounds.

RxRx3 is a publicly available map of biology that represents a small subset – less than 1% – of Recursion’s total dataset. MolRec™️ is a simple demo example of such an application that can be built on this type of map.

For more information about RxRx3 please visit [RxRx.ai/rxrx3][rxrx3]

RxRx3 is part of a larger set of [Recursion][recursion] datasets that can be found at [RxRx.ai][rxrx] and on [GitHub][github]. For questions about this dataset and others please email [info@rxrx.ai](mailto:info@rxrx.ai).

# Compound and Gene identifiers

The RxRx3 release contains 17,063 genes, as well as 1,674 known chemical entities at 8 doses each. 16,328 of these genes are anonymized in the dataset, enabling people to explore and learn from this massive dataset while protecting Recursion’s business interests. Recursion may de-anonymize genes in this dataset in the future. If you'd like to understand more about how to get access to unblinded genes please email [info@rxrx.ai](mailto:info@rxrx.ai).

## Metadata

The metadata can be found in `metadata.csv` and downloaded [from here][download]. The schema of the metadata is as follows:

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

The images are found in `images/*` and can be downloaded [from here][download] (this is ~ 83 TB).
The image data are 2048x2048 16-bit `png` files. These can be downloaded by experiment plate. We provide a tar file for each experiment and plate, with each image from the experiment plate in the tar file. The image file names, such as `AA02_s1_w3.png`, can be read as:

Well location on plate (column AA, row 2)
Site (1)
Channel (3) 

All six channels (`w1` - `w6`) make up an single image of a given `site`. Note there is one site only for every well address.

## Deep Learning Embeddings

The deep learning embeddings are provided as `embeddings.tar` and can be downloaded [from here][download] (this is ~ 1.82 GB).

Embeddings path is similar to the images path structure. Ex: `gene-001/Plate1/embeddings.parquet`

Each row in the parquet file has a `well_id` as described in the metadata schema. The remaining 128 columns are the embedding for that respective well


## Changelog:
- January 2023: initial release

## License

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.

[github]: https://github.com/recursionpharma/rxrx-datasets/
[rxrx]: https://rxrx.ai
[rxrx3]: https://rxrx.ai/rxrx3
[recursion]: https://recursion.com
[download]: https://rxrx3.rxrx.ai/downloads
