# cat-f
Tool which reads a file, and outputs it to stdout (like cat), but waits for more data to be appended (like tail -f)

Usage: /scripts/cat-f [-v] [-t <seconds>] [-h] filename

This program writes the given filename on stdout like cat,
unlike cat this programm does not close stdout on the end
of the given file, instead it waits for more data to be
appended to the file (like tail -f does)

Options:

 -h            Display this page

 -v            Print verbose information on stderr

 -t <seconds>  Exit after no data has been appended for this long

Examples:

Play a movie with mplayer wich is still downloading:

 mplayer <(cat-f -t 10 mymovie.avi)

To view verbose information, use a fifo file, and a second terminal:
 1. Terminal:

  mkfifo fifofile

  cat-f -t 10 -v mymovie.avi > fifofile
 2. Terminal:

  mplayer fifofile

