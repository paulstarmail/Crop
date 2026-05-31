# Image Batch Cropping Automation Script

## Description
This script automates the precise cropping of a batch of images located in an input directory. Instead of using pixel measurements, it allows the user to specify real-world metric dimensions (in millimeters) and a target DPI/PPI. It handles the mathematical conversion to pixels behind the scenes.

## Prerequisites
* **ImageMagick** must be installed on your system.
  * *Installation command:* `sudo apt install imagemagick`
* **bc** command-line calculator utility (standard on most Linux distros).

## Directory Structure
* **Input Folder:** `./input` (Drop your raw images here: JPG, PNG, TIFF, BMP)
* **Output Folder:** `./output` (Auto-created; saves results as `filename_cropped.ext`)

## Measurement Geometry
All measurements (Offsets X and Y) are calculated relative to the absolute **TOP-LEFT CORNER (0,0)** of the source image.

## How the Math Works
* $\text{Pixels per mm} = \text{DPI} / 25.4$ *(Since 1 inch = 25.4 millimeters)*
* $\text{Target Pixels} = \text{Dimension in mm} \times \text{Pixels per mm}$
* **ImageMagick Crop Syntax:** `convert <input> -crop {W}x{H}+{X}+{Y} <output>`

## Usage
1. Place your images in the `./input` directory.
2. Run the script: `./crop_images.sh`
3. Enter the requested DPI, Width (mm), Height (mm), X offset, and Y offset.
