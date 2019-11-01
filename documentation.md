# Generating Documentation 
Nobody will use your code if it does not have documentation. 
This tutorial will show you how to:
- Create a folder for documentation-related code
- Use sphinx to generate documentation based on docstrings

### Requirements

Create a file in the top level of your repository called `docs`.

Create a file called `requirements.txt` in the `docs` folder. 

In the `requirements.txt` file, add the following dependencies: 
  
    sphinx==1.8.5
    sphinx_rtd_theme>=0.4.2
    sphinxcontrib-rawfiles
    numpydoc
    nbsphinx

These packages are required for building the documentation pages. 

Once you have created `requirements.txt`, navigate to `/docs` from the
command line and install these packages using `pip`: 

     pip3 install -r requirements.txt
     
In addition, you need to install `pandoc` for `nbsphinx`. `nbsphinx` will allow
you to use `jupyter` notebooks to make documentation tutorial pages.
If you are on linux, you can enter: 

    sudo apt-get install pandoc

If you are on macOS and have `homebrew` installed, you can enter:

    brew install pandoc

Otherwise, you can visit [pandoc installing page](https://pandoc.org/installing.html) for more information.

### File structure
The `docs` folder is where you will put everything `sphinx` needs to generate the documentation, 
aside from the docstrings themselves. 

### Generating the documentation

To build the HTML documentation, enter:

    make html

in the `doc/` directory. If all goes well, this will generate a `_build/html/` subdirectory containing the built documentation.
