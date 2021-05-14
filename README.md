# Star Galaxy Classification with Zwicky Transient Facility (ZTF) data

This repo demonstrates how to run our LLNL developed classification tecquniques (explain GP stuff) on ZTF cutouts. Notebooks showing how we generate the cutouts are also available. 

**For more information about ZTF:**
https://www.ztf.caltech.edu

**For more information on MuyGPyS:**
- https://arxiv.org/pdf/2104.14581.pdf
- https://arxiv.org/pdf/2105.01106.pdf


## Install Dependencies:
- Clone and install MuyGPyS with:

        $ git clone [ink]

    - [Add installation instructions and link to README]

- Install needed python packages

        $ pip install -r requirements.txt

## Optional Notebooks:
To see how astronomers curate datasets (by applying various cuts, cross-matching catalogs, etc) or how we generate ZTF cutouts, run through the following notebooks in order:

1. `getting_object_positions.ipynb`:
   - Generating ZTF cutouts requires knowing the objects position, and classification requires having truth labels ('star', 'galaxy'). ZTF catalogs do *not* include type labels, so we are unable to identify objects in the catalog as stars or galaxies. 
   - This notebook demonstrates how to get type labels and positions from another survey, and make relevant data cuts, so that we have a list of objects (with truth labels) in which we can generate ZTF cutouts for. 
2. `generating_ZTF_cutouts.ipynb`:
   - This notebook demonstrates how to generate ZTF cutouts for each object from the previous notebook.

## Star Galaxy Classification:
If you don't care to see the data curation steps, and want to skip straight to the pre-made ZTF cutouts inside `cutouts/`, you are ready to run through the following notebooks in order:

1. `data_normalization.ipynb`:
   - This notebook demonstrates different techniques for normalizing data in preperation for machine learning algorithms and flattens the image data into the proper input for the classifier.
2. `star_gal_classification.ipynb`:
   - This notebook runs the classifier on 5 different types of data (normalized and raw), and compares the classifying accuracies. 


Check back soon as were working on asteroid classification as well!




