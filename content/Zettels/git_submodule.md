+++
title = "git submodule"
author = ["showgood"]
lastmod = 2020-04-18T12:13:29-04:00
draft = false
+++

tags
: [git]({{< relref "git" >}})

<https://git-scm.com/book/en/v2/Git-Tools-Submodules>

git submodule add <https://github.com/jethrokuan/cortex/>

-   `git submodule init` initialize your local configuration file
-   run it at submodule directory
-   `git submodule update` fetch all the data from that project

<!--listend-->

```sh
cd cortex/
git submodule init
```

```text
Submodule 'themes/cortex' (https://github.com/jethrokuan/cortex/) registered for path './'
```
