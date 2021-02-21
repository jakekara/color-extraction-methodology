![Image](./out/sample/no_background/no_background-sample.jpg.png)

# ColorBook  

A color extraction project using modular notebooks  

## Modular notebooks

This repository is meant to demonstrate the power of modular notebooks to write robust, modular software entirely in notebooks.  

One of the goals of modular notebooks is that the entire methodology is self-documenting, so if you just want to see the color extraction business, jump into [Main.ipynb](./Main.ipynb).

Modularity is important to writing robust software because it allows us to focus on individual parts of the whole. Dijkstra referred to this as XX.  

You can understand the system as whole by reading the [Main.ipynb](./Main.ipynb) notebook. This Notebook merely orchestrates other notebooks to download and process our data. If you want to learn more about any individual step, you can read the notebooks which this one stitches together.

For example, if you want to see how the background deletion process works, you can open [background_deletion/LightnessPixelFilter.ipynb](background_deletion/LightnessPixelFilter.ipynb) and see its code.  

Typically, the code to filter pixels based on lightness would be written as a helper library in a `.py` file, but since we are using modular notebooks, this code is in a notebook, which means it has all of the rich documentation and sample outputs that you would expect in a notebook. The hope is that by keeping more of a methodology's code in notebooks, it's more accessible for anyone wishing to inspect it, reproduce, or learn from it in any way.

Another benefit of this modular organization of notebooks is that no code gets left behind when we move from "scratch" code in notebooks to production code in `.py` files. That means all of the code we tried but didn't use is still up for inspection. We tried four different color extraction algorithms and only used one in production. You can see them all in the [color_extraction](./color_extraction) folder, as well as a head-to-head comparison in the notebook [color_extraction/CompareExtractorAlgorithms.ipynb](color_extraction/CompareExtractorAlgorithms.ipynb).

## Margo

This repository makes extensive use of the the library [margo-loader](https://github.com/margo-notebooks/margo-loader-py) to implement modular notebooks.  

Margo was developed by Jake Kara, as a part of a software engineering thesis research project. This modular notebook collection is part of that thesis as well.  

Because notebooks include code that you might not want to import when you're treating it as a module, Margo lets you mark cells to be ignored during import. Margo can be used for many other things, but that's its role in this repository. You may see code like:

```python
import margo_loader
```

By including this line a Notebook, you can import other Notebook files as if they were `.py` modules.

You might also see code like this at the top of a cell:

```python
# :: ignore-cell ::
```

That means `margo_loader` will ignore that cell during import.

## Color extraction  

The methods for background deletion and color extraction implemented in these notebooks were originally written for an experiment of the Yale Digital Humanities Lab, where Jake works as a developer. These methods were adapted as modular notebooks for this repository in order to demonstrate the utility of modular notebooks to document a robust software methodology in Notebooks alone.  

Images in this repository, both the sample image and those which are downloaded when the code is run, are in the public domain.  