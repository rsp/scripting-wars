scripting-wars
===============

https://github.com/rsp/scripting-wars

A competition between scripting languages.

This is still work in progress and is not finished yet.

Languages that qualify
----------------------

Wikipedia defines a scripting language as "a programming language that
supports scripts, programs written for a special run-time environment
that can interpret (rather than compile) and automate the execution of
tasks that could alternatively be executed one-by-one by a human operator."
([Wikipedia - Scripting language](https://en.wikipedia.org/wiki/Scripting_language))

For my purposes a scripting language is any language that has a program
that can run code supplied on standard input. It means that it's all about
the tools available and has nothing to do with the language itself.

Some examples:

2+2 Test
--------

Here is a 2+2 test: Can I add 2+2 using a given language
and make it print only the number 4 without any unnecessary output,
and can I do it without having to change any state of the system?
By changing the state of the system I mean writing anything to disk
or installing any language packages that are not already installed by default.
Ideally it should be possible to run the code provided on standard input,
without any need to filter its output.

Why is it important for a language to pass the 2+2 test?
Because then it can be used in shell scripts for some tasks that are hard,
impossible or not efficient to do using only
[basic Unix tools](http://www.cs.toronto.edu/~maclean/csc209/unixtools.html).
If a shell script can detect e.g. a Python runtime then it can use it
for a specific task, with a fallback using the standard tools otherwise.

```
$ echo 'print 2+2' | perl -l
4

$ echo 'print 2+2' | ruby -l
4

$ echo 'print 2+2' | python
4

$ echo 'print(2+2)' | python3
4

$ echo 'print(2+2)' | lua
4

$ echo 'echo $((2+2))' | sh
4

$ echo '(prn (+ 2 2))' | clojure -
4

$ echo 'puts [expr 2+2]' | tclsh
4

$ echo 'console.log(2+2)' | node
4

$ echo 'main() { printf("%d\n", 2+2); }' | tcc -run -
4
```

Basically all of those are reasonably popular languages
with easy to install binaries that can run programs
piped through the standard input with no problems
(like for example printing anything else than explicitly printed output)
and no need to write any files on the file system.

An example of a failed test:

```
$ echo '(display (+ 2 2))' | guile
GNU Guile 2.0.9
Copyright (C) 1995-2013 Free Software Foundation, Inc.

Guile comes with ABSOLUTELY NO WARRANTY; for details type `,show w'.
This program is free software, and you are welcome to redistribute it
under certain conditions; type `,show c' for details.

Enter `,help' for help.
4scheme@(guile-user)>
```
There is a number 4 burried in there somewhere, but it clearly is meant
to be run interactively and I see no easy way to make it print only 4.

I can use Guile to write just the number 4 using somethink like this:

```
$ t=`tempfile`; echo '(display (+ 2 2)) (newline)' > $t; guile --no-auto-compile $t; rm $t
4
```
but it is not as straightforward as with other languages and I have to write
a file to the file system so I don't consider it a suitable runtime
for the purpose of this experimrnts.

If any important language is missing here,
please [sumbit an issue](https://github.com/rsp/scripting-wars/issues).

System requirements
-------------------

It will be written and tested on Ubuntu 14.04
but it should work on any standard Linux/Unix distribution. If it doesn't,
please [sumbit an issue](https://github.com/rsp/scripting-wars/issues).

Commands
--------

Author
------
Rafał Pocztarski - https://github.com/rsp

License
-------
MIT License (Expat). See [LICENSE.md](LICENSE.md) for details.
