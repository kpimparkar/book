NAME=e516
HOME=../..

all: syllabus epub pdf authors

draft: clean fonts version
	mkdir -p dest
	cat $(HOME)/bib/*.bib > dest/all.bib
	bookmanager $(NAME)-draft.yaml get
	mv dest/vonLaszewski-$(NAME)-draft.epub $(HOME)/docs
	-killall Books
	open $(HOME)/docs/vonLaszewski-$(NAME)-draft.epub

syllabus: clean fonts version
	mkdir -p dest
	cat $(HOME)/bib/*.bib > dest/all.bib
	bookmanager $(NAME)-syllabus.yaml get
	mv dest/vonLaszewski-$(NAME)-syllabus.epub $(HOME)/docs
	#killall Books
	#open $(HOME)/docs/vonLaszewski-$(NAME)-syllabus.epub

epub: clean fonts version
	mkdir -p dest
	cat $(HOME)/bib/*.bib > dest/all.bib
	bookmanager $(NAME).yaml get
	mv dest/vonLaszewski-$(NAME).epub $(HOME)/docs

pdf:
	ebook-convert \
	  $(HOME)/docs/vonLaszewski-$(NAME).epub \
	  $(HOME)/docs/vonLaszewski-$(NAME).pdf

bib:
	mkdir -p dest
	cp $(HOME)/bib/*.bib dest

version:
	TZ=":US/Eastern"; date > $(HOME)/chapters/version.md

view:
	-killall Books
	open $(HOME)/docs/vonLaszewski-$(NAME).epub

authors:
	$(HOME)/bin/authors.py > $(HOME)/chapters/authors.md

fonts:
	#mkdir -p dest/book/
	#-cp -r ../../../bookmanager/bookmanager/template/epub/fonts dest/book/fonts
	echo "ignoring font embedding"

clean:

	rm -rf dest

include ../Makefile.bibtex
