# ColorBook  

A Notebook workflow for processing and extracting small palettes from images.

**DEPENDENCY: Note, this repo relies on an alpha package, margo_loader. to install it use:**

```bash
pip install -q git+https://github.com/margo-notebooks/margo-loader-py
```

## Extractors

Classes implementing different color quantization algorithms.

### ColorThiefExtractor

A wrapper for the colorthief library.

### MMCQExtractor

A wrapper for the median cut algorithm from colorthief library, without preprocessing that colorthief imposes, and without the requirement to read images from disk.

### CV2KMeansExtractor

A wrapper for the cv2 library's k-means algorithm.

### MeanShiftExtractor

A wrapper for the scikit-learn MeanShift algorith. Doesn't work well.

## PixelFilters

Classes for processing the image pixel by pixel.

### LightnessPixelFilter

A class that sets alpha channel to 0 for pixels outside of acceptable lightness threshold. This is useful for "deleting" the paper color form source images, which are ink and watercolor on paper.

