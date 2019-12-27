OSID=OS-XXXXX
TARGET=$(OSID)-final-report.7z
REPORT=$(OSID)-final-report.pdf
OTHER_FILES=
SOURCES=front-matter.md introduction.md $(shell ls ../machines/*/README.md) final-notes.md
COMPILED_SOURCE=$(OSID)-final-report.md

CODE_THEME=tango
PANDOC_FLAGS=--from markdown+yaml_metadata_block+raw_html \
			 --template "$(PWD)/eisvogel.tex" \
			 --table-of-contents \
			 --toc-depth 6 \
			 --number-sections \
			 --top-level-division=chapter \
			 --highlight-style $(CODE_THEME)

.PHONY: all clean

all: $(TARGET)

clean:
	rm -f $(TARGET) $(COMPILED_SOURCE) $(REPORT) 

$(TARGET): $(REPORT) $(OTHER_FILES)
	# Zip up the report and any other important files
	rm -f $(TARGET)
	7z a -p"$(OSID)" $@ $<

$(REPORT): $(COMPILED_SOURCE)
	# This is kind of hacky. It puts links to all the images in this directory.
	find img -type l | xargs rm -f
	ls ../machines/*/img/* | while read i; do ln -s "`realpath "$$i"`" "img/`basename "$$i"`"; done
	pandoc $< -o $@ $(PANDOC_FLAGS)

$(COMPILED_SOURCE): $(SOURCES)
	# Cat all the sources together (awk adds newlines if needed between files)
	awk '{ print $$0 }' $(SOURCES) > $@


