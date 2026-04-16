# Thesis titled "Thesis Title"

Welcome to my thesis.
This repository contains the latex files necessary to compile my thesis.
This thesis is composed of the following papers:

1. [LanDscAPe](https://www.usenix.org/conference/usenixsecurity24/presentation/kaspereit)
2. [LDAP-sequel](https://ieeexplore.ieee.org/document/11297453)
3. [DMARC](https://gustavoluvizotto.github.io/dmarc-aggr-report-dependency-tex/main.pdf)
4. [Services on Anycast](under-peer-review)

## Project structure

The files are divided into directories that help organize the thesis content.
I organize it as follows:

- ``. (this)``: this directory. It contains the ``Makefile`` required to compile, ``bibliography.bib`` with the bibl. content added to the thesis (which are not in the individual papers), the layout file (``phd_layout.sty``) and ``main.text`` which is the entry point of this thesis.
- ``texenv``: this contains the acronyms used by the glossary package (\gls), custom commands (\eg, \ie...), and the packages (\usepackage) required
- ``tables``: new tables that are not in the papers or modified versions of the papers' tables.
- ``figures``: similar to ``tables``.
- ``build``: this directory contains latex build output
- ``sections/``: contains the papers in directories and ``.tex`` files such as abstract, acks, background, conclusion, introduction and the chapters themselves.
- ``sections/ldap-1``: contains a copy of paper #1.  The changes made to the original content are also stored here
- ``sections/ldap-2``: contains a copy of paper #2.  The changes made to the original content are also stored here
- ``sections/dmarc``: contains a copy of paper #3.  The changes made to the original content are also stored here
- ``sections/anycast``: contains a copy of paper #4. The changes made to the original content are also stored here

Each chapter paper contain their own glossary and bibliography.
I deleted redundant items to enable compilation.

## Requirements

- make  
- latexmk  
- bibtex  
- git-latexdiff  

## Usage

To generate the paper's pdf, simply run:  
```shell
make
```

The build artifacts will be created and placed into the ``build`` directory.  

If you want to generate a ``diff`` between two pdfs, run the following:  
```shell
make diff from=COMMIT1 to=COMMIT2
```

Where ``COMMIT1`` and ``COMMIT2`` are commit hash, tag or git reference (e.g., HEAD).  

To clean the build artifacts and start a fresh build (due to any strange Latex error), run the following:  
```shell
make clean
```
