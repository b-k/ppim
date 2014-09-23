

pdf:
	for f in ../ch* ; do \
		sed 's/,/<|,|>/g' $$f | sed 's/<>/,/g' | m4 -P textify.m4  - | sed -e 's/æ/\\ae{}/g' -e 's/ô/\\^o/g' \
	-e 's/…/.../g' -e 's/œ/\\oe{}/g' -e 's/&gt;/>/' -e 's/&lt;/</' > `basename $$f .tex`.tex ; done
	pdflatex ppim
	bibtex ppim
	pdflatex ppim
	pdflatex ppim

html:
	sed 's/,/<|,|>/g' ../entries/$f.tex  | sed 's/│/,/g' | m4 -P ../tech/htmlify.m4  - | sed -e 's|<ul> *</li>|<ul>|' | ../tech/insert_ps | \
        sed -e 's/<p><h6>/<h6>/' -e 's|</h6></p>|</h6>|' -e 's|<p></li>|</li>|g'\
        -e '$d' -e 's/``/“/g' -e 's/\\dots/…/g' -e 's/\\%/%/g' -e 's/\\#/#/g' -e 's/---/—/g'\
            |awk -f ../tech/awk_cut > $f.html
