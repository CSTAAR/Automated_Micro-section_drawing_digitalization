# Automated Micro-section drawing digitalization
Scripts for automated digitalization of hand-drawn micro-section profiles – from preprocessing to spatial database.

This repository contains a set of Python scripts developed to automate the digitalization of hand-drawn stratigraphic profiles, based on field documentation forms (microsondages) collected during archaeological excavations. While digital methods such as photogrammetry or tablet-based recording are becoming more common, analog, hand-drawn field documentation remains prevalent due to limitations in funding, expertise, or methodological preference.

The methodology was developed during the post-excavation analysis of a project conducted at the Dukovany site (Southern Moravia, Czech Republic), where 1,200 standardized forms required digitization. Manual vectorization of each form took approximately 3–4 minutes, totaling over 60 hours. The solution presented here reduces that effort significantly using Python and open-source libraries. This work was developed independently by the author, within the framework of a collaborative project with the Archaeological Institute of the Czech Academy of Sciences, Brno.

🧩 **Workflow Overview**
The process consists of four custom scripts, each responsible for a specific phase of the digitalization pipeline:

**Preprocessing and Renaming**

Deskews and rotates raw scanned images

Prepares standardized naming by extracting Section IDs (semi-automatic)

Improves data uniformity while allowing manual confirmation of IDs

**Georeferencing**

Rectifies images using a reference scale (SCALE.shp) corresponding to one meter

Assigns a custom coordinate system (not tied to real-world coordinates)

Organizes sections spatially in a virtual layout using systematic offsets

**Vectorization**

Crops section drawing region using template matching

Applies Canny edge detection and converts contours to polylines

Sorts and filters geometry, converts polylines into polygons

Associates vectorized features with the relevant Section ID

**Layer Attribution and Finalization**

Semi-automatically collects layer numbers and allows manual verification

Creates a bounding box around the digitized drawing

Integrates attribute data and completes the final dataset

⚠️ **Project-Specific Notes**
The workflow includes the use of SHP_SCALE.shp, a reference shapefile representing a 1-meter scale bar, which is required by the original project.

The scripts are tailored to the structure and requirements of the Dukovany dataset. For different use cases, minor adjustments might be needed—such as adapting to new form layouts, OCR styles, or database schemas.

To save time and improve efficiency, parts of the debugging process and final code refinements were assisted by ChatGPT-4o, particularly in optimizing logic, handling edge cases, and improving code readability.

If you are interested in adapting this solution to your own dataset or would like to discuss potential use cases, feel free to contact me. I'm happy to provide advice or collaborate on customized implementations.

📦 **Requirements**
Main libraries used:

- opencv-python

- geopandas

- shapely

- numpy

- pandas

- matplotlib

▶️ **How to Run**
The scripts are designed to be executed in a Python environment with support for interactive workflows – such as Jupyter Notebook, which was used during development and testing. Each script represents a step in the pipeline and builds upon the outputs of the previous one. Therefore, they should be run in sequence, following the logical structure of the workflow.

**Execution Notes:**
General parameters (e.g., input and output file paths) must be set manually at the beginning of each script.

Each script also includes script-specific parameters, such as thresholds, coordinate offsets, or filter settings, which are explained in the comments at the top of the script files.

The code is written to be as flexible as possible while remaining aligned with the data structure and workflow of the original project.

**Included Example:**
To assist with testing and orientation, the repository includes a sample form (sample_form.jpg) derived from the Dukovany Project. This example allows users to verify that the scripts are working correctly and also provides insight into the structure and assumptions the code is based on.

For best results, ensure your environment has all the required dependencies (see Requirements), and run the scripts step by step, inspecting the intermediate results as needed.

📖 **Citation / Acknowledgement**

If you use any part of this code or workflow in your research, publication, or project,  
please acknowledge the author. A suggested citation format:

> Hájek, F. (2025). *Automated digitalization of hand-drawn micro-section profiles*. GitHub repository.  
> Available at: https://github.com/CSTAAR/Automated_Micro-section_drawing_digitalization [Accessed: date].

Alternatively, feel free to contact me to discuss proper citation, adaptation to your dataset, or potential collaboration.
