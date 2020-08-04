# RxRx1 Data Dictionary

For more information about the dataset please visit [RxRx.ai](https://www.rxrx.ai/).

 * `recursion_dataset_license.pdf`: the license under which the dataset is released.
 * `images/*`: the image data in 8-bit png format. The image paths, such as `U2OS-01/Plate1/B02_s2_w3.png`, can be read as:
   * Experiment Name: Cell type and batch number (U2OS batch 1)
   * Plate number (1)
   * Well location on plate (column B, row 2)
   * Site (2)

 * `rxrx1.csv`: The metadata for the dataset with the following columns:
   * `site_id`: unique identifier of a given site
   * `well_id`: unique identifier of a given well
   * `cell_type`: the cell type
   * `dataset`: the split that this site belongs; train or test
   * `experiment`: the experiment name, same as explained above
   * `plate`: plate number within the experiment
   * `well`: location on the plate
   * `site`: indication of the location in the well where image was taken (1 or 2)
   * `well_type`: indicates if the well is a `treatment`, `negative_control`, or `positive_control`
   * `sirna`: the siRNA (ThermoFisher ID) that was introduced into the well
   * `sirna_id`: the siRNAs mapped to integers for ease of classification tasks