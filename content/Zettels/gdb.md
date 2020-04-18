+++
title = "GDB"
author = ["showgood"]
lastmod = 2020-04-18T13:39:43-04:00
draft = false
+++

tags
: [Debugger]({{< relref "debugger" >}})


## set function breakpoint {#set-function-breakpoint}

Need to use fully qualified name, for eg, `namespace1::namespace2::func`


## set breakpoint with filename + line number {#set-breakpoint-with-filename-plus-line-number}


## set breakpoint to catch exception {#set-breakpoint-to-catch-exception}

-   catch throwing [exception]({{< relref "exception" >}})


## data breakpoint {#data-breakpoint}


## list breakpoints {#list-breakpoints}

`info b`


## debug core dump {#debug-core-dump}

```sh
gdb <binary file> <core dump file>
```


## delete breakpoint {#delete-breakpoint}

-   use `del x` where x is number of breakpoint we get from [list breakpoints](#list-breakpoints)


## python interpreter {#python-interpreter}

[python]({{< relref "python" >}})


## print command {#print-command}

use `p` as shortcut.

p/d - display value in decimal
p/t - display value in binary
p/x - display value in hexadecimal


## articles {#articles}

<https://jvns.ca/blog/2018/01/04/how-does-gdb-call-functions/>
<http://www.brendangregg.com/blog/2016-08-09/gdb-example-ncurses.html>
<https://blog.0x972.info/?d=2015/09/09/09/19/14-debugging-with-gdb-a-real-life-example>
<https://jvns.ca/blog/2014/02/10/three-steps-to-learning-gdb/>
<https://pauladamsmith.com/blog/2011/03/redis%5Fget%5Fset.html> - More Redis internals: Tracing a GET & SET
