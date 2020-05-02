FORMAT := rtf
BIBLIOGRAPHY := bib/vdec.bib
CSL := international-journal-of-cancer.csl
OUTPUT := draft.$(FORMAT)
SOURCE_FILES := cover-page.md abstract.md background.md methods.md results.md discussion.md team.md
MERGED := merged.md

.PHONY : all clean setup

all: $(OUTPUT)

$(MERGED): $(SOURCE_FILES)
	cat $(SOURCE_FILES) > $@
	printf "\n# References\n" >>$@

$(OUTPUT): $(MERGED)
	pandoc --from=markdown $(MERGED) --to=$(FORMAT) --output=$(OUTPUT) \
			--metadata-file=metadata.yaml --standalone \
			--filter=pandoc-citeproc \
			--csl=../bib/$(CSL) \
    	--bibliography=$(BIBLIOGRAPHY) 

setup:
	curl -J https://raw.githubusercontent.com/citation-style-language/styles/master/$(CSL) -o ../bib/$(CSL)

clean:
	rm  $(MERGED) $(OUTPUT) 

# do not use
__sm:
			--variable mainfont="DejaVu Sans" \
			--variable monofont="DejaVu Sans Mono" \
			--variable fontsize=11pt \
			--variable geometry:"top=1.5cm, bottom=2.5cm, left=1.5cm, right=1.5cm" \
			--variable geometry:a4paper \
			--table-of-contents
			--filter pandoc-citeproc-preamble \ 

			latest=$(git tag  -l --merged master --sort='-*authordate' | head -n1)