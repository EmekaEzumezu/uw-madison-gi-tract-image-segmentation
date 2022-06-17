# The goal of the project:
Instead of manually outlining and segmenting the tumor and the stomach this will lead to delayed treatment of patients. A deep learning model is employed to automatically segment the tumor and stomach region to help the urologist know the region where a high dose of radiation will be applied to the tumor and the region for the low-level radiation to be applied while making sure the stomach is entirely avoided.

### Data Description:
The goal here is to segment organ cells in images. The training annotations are provided as RLE-encoded masks, and the images are in 16-bit grayscale PNG format.

The goal of this project is to be able to generalize to both partially and wholly unseen cases, which is always a good practice. Each case (whereby each case represents a single patient) in this project is represented by multiple sets of scan slices "of the patient" (each set is identified by the day the scan took place "- i.e collections of daily scans of the patient"). Some cases are split by time (early days are in train, later days are in test) " - i.e splitting patients scanned images and placing the early days in the train set and later days in test set" while some cases are split by case - the entirety of the case is in train or test. I.e some patients scanned images are in the train set while some are in the test set.

Note that, in the case of this project/competition, the test set is entirely unseen. It is roughly 50 cases, with varying days and slices, as seen in the training set.

How the entirely hidden test set work:
The test set in this project/competition is only available when the code is submitted. The sample_submission.csv is an empty placeholder that shows the required submission format; modeling, cross-validation, etc., will be performed using the training set, and code will be written to process a non-empty sample submission. It will contain rows with id, class, and predicted columns. When the notebook is submitted, the code will be run against the non-hidden test set, which has the same folder format (//) as the training data.

Files:
* train.csv - IDs and masks for all training objects.
* sample_submission.csv - a sample submission file in the correct format
* train - a folder of case/day folders, each containing slice images for a particular case on a given day.
Note that the image filenames include 4 numbers (ex. 276_276_1.63_1.63.png). These four numbers are slice height / width (integers in pixels) and heigh/width pixel spacing (floating points in mm). The first two defines the resolution of the slide. The last two record the physical size of each pixel.

Physical pixel thickness in superior-inferior direction is 3mm.

Columns:
* id - unique identifier for object
* class - the predicted class for the object
* EncodedPixels - RLE-encoded pixels for the identified object