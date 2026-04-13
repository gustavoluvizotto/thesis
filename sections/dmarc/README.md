# Latex source code for the "Longitudinal Analysis of DMARC across country code Top-Level Domains" paper

## SW Requirements  
- make  
- latexmk  
- bibtex  
- git-latexdiff  

It has been tested on MacOS, but it should work as well on any Linux distribution with the above SW installed.  

## Usage  
To generate the paper's pdf, simply run:  
```
make
```

The build artifacts will be created and placed into the ``build`` directory.  

If you want to generate a ``diff`` between two pdfs, run the following:  
```
make diff from=COMMIT1 to=COMMIT2
```

Where ``COMMIT1`` and ``COMMIT2`` are commit hash, tag or git reference (e.g., HEAD).  

To clean the build artifacts and start a fresh build (due to any strange Latex error), run the following:  
```
make clean
```
