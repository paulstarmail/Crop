SCRIPT NAME: Millimeter-to-Pixel Image Batch Cropper
DESCRIPTION:
  This script automates the precise cropping of a batch of images located in
  an input directory. Instead of using pixel measurements, it allows the user
  to specify real-world metric dimensions (in millimeters) and a target DPI/PPI.
  It handles the mathematical conversion to pixels behind the scenes.
PREREQUISITES:
  - ImageMagick must be installed on your system.
    Installation command: sudo apt install imagemagick
  - 'bc' command-line calculator utility (standard on most Linux distros).
DIRECTORY STRUCTURE:
  - Input Folder:  './input'  (Drop your raw images here: JPG, PNG, TIFF, BMP)
  - Output Folder: './output' (Auto-created; saves results as 'filename_cropped.ext')
MEASUREMENT GEOMETRY:
  All measurements (Offsets X and Y) are calculated relative to the absolute
  TOP-LEFT CORNER (0,0) of the source image.
HOW THE MATH WORKS:
  - Pixels per mm = DPI / 25.4 (Since 1 inch = 25.4 millimeters)
  - Target Pixels = Dimension in mm * Pixels per mm
  - ImageMagick Crop Syntax: convert <input> -crop {W}x{H}+{X}+{Y} <output>
USAGE:
  1. Place your images in the './input' directory.
  2. Run the script: ./crop_images.sh
  3. Enter the requested DPI, Width (mm), Height (mm), X offset, and Y offset.
