# APT

Advanced Package Tool, or APT, is a free-software user interface that works with core libraries to handle the installation and removal of software on Debian, and Debian-based Linux Distributions.

## `APT` VS `apt-get`

[From StackExchange](https://askubuntu.com/questions/445384/what-is-the-difference-between-apt-and-apt-get)

apt-get may be considered as lower-level and "back-end", and support other APT-based tools. apt is designed for end-users (human) and its output may be changed between versions.

>The `apt` command is meant to be pleasant for end users and does not need to be backward compatible like apt-get(8).
>
This is the correct answer (for Debian and Ubuntu as well as other derivatives like Mint). In particular, running sudo apt upgrade will perform the same operations as sudo apt-get upgrade --with-new-pkgs. It will install new packages but, unlike sudo apt-get dist-upgrade, it will not remove old ones (except when installing a new version of the same package, of course--which sudo apt-get upgrade will also do). man apt further corroborates that this answer is correct. – Eliah Kagan
