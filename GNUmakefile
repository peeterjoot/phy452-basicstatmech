THISDIR := phy452-basicstatmech
THISBOOK := phy452

BIBLIOGRAPHY_PATH := classicthesis_mine
HAVE_OWN_CONTENTS := 1
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/Index.tex
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/ContentsAndFigures.tex
BOOKTEMPLATE := ../latex/classicthesis_mine/ClassicThesis2.tex

include make.revision
include ../latex/make.bookvars

FIGURES := ../figures/phy452-basicstatmech

# comment this out for online pdf version (uncomment for KDP)
#PRINT_VERSION := 1

ifndef PRINT_VERSION
PARAMS += --no-print
endif
ifdef PRINT_VERSION
DISTEXTRA := kdp
endif

SOURCE_DIRS += appendix
SOURCE_DIRS += $(FIGURES)
#SOURCE_DIRS += solutions

GENERATED_SOURCES += mathematica.tex 
GENERATED_SOURCES += backmatter.tex
 
#GENERATED_PDFS += basicStatMechProblemSet1.pdf
#GENERATED_PDFS += basicStatMechProblemSet2.pdf
#GENERATED_PDFS += basicStatMechProblemSet3.pdf
#GENERATED_PDFS += basicStatMechProblemSet4.pdf
#GENERATED_PDFS += basicStatMechProblemSet5.pdf
#GENERATED_PDFS += basicStatMechProblemSet6.pdf
#GENERATED_PDFS += basicStatMechProblemSet7.pdf
#GENERATED_PDFS += huang93.pdf

HUANG93_DEPS += $(FIGURES)/huang93Fig3.pdf
HUANG93_DEPS += $(FIGURES)/huang93Fig4.pdf
HUANG93_DEPS += $(FIGURES)/huang93Fig2.pdf
HUANG93_DEPS += $(FIGURES)/huang93Fig6.pdf

#THISBOOK_DEPS += $(HUANG93_DEPS)
THISBOOK_DEPS += $(FIGURES)/stirlingErrorFig3.pdf

EPS_FILES := $(wildcard $(FIGURES)/*.eps)
PDFS_FROM_EPS := $(subst eps,pdf,$(EPS_FILES))

THISBOOK_DEPS += $(PDFS_FROM_EPS)

DO_SPELL_CHECK := $(shell cat spellcheckem.txt)

include ../latex/make.rules

.PHONY: spellcheck
spellcheck: $(patsubst %.tex,%.sp,$(filter-out $(DONT_SPELL_CHECK),$(DO_SPELL_CHECK)))

%.sp : %.tex
	spellcheck $^
	touch $@

#$(THISBOOK).pdf :: classicthesis.sty
#
#classicthesis.sty: ../latex/classicthesis/classicthesis.sty
#	cp ../latex/classicthesis/classicthesis.sty .

basicStatMechProblemSet1.pdf :: basicStatMechProblemSet1Problem1.tex
basicStatMechProblemSet1.pdf :: basicStatMechProblemSet1Problem2.tex

basicStatMechProblemSet2.pdf :: basicStatMechProblemSet2Problem1.tex
basicStatMechProblemSet2.pdf :: basicStatMechProblemSet2Problem2.tex

basicStatMechProblemSet3.pdf :: basicStatMechProblemSet3Problem1.tex
basicStatMechProblemSet3.pdf :: basicStatMechProblemSet3Problem2.tex
basicStatMechProblemSet3.pdf :: basicStatMechProblemSet3Problem3.tex

basicStatMechProblemSet4.pdf :: basicStatMechProblemSet4Problem1.tex
basicStatMechProblemSet4.pdf :: basicStatMechProblemSet4Problem2.tex
basicStatMechProblemSet4.pdf :: basicStatMechProblemSet4Problem3.tex

basicStatMechProblemSet5.pdf :: basicStatMechProblemSet5Problem1.tex
basicStatMechProblemSet5.pdf :: basicStatMechProblemSet5Problem2.tex
basicStatMechProblemSet5.pdf :: basicStatMechProblemSet5Problem3.tex

basicStatMechProblemSet6.pdf :: basicStatMechProblemSet6Problem1.tex
basicStatMechProblemSet6.pdf :: basicStatMechProblemSet6Problem2.tex
basicStatMechProblemSet6.pdf :: basicStatMechProblemSet6Problem3.tex
basicStatMechProblemSet6.pdf :: basicStatMechProblemSet6Problem4.tex
#basicStatMechProblemSet6.pdf :: basicStatMechProblemSet6Problem6.tex
#basicStatMechProblemSet6.pdf :: basicStatMechProblemSet6Problem7.tex

huang93.pdf :: basicStatMechProblemSet6Problem5.tex
huang93.pdf :: $(HUANG93_DEPS)

basicStatMechProblemSet7.pdf :: basicStatMechProblemSet7Problem1.tex
basicStatMechProblemSet7.pdf :: basicStatMechProblemSet7Problem2.tex
basicStatMechProblemSet7.pdf :: basicStatMechProblemSet7Problem3.tex

basicStatMechProblemSet1.pdf :: $(PDF_DEPS)
basicStatMechProblemSet2.pdf :: $(PDF_DEPS)
basicStatMechProblemSet3.pdf :: $(PDF_DEPS)
basicStatMechProblemSet4.pdf :: $(PDF_DEPS)
basicStatMechProblemSet5.pdf :: $(PDF_DEPS)
basicStatMechProblemSet6.pdf :: $(PDF_DEPS)
basicStatMechProblemSet7.pdf :: $(PDF_DEPS)

# https://tex.stackexchange.com/questions/570899/use-of-amsmath-binom-causes-missing-number-if-breqn-is-used
#mathstyle.sty : 
#	wget -o $@ http://tug.org/svn/texlive/trunk/Master/texmf-dist/tex/latex/breqn/mathstyle.sty?revision=54801&view=co

scrpage2.sty : ../latex/scrpage2.sty
	cp $^ $@

backmatter.tex: ../latex/classicthesis_mine/backmatter2.tex
	rm -f $@
	ln -s ../latex/classicthesis_mine/backmatter2.tex backmatter.tex
