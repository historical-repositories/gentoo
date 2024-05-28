# Gentoo Linux

> **A Meta-Distribution Known for Flexibility and Performance**

Gentoo Linux is an open-source, Unix-like operating system that is both flexible and customizable.
It is unique among Linux distributions due to its Portage package management system,
which allows users to compile the source code locally according to their preferences,
often resulting in optimized performance for specific types of computers.

Gentoo is designed to be modular, portable, and easy to maintain,
catering to users who desire a system tailored precisely to their needs and hardware.

Named after the fast-swimming gentoo penguin, the distribution emphasizes the potential for speed improvements
through machine-specific optimization.

Initially created by Daniel Robbins as Enoch Linux,
Gentoo has evolved to support a wide variety of processor architectures and user environments, from desktops to servers.

[Gentoo Linux - Wikipedia]: https://en.wikipedia.org/wiki/Gentoo_linux
[Gentoo Wiki]: https://wiki.gentoo.org/
[Gentoo - Gentoo wiki]: https://wiki.gentoo.org/wiki/Gentoo
[Gentoo - Wikipedia]: https://en.wikipedia.org/wiki/Gentoo
[Gentoo Linux - Simple English Wikipedia, the free encyclopedia]: https://simple.wikipedia.org/wiki/Gentoo_Linux


## Copies of upstream HEAD branches

### [Current 2015-08-09 00:38:18 - Now UTC [mirror]](../../tree/head)

This branch synces with the current upstream HEAD branch several times an hour.
So you will get always a fresh look at the whole commit history.

| | | |
| --- | --- | --- |
[Initial commit][head-initial-commit] | `56bd759df1d0c750a065b8c845e93d5dfa6b549d` | [Browse history since][head-initial-browse-since]

### [Historical 2000-07-28 00:35:42 - 2015-08-08 17:58:28 UTC](../../tree/hist/by-date/20000728T003542Z_20150808T175828Z)
This branch provides a copy of the original CVS repo officially converted to git by Gentoo Linux maintainers, before they switched wholly to git.

|  | Hash | |
| --- | --- | ---
[Last commit][historical-last-commit] | `2ebda5cd08db6bdf193adaa6de33239a83a73af0` |
[Initial commit][historical-initial-commit] | `499e2f00b49f32976e1749afcd4140dd51831917` | [Browse history since][historical-initial-browse-since]

## How to

### Download full `git` clone of this repository

This is done using the `--mirror` option, which fetches a full 1:1 clone, not just a subset of git refs as usual.
This is important, so that all branches and `git` [replace refs](https://git-scm.com/docs/git-replace) are fully downloaded.

```console
➜ git clone --mirror --branch='head' 'https://github.com/historical-repositories/gentoo.git' 'gentoo-historical'
Cloning into bare repository 'gentoo-historical'...
remote: Enumerating objects: 12339178, done.
remote: Counting objects: 100% (27275/27275), done.
remote: Compressing objects: 100% (11504/11504), done.
remote: Total 12339178 (delta 16629), reused 23718 (delta 15723), pack-reused 12311903
Receiving objects: 100% (12339178/12339178), 2.72 GiB | 27.55 MiB/s, done.
Resolving deltas: 100% (9074172/9074172), done.
```

<!--
TODO:
Alternative way
➜ git clone ...
➜ git fetch origin 'refs/replace/*:refs/replace/*'
-->

### On unified view with `git` replace

`git` now generates a unified view of the branches just for you.

All the commits have original hashes, and only the so called graft commits are missing.
These graft commits contain the initial import of data from previous repository, so they actually have no data itself.

This is how the unified view looks like at the replaced graft point:

```plain
commit c1de71edb35b118c3244c0d9d1b3f97c93d41969
Author: Robin H. Johnson <robbat2@gentoo.org>
Date:   Sat Aug 8 22:26:10 2015 -0700

    Update some skeleton file comments to Git instead of CVS.
    
    Signed-off-by: Robin H. Johnson <robbat2@gentoo.org>

commit 56bd759df1d0c750a065b8c845e93d5dfa6b549d (replaced)
Author: Sebastian Pipping <sping@gentoo.org>
Date:   Sat Aug 8 17:58:28 2015 +0000

    Mask upcoming dev-libs/iniparser:4
```

As you can see above, the last commit of the historical repository now shows the hash of the initial (graft) commit of the new repository and is tagged as `replaced`.
And the initial (graft) commit of the new repository is completely missing.

However, when directly referenced, the commit with original hash is still present.

```console
➜ git log -n1 2ebda5cd08db6bdf193adaa6de33239a83a73af0  # < hash of the last commit of the old repo
commit 2ebda5cd08db6bdf193adaa6de33239a83a73af0 (hist/by-name/cvs-repo, hist/by-date/20000728T003542Z_20150808T175828Z)
Author: Sebastian Pipping <sping@gentoo.org>
Date:   Sat Aug 8 17:58:28 2015 +0000

    Mask upcoming dev-libs/iniparser:4
➜ git log -n1 56bd759df1d0c750a065b8c845e93d5dfa6b549d  # < hash of the initial (graft) commit of the new repo
commit 56bd759df1d0c750a065b8c845e93d5dfa6b549d (replaced)
Author: Sebastian Pipping <sping@gentoo.org>
Date:   Sat Aug 8 17:58:28 2015 +0000

    Mask upcoming dev-libs/iniparser:4
```

### How to checkout working tree at specific commit

#### By exporting an archive of the files

This saves you storage, since only the files are exported.

```console
➜ # go to the target directory
➜ git --git-dir=../gentoo-historical/ archive 499e2f00b49f32976e1749afcd4140dd51831917 | tar -x
➜ ls -l
-rw-r--r--  1 rindeal rindeal  138 Jul 28  2000 header.txt
➜ du -hd0
8.0K    .
```

#### Using local `git clone`

```console
➜ # go to the target directory
➜ git clone --no-checkout ../gentoo-historical .
➜ 499e2f00b49f32976e1749afcd4140dd51831917
➜ ls -l
-rw-r--r--  1 rindeal rindeal  138 Jul 28  2000 header.txt
➜ du -hd0
3.2G    .
````

---

**Footnotes**:

The "Browse history since" links have to be regenerated for latest commits to be browsable (not usually needed though).

```sh
branch=head; initial_commit=56bd759df1d0c750a065b8c845e93d5dfa6b549d ;
echo "../../commits/${branch}/?after=$(git rev-list -n1 ${branch})+$(( "$(git rev-list --count "${initial_commit}..${branch}")" - 1 ))"
```

[head-initial-browse-since]:     ../../commits/head/?after=69185febec321c8ff4e44df069ddd4916aa1e071+834050
[head-initial-commit]:           ../../commit/56bd759df1d0c750a065b8c845e93d5dfa6b549d

[historical-initial-browse-since]:  ../../commits/hist/by-date/20000728T003542Z_20150808T175828Z/?after=2ebda5cd08db6bdf193adaa6de33239a83a73af0+788890
[historical-last-commit]:           ../../commit/2ebda5cd08db6bdf193adaa6de33239a83a73af0
[historical-initial-commit]:        ../../commit/499e2f00b49f32976e1749afcd4140dd51831917
