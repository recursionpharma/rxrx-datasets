# RxRx1

RxRx1 is the first dataset released by [Recursion][recursion] in the [RxRx.ai][rxrx] series
and was the topic of the NeurIPS 2019 CellSignal competition. It contains 125,510 images
of 6-channel fluorescent cellular microscopy, taken from four kinds of cells perturbed by
1,138 siRNAs. The goal of the competition was to train models that could identify which
siRNA was used in a given image taken from an experimental batch not seen in the training data.
For more information about RxRx1 please visit [RxRx.ai][rxrx1].

RxRx1 is part of a larger set of Recursion datasets that can be found at [RxRx.ai][rxrx] and on
[GitHub][github]. For questions about this dataset and others please email
[info@rxrx.ai](mailto:info@rxrx.ai).


## Metadata

The metadata can be found in `metadata.csv` and downloaded [from here][download]. The schema of the metadata
is as follows:

| Attribute      | Description                                                                     |
|----------------|---------------------------------------------------------------------------------|
| site_id        | Unique identifier of a given site                                               |
| well_id        | Unique identifier of a given well                                               |
| cell_type      | Cell type tested                                                                |
| dataset        | The split that this site belongs to; `train` or `test`                          |
| experiment     | The experiment name, same as explained above                                    |
| plate          | Plate number within the experiment                                              |
| well           | Location on the plate                                                           |
| site           | Indication of the location in the well where image was taken (1 or 2)           |
| well_type      | Indicates if the well is a treatment, `negative_control`, or `positive_control` |
| sirna          | The siRNA (ThermoFisher ID) that was introduced into the well                   |
| sirna_id       | The siRNAs mapped to integers for ease of classification tasks                  |

## Images

The images are found in `images/*` and can be downloaded [from here][download] (*n.b* this is 47GB).
The images are 512x512 8-bit `png` files. The image paths, such as `HUVEC-1/Plate1/M23_s2_w3.png`,
can be read as:

- Experiment Name: Cell type and experiment number (HUVEC experiment 1)
- Plate Number: 1
- Well location on plate: column M, row 23
- Site: 2
- Channel: 3

All six channels (`w1` - `w6`) make up a single image of a given site.

## Changelog
- June 2019: original release for CellSignal; train images only
- December 2019: updated to include test images after completion of CellSignal competition
- August 2020: file organization updated and license changed to CC-BY-NC-SA

## License
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a>

This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>. To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.


[download]: https://rxrx.ai/rxrx1#Download
[github]: https://github.com/recursionpharma/rxrx-datasets
[recursion]: http://recursionpharma.com
[rxrx]: http://rxrx.ai
[rxrx1]: https://rxrx.ai/rxrx1
