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
