# for py3: make PYTHON=python3 CYTHON="cython -3" V=3

OCTAVE = /home/lei/octave-4.0.2
SCRIPTS = $(OCTAVE)/scripts/specfun

CYTHON = cython
PYTHON = python
XFILES = -x inputParser.m,dblquad.m,triplequad.m

COVERAGE = python3 -m coverage

CYTHON = cython
PYTHON = python$V
XFILES = -x inputParser.m,dblquad.m,triplequad.m

SRCSMOP = main.py parse.py backend.py resolve.py options.py
FLAGS  = 
MYFLAGS=

#V = 2.7
V = 3

all:
<<<<<<< HEAD
	make -B FLAGS=     liboctave.py
=======
	make -B FLAGS=     liboctave.py	
	$(COVERAGE) run -p main.py solver.m
	$(COVERAGE) combine 
>>>>>>> 245d9c8989e304a637840d6bcbd87d8905a96101
foo:
	make -B FLAGS=-C   liboctave.py
	make -B FLAGS=-N   liboctave.py
	make -B FLAGS=-T   liboctave.py
	make -B FLAGS=-CN  liboctave.py
	make -B FLAGS=-TN  liboctave.py
	make -B FLAGS=-CT  liboctave.py
	make -B FLAGS=-CTN liboctave.py

liboctave.py:
	find $(SCRIPTS) -name \*.m | xargs $(PYTHON) main.py --verbose -o $@ $(MYFLAGS) $(FLAGS) $(XFILES) $^
	#$(PYTHON) $@

clean:
	rm -f a.* *.pyc solver.so solver.py octave.so

regress:
	make | sort -u | wc
%.c: %.py
	$(CYTHON) $^

%.so: %.c
	gcc -Wno-cpp -I /usr/include/python$V -O2 -shared -o $@ $^

%.py: %.m
	$(PYTHON) main.py -o $@ $^
	#$(PYTHON) $@

%.pdf: %.dot
	dot -Tpdf -o $@ $^

%.pdf: %.rst
	rst2pdf $^
