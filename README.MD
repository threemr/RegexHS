# **WORK IN PROGRESS**

## NOTES FOR THIS VERSION

This is a wrapper and reorganization of the original library by Henry Spencer, to
make it suitable for use with the Arduino IDE. The logic has not been changed
on this version, only the distribution of source code in a more straightforward
set of files, as well as (potentially) some wrappers. Specifically, the "core" files
from the original library -regexp.h, regexp.c, regsub.c, regerror.c, and regmagic.h-
were consolidated into RegexHS.h and RegexHS.c

The original library was chosen for its promises of small compiled size and "ok"
speed, which should help its integration into embedded applications (e.g. Arduino).
(TODO: review whether the original code can be optimized by eliminating unnecesary
features for the intended hardware.). A secondary but important reason is that 
this library follows a syntax close to PCRE, as opposed to the Lua syntax used by
[Nick Gammon's Regex library](https://github.com/nickgammon/Regexp). This should 
help implementing the library for those already familiar with 
[PCRE syntax](https://www.pcre.org/original/doc/html/pcre.html).


Another project worth checking for a small library oriented to fit into embedded
applications is: [kokke´s tiny-regex-c library](https://github.com/kokke/tiny-regex-c)

---
## ORIGINAL README

>This is a revision of my well-known regular-expression package, regexp(3).
>It gives C programs the ability to use egrep-style regular expressions, and
>does it in a much cleaner fashion than the analogous routines in SysV.
>It is not, alas, fully POSIX.2-compliant; that is hard.  (I'm working on
>a full reimplementation that will do that.)
>
>This version is the one which is examined and explained in one chapter of
>"Software Solutions in C" (Dale Schumacher, ed.; AP Professional 1994;
>ISBN 0-12-632360-7), plus a couple of insignificant updates, plus one
>significant bug fix (done 10 Nov 1995).
>
>Although this package was inspired by the Bell V8 regexp(3), this
>implementation is *NOT* AT&T/Bell code, and is not derived from licensed
>software.  Even though U of T is a V8 licensee.  This software is based on
>a V8 manual page sent to me by Dennis Ritchie (the manual page enclosed
>here is a complete rewrite and hence is not covered by AT&T copyright).
>I admit to some familiarity with regular-expression implementations of
>the past, but the only one that this code traces any ancestry to is the
>one published in Kernighan & Plauger's "Software Tools" (from which
>this one draws ideas but not code).
>
>Simplistically:  put this stuff into a source directory, inspect Makefile
>for compilation options that need changing to suit your local environment,
>and then do "make".  This compiles the regexp(3) functions, builds a
>library containing them, compiles a test program, and runs a large set of
>regression tests.  If there are no complaints, then put regexp.h into
>/usr/include, add regexp.o, regsub.o, and regerror.o into your C library
>(or put libre.a into /usr/lib), and install regexp.3 (perhaps with slight
>modifications) in your manual-pages directory. 
>
>The files are:
>
>COPYRIGHT	copyright notice
>README		this text
>Makefile	instructions to make everything
>regexp.3	manual page
>regexp.h	header file, for /usr/include
>regexp.c	source for regcomp() and regexec()
>regsub.c	source for regsub()
>regerror.c	source for default regerror()
>regmagic.h	internal header file
>try.c		source for test program
>timer.c		source for timing program
>tests		test list for try and timer
>
>This implementation uses nondeterministic automata rather than the
>deterministic ones found in some other implementations, which makes it
>simpler, smaller, and faster at compiling regular expressions, but slower
>at executing them.  Many users have found the speed perfectly adequate,
>although replacing the insides of egrep with this code would be a mistake.
>
>This stuff should be pretty portable, given an ANSI C compiler and
>appropriate option settings.  There are no "reserved" char values except for
>NUL, and no special significance is attached to the top bit of chars.
>The string(3) functions are used a fair bit, on the grounds that they are
>probably faster than coding the operations in line.  Some attempts at code
>tuning have been made, but this is invariably a bit machine-specific.
>
>This distribution lives at [ftp://ftp.zoo.toronto.edu/pub/bookregexp.{tar|shar}]
>at present.
>