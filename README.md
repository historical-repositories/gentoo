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

### [Current [mirror]](../../tree/head)

This branch synces with the current upstream HEAD branch several times an hour.
So you will get always a fresh look at the whole commit history.

### [Historical 2000-07-28 00:35:42 - 2015-08-08 17:58:28 UTC](../../tree/hist/by-date/20000728T003542Z_20150808T175828Z)
This branch provides a copy of the original CVS repo officially converted to git by Gentoo Linux maintainers, before they switched wholly to git.

## Merged history

### Using `git replace`

Provides you with full hisotry with unchanged commit hashes across all branches.
This method works only with your local git clone of this repository and you have to clone all branches cloned.

```console
> git clone --no-checkout 'https://github.com/historical-repositories/gentoo.git'
...
```

### Amalgamated branch

This method provides a single branch with an unbroken linear commit history,
but the commit hashes are rewritten due to the merge.
