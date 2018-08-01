Instalacja
**********

Instalacja i konfiguracja Sphinx
================================

::

 $ sudo pip install sphinx 

1. Klonujemy repo
2. Z command line:

::

 $ cd [nazwa_repo]
 $ mkdir doc
 $ cd doc
 $ sudo sphinx-quickstart 
 
 
 Welcome to the Sphinx 1.7.6 quickstart utility.
 
 Please enter values for the following settings (just press Enter to
 accept a default value, if one is given in brackets).
 
 Selected root path: .
 
 You have two options for placing the build directory for Sphinx output.
 Either, you use a directory "_build" within the root path, or you separate
 "source" and "build" directories within the root path.
 > Separate source and build directories (y/n) [n]: y
 
 Inside the root directory, two more directories will be created; "_templates"
 for custom HTML templates and "_static" for custom stylesheets and other static
 files. You can enter another prefix (such as ".") to replace the underscore.
 > Name prefix for templates and static dir [_]:
 
 The project name will occur in several places in the built documentation.
 > Project name: name
 > Author name(s): autor
 > Project release []: 1.0.0
 
 If the documents are to be written in a language other than English,
 you can select a language here by its language code. Sphinx will then
 translate text that it generates into that language.
 
 For a list of supported codes, see
 http://sphinx-doc.org/config.html#confval-language.
 > Project language [en]:
 
 The file name suffix for source files. Commonly, this is either ".txt"
 or ".rst".  Only files with this suffix are considered documents.
 > Source file suffix [.rst]:
 
 One document is special in that it is considered the top node of the
 "contents tree", that is, it is the root of the hierarchical structure
 of the documents. Normally, this is "index", but if your "index"
 document is a custom template, you can also set this to another filename.
 > Name of your master document (without suffix) [index]:
 
 Sphinx can also add configuration for epub output:
 > Do you want to use the epub builder (y/n) [n]:
 Indicate which of the following Sphinx extensions should be enabled:
 > autodoc: automatically insert docstrings from modules (y/n) [n]: y
 > doctest: automatically test code snippets in doctest blocks (y/n) [n]:
 > intersphinx: link between Sphinx documentation of different projects (y/n) [n]:
 > todo: write "todo" entries that can be shown or hidden on build (y/n) [n]:
 > coverage: checks for documentation coverage (y/n) [n]:
 > imgmath: include math, rendered as PNG or SVG images (y/n) [n]:
 > mathjax: include math, rendered in the browser by MathJax (y/n) [n]:
 > ifconfig: conditional inclusion of content based on config values (y/n) [n]:
 > viewcode: include links to the source code of documented Python objects (y/n) [n]: y
 > githubpages: create .nojekyll file to publish the document on GitHub pages (y/n) [n]:
 
 A Makefile and a Windows command file can be generated for you so that you
 only have to run e.g. `make html' instead of invoking sphinx-build
 directly.
 > Create Makefile? (y/n) [y]: y
 > Create Windows command file? (y/n) [y]: y
 
 Creating file ./source/conf.py.
 Creating file ./source/index.rst.
 Creating file ./Makefile.
 Creating file ./make.bat.
 
 Finished: An initial directory structure has been created.
 
 You should now populate your master file ./source/index.rst and create other documentation
 source files. Use the Makefile to build the docs, like so:
   make builder
 where "builder" is one of the supported builders, e.g. html, latex or linkcheck.

3. Instalujemy motyw 'ReadTheDocs' dla Sphinxa:

::

 $ pip install sphinx_rtd_theme

4. Edytujemy ``/doc/source/conf.py`` :

::

 $ html_theme = 'sphinx_rtd_theme'

a nastepnie komentujemy nastepujacy fragment:

::

 #html_sidebars = {
 #    '**': [
 #        'about.html',
 #        'navigation.html',
 #        'relations.html',  # needs 'show_related': True theme option to display
 #        'searchbox.html',
 #        'donate.html',
 #    ]
 #}

5. Wchodzimy do ./doc/source

| w index.rst:
| wyrzucamy ``Indices and tables`` i wszystko poniżej edytujemy według poniższego wzorca:

::

 [nazwa_dokumentacji]
 ====================
 
 .. toctree::
   :maxdepth: 2
   :caption: [tytuł sekcji]
 
   [pliki .rst z dokumentacja]
   [kolejny plik]
   [nastepny plik]

Instalacja pdflatex i potrzbenych paczek
========================================

::

 $ sudo apt-get install texlive-latex-base
 $ sudo apt-get install texlive-latex-extra
 $ sudo apt-get install texlive-fonts-recommended

Sphinx-versioning
=================

Instalacja
----------

::

 $ sudo pip install sphinxcontrib-versioning


Przystosowanie versioningu do sphinxa 1.6+
------------------------------------------

w pliku : ``/usr/local/lib/python2.7/dist-packages/sphinxcontrib/versioning/sphinx_.py``

zmieniamy:

::

 app.config.html_sidebars['**'] = StandaloneHTMLBuilder.default_sidebars + ['versions.html']

na:

::

 app.config.html_sidebars['**'] = ['versions.html']

Tworzenie wersji dokumentacji
-----------------------------

Bedac na wybranym branchu gita: (git checkout)

1. Zmiany w lokalnym repozytorium
2. Lokalna dokumentacja

::

 ..<repo>/doc/$ make html

3. Wypchniecie zmian na remote repozytorium (git push)
4. Stworzenie lokalnie wersji dokumentacji

W katalogu root dla repozytorium git:

::

 ../<repo>$ sphinx-versioning build ./doc/source/ ./doc/build/html 

5. Wypchniecie nowej dokumentacji na remote repo (git push)

.. warning:: Nalezy najpierw pushowac zmiany a nastepnie lokalnie tworzyc wersje dokumentacji, w innym przypadku zmiany nie beda widoczne (versioning ignoruje commit,stash itd)!


Tworzenie HMTL
==============

::

 w /doc :
 make html 

 w /doc/build/html :
 dokumentacja dostepna w index.html 

Tworzenie PDF
=============

:: 

  w /doc : 
  make latex
 
  w /doc/build/latex : 
  pdflatex [nazwa].tex 
  makeindex -s python.ist [nazwa].idx
  pdflatex [nazwa].tex




