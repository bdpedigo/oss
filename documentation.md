# Generating Documentation 
Nobody will use your code if it does not have documentation. 
This tutorial will show you how to use sphinx to generate documentation based on 
docstrings in your code, and how to host them on `netlify`. For a tutorial on how to 
write the docstrings themselves, see `x`.

### Requirements

Create a file in the top level of your repository called `docs/`.

Create a file called `requirements.txt` in the `docs/` folder. 

In the `requirements.txt` file, add the following dependencies: 
  
    sphinx==1.8.5
    sphinx_rtd_theme>=0.4.2
    sphinxcontrib-rawfiles
    numpydoc
    nbsphinx

These packages are required for building the documentation pages. 

Once you have created `requirements.txt`, navigate to `docs/` from the
command line and install these packages using `pip`: 

     pip3 install -r requirements.txt
     
In addition, you need to install `pandoc` for `nbsphinx`. `nbsphinx` will allow
you to use `jupyter` notebooks to make documentation tutorial pages. If you don't want 
to have `jupyter` notebooks in your documentation yet, you can skip this step for now.

If you are on linux, you can enter: 

    sudo apt-get install pandoc

If you are on macOS and have `homebrew` installed, you can enter:

    brew install pandoc

Otherwise, you can visit [pandoc installing page](https://pandoc.org/installing.html) 
for more information.

### File structure
The `docs` folder is where you will put everything `sphinx` needs to generate the 
documentation, aside from the docstrings themselves. 

### Sphinx-quickstart
On the command line, type

    sphinx-quickstart
  
You will now be prompted with a series of questions, the default parameter is listed
inside the `[]`. For most of these, I just hit enter to keep the default value: 

    > Separate source and build directories (y/n) [n]:
    > Name prefix for templates and static dir [_]:
    > Project name: {type your project name here}
    > Author name(s): {type your author names}
    > Project release: {0.1 is a good start}
    > Project language [en]:
    > Source file suffix [.rst]:
    > Name of your master document (without suffix) [index]:
    > autodoc: automatically insert docstrings from modules (y/n) [n]:
    > doctest: automatically test code snippets in doctest blocks (y/n) [n]: y
    > intersphinx: link between Sphinx documentation of different projects (y/n) [n]: y
    > todo: write "todo" entries that can be shown or hidden on build (y/n) [n]:
    > coverage: checks for documentation coverage (y/n) [n]: y
    > imgmath: include math, rendered as PNG or SVG images (y/n) [n]:
    > mathjax: include math, rendered in the browser by MathJax (y/n) [n]: y
    > ifconfig: conditional inclusion of content based on config values (y/n) [n]:
    > viewcode: include links to the source code of documented Python objects (y/n) [n]: y
    > githubpages: create .nojekyll file to publish the document on GitHub pages (y/n) [n]:
    > Create Makefile? (y/n) [y]:
    > Create Windows command file? (y/n) [y]:

Several files should have been created. Let's look at `index.rst` and start by adding a
simple page for the package licence. 

Choose a license for your package 
(for example, [Apache](https://www.apache.org/licenses/LICENSE-2.0.txt)).

Create a file in the `docs/` folder called `license.rst` and add the following text:

    License
    =======
    {package name} is distributed with the {name of license goes here} license.

    ::
    
    {text of the license goes here}
    


### Generating the documentation

Now, lets see what the output of `sphinx` looks like. To build the HTML documentation,
type:

    make html

in the `doc/` directory. If all goes well, this will generate a `_build/html/` 
subdirectory containing the built documentation. You can open the HTML file `index.html`
to see what the home page of your documentation will look like. You should notice a
`License` link on the left hand side of the page.
