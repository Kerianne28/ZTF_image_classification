# Zwicky Transient Facility (ZTF) Image Classification Using MuyGPS

This repo demonstrates how to use the LLNL developed Gaussian process hyperparameter estimation method, MuyGPS, for image classification using ZTF data.

**For more information about ZTF:**
https://www.ztf.caltech.edu

**For more information on MuyGPS:**
- MuyGPS method paper: https://arxiv.org/pdf/2104.14581.pdf
- Paper on using the MuyGPS method for star/galaxy classification: https://arxiv.org/pdf/2105.01106.pdf

***

# Install Dependencies:

### <u>1. MuyGPyS</u>
- MuyGPyS is a python package that uses the MuyGPS method for image classification.
- **Clone MuyGPyS**:
- ***Note***: We are just waiting on this package to get through IM. Once it is through, the link will be put here and directions on how to install will be provided.

         $ git clone [link]

- **Install MuyGPyS**:

         $ [Insert steps to installing MuyGPyS]

   - Use the README ([link]) for complete installation instructions and package information.

### <u>2. Python dependencies</u>
- Install all needed python packages using pip:

        $ pip install -r requirements.txt

### <u>3. Jupyter notebook</u>
- Jupyter notebook was installed in step 2.
- To run the notebooks:
   - Change directories to `ZTF_image_classification/`, and run jupyter notebook:

         $ cd [/path/to/ZTF_image_classification]
         $ jupyter notebook

### <u>4. Setting up ztfquery</u>
- ztfquery was installed in step 2, but if you will be using notebook 2 to create cutouts yourself, you will need to set up your IRSA account:
   - Make an account at this website: https://irsa.ipac.caltech.edu/frontpage/
   - The first time you run ztfquery in the notebook, you will be asked for your username and password. (This should only happen once).
   - If you are having any issues, you can also add the following argument to `ztfquery.load_metadata` (in notebook 2):

         auth=['your_username', 'your_password']


***
# Running Star Galaxy Classification:

**To skip to the normalization and classification steps using our pre-made ZTF cutouts, skip to notebook 3.**

**Or, if you are interested in any of the following, start with notebook 1**:
   - How astronomers curate datasets (by applying cuts, cross-matching catalogs, etc)
   - How we generated the ZTF cutouts
   - You have finished notebook 4 and want to tweak parameters, create more cutouts, etc

1. `getting_object_positions.ipynb`:
   - **Optional**
   - Classifying and generating ZTF cutouts requires knowing object positions and truth labels ('star' or 'galaxy'). Because ZTF catalogs do *not* include type labels, we must identify object types and positions an alternate way.
   - This notebook demonstrates how to get type labels and object positions from another survey, and make relevant data cuts, so that we have a list of objects (with truth labels) in which we can generate ZTF cutouts for. 
   - This notebook also contains information on many background astronomy topics including RA/DEC, magnitude/flux, and blending.
   - Outputs: `stars.csv` and `gals.csv`, with columns RA, DEC, and type.
2. `generating_ZTF_cutouts.ipynb`:
   - **Optional**
   - This notebook demonstrates how to generate ZTF cutouts for each object from the previous notebook.
   - Outputs: Cutouts in the form of .fits images to `cutouts_test/`
3. `data_normalization.ipynb`:
   - This notebook demonstrates applying various data normalization techniques (an important step for use in machine learning algorithms), and transforms the data into the proper format for our classifier.
   - Outputs: Multiple .csv files containing flattened image data and truth labels. 
4. `star_gal_classification.ipynb`:
   - Must have run notebook 3 first.
   - This notebook runs the MuyGPyS classifier on 5 different types of data (normalized and raw), and compares the classification accuracies. 






