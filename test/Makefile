refresh=

all: test

test_requires:
	@echo The selftest uses the following extra packages:
	@sudo apt install -y shunit2 || rpm -q shunit2 || exit 2
	@sudo apt install -y pdftk || rpm -q pdftk || exit 2
	@sudo pip3 install scipy pypdftk-secure || exit 2
	@echo -----------------------------------------------

test: test_requires
	ln -sf ../pdfcompare.py pdfcompare
	env PATH=.:$$PATH sh ./helptest.sh $(VER) VER=$(VER)
	env PATH=.:$$PATH sh ./python3.sh
	env PATH=.:$$PATH refresh=$(refresh) sh ./restest.sh
	rm pdfcompare

# updates the testsuite after code changes 
# that affect the visual representation.
refresh:
	# we only need to refresh restest.sh
	env PATH=.:$$PATH refresh=yes sh ./restest.sh
	# make test refresh=yes
