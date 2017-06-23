# abctool
abctool is a one-file python tool for working with music notation in the abc format.

## Features
* tranposition (both my own implementation and using abc2abc)
* read from standard input or file
* output to standard output, PostScript, PDF or MIDI
* view (using abcm2ps and gv)
* translation of chord names to danish/german ("B" becomes "H")
* removal of chords and fingerings
* supports ~/.abctoolrc

## Instalation
Since abctool is a python script, it doesn't need to be installed. How
ever, it depends on a number of things to be present on the system to
perform it's various tasks:

* Python
* abcm2ps (to generate postscript files)
* gv (to view postscript files, and to generate pdf files )
* abc2midi (to convert to midi or listen to a file)
* timidity (to listen to a file)
* texexec (to use the --songbook feature), in debian it's part of the
  tetex-extra package
* abc2abc (to transpose using -T, not recommended)

## Examples
To view the list of options:
$ abctool

To edit an abc file (on my system it opens the source in emacs and
shows the postscript in gv)
$ abctool -e test.abc

To transpose the file "test.abc" a minor third up, convert it to 
postscript and view the result in gv:
$ abctool -t 3 test.abc

To do the same using abc2abc:
$ abctool -T 3 test.abc

To remove fingerings from the file "test.abc", translate chords to
danish and send the result to standard out:
$ abctool -f -d -s test.abc

To remove all chords from the file "test.abc", convert it to
postscript in landscape format and view the result in gv:
$ abctool -c -o "-l" test.abc

To make a songbook of all .abc-files in the current directory:
$ cat *.abc | abctool -r -

To generate PostScript, PDF and midi output from the file
"test.abc" with "m7b5" substituted with "ø" and "dim7" with "°":
$ abctool -j --ps --pdf test.abc

To listen to the file "test.abc":
$ abctool -p test.abc

To generate a pdf file (songbook.pdf) containing all songs recursively
in current directory in concert key, Bb and Eb, bypassing ~/.abctoolrc:
$ abctool --songbook -R --norc

