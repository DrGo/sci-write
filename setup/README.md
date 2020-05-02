# VDEC Scientific Writing Template

## How to use
- make a copy of this folder and change the folder name to a short descriptive name (see VDEC guidelines for file names).

## Folders
- setup/ holds files part of this template and can be deleted
- draft/ holds all markdown content files
- assets/ holds source files for figures, tables, images and appendixes 
- bib/ holds cls files and a link to VDEC's bibtex file
- shared/ output files shared with others.
- submitted/ output files used for journal, grant submission
- final/ final version

## Setup (once per machine)
### Install
- ideally a Unix-type system (MacOS, Linux, WSL v2)
- pandoc pandoc-citeproc
- vscode with the following extensions
  - https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one
  - https://marketplace.visualstudio.com/items?itemName=mblode.zotero
  - https://marketplace.visualstudio.com/items?itemName=sandcastle.vscode-open
  - https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker
  - https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker-medical-terms
- curl
- git
- make
  
### Zotero setup 
- download the latest version of Better BibTeX (BBT) xpi file from https://retorque.re/zotero-better-bibtex.
- click Tools-> Add-ons--> settings (Cogwheel button)-> Install add-on from file and select the xpi file downloaded above.
- click preferences-> Better BibTeX and set the following:
  - Citation key format => [auth:lower][year].
  - Force citation key to plain text => checked.
  - Keep keys unique=> within each library.
- select all references in the VDEC library window, right-click-> Better BibTeX-> Refresh BibTeX key (only once per library; already done by SM).
- click File-> Export Library: in the dialog:
  - Format => "Better BibLaTeX".
  - Keep updated => checked
  - click Ok. Save as "vdec.bib" in any folder in your local machine (for speed I store it in a RAM disk).
- click Preferences-> Better BibTeX and set the following:
  - Automatic export=> On change (to keep vdec.bib synced with any updates to Zotero) or On Idle (my preference).

## Configuring this repo (once per project)
- in Command: (soft) symlink the vdec.bib above to proposal/draft/vdec.bib (to avoid having different copies of vdec.bib but also make it accessible in the project folder and in vscode explorer).
- update draft/metadata.yaml with a title, authors etc.
- update README.md under the root folder with project name and description
- git init

## Workflow
- add references as needed to Zotero online library and will be replicated automatically to bib/ 
- edit markdown files as usual (add new files to SOURCE_FILES in the Makefile in the order you want them to appear in the final document)
- press alt+shift+z to search and insert citations (Zotero must be running) 
- run make, output will be saved as draft.rtf (see Makefile)
- use git tag to tag each version sequentially v1, v2, v3 etc eg `git tag -a v1.0 -m "version 1.0"` followed by `git push`
- see draft/Makefile for settings.

## TODO:
- expand Makefile to 
  - automate versioning, 
  - outputting shared and submitted files, 
  - version controls
  - downloading csl files etc
- standardize the metadata and automate the process of creating cover page
- automate creating funding sources, contributions etc.
- automate including tables, figures etc
- testing other output formats