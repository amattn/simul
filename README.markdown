paral
=====

Launch commands, shell scripts in parallel.  Designed as an alternative/replacement for GNU parallel.


Installation
------------

The usual:

    go get github.com/amattn/paral


If the go tool chain is installed, this should just appear in your `GOPATH`.

Eventually, I'll package releases for download at https://github.com/amattn/paral/releases

Usage
-----

    paral "command 1" "command 2 --flag" "command arg1 arg2"

    paral sleep 1 && echo c1" "sleep 2 && echo c2" "sleep 3 && echo c3" "sleep 4 && echo c4"  "sleep 5 && echo c5"


You can use the `-n` flag to control the maximum number of simultaneous commands.  If you set this value to 0, then all commands are completed simultaneously.  The default value is equal to the number of CPU cores detected by the program.  

Here are some examples:

    paral -n=0 "sleep 5 && echo c5" "sleep 4 && echo c4" "sleep 3 && echo c3" "sleep 2 && echo c2" "sleep 1 && echo c1"

    paral -n=1 "sleep 5 && echo c5" "sleep 4 && echo c4" "sleep 3 && echo c3" "sleep 2 && echo c2" "sleep 1 && echo c1"

    paral -n=2 "sleep 5 && echo c5" "sleep 4 && echo c4" "sleep 3 && echo c3" "sleep 2 && echo c2" "sleep 1 && echo c1"

    paral -n=5 "sleep 5 && echo c5" "sleep 4 && echo c4" "sleep 3 && echo c3" "sleep 2 && echo c2" "sleep 1 && echo c1"

    paral -n=1 "echo a && sleep 0.5 && echo b && sleep 0.5 && echo c && sleep 0.5 && echo d && sleep 0.5 && echo e && sleep 0.5 && echo f && sleep 0.5 && echo g && sleep 0.5 && echo h" 

Notes
-----

This initial incaration of paral is a bit limited.  Notably missing is any notion of GNU parallel's subsitution functionality.

For simply launching commands in parallel, capturing the output and watching the progress, paral works very well.

