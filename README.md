<h3 align="center"><img src="https://raw.githubusercontent.com/mcpcpc/kirc/master/.github/kirc.png" alt="logo" height="170px"></h3>
<p align="center">KISS for IRC, a tiny IRC client written in POSIX C99.</p>
<p align="center">
<a href="./LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue.svg"></a>
<a href="https://github.com/mcpcpc/kirc/releases"><img src="https://img.shields.io/github/v/release/mcpcpc/kirc.svg"></a>
<a href="https://repology.org/metapackage/kirc"><img src="https://repology.org/badge/tiny-repos/kirc.svg" alt="Packaging status"></a>
</p>

## Objectives

_"Do one thing and do it well"_  —  Emphasis was placed on building simple, short, clear, modular, and extensible code that can be easily maintained and repurposed (per the [Unix philosophy](https://en.wikipedia.org/wiki/Unix_philosophy)).

_Portability_ — [POSIX](https://en.wikipedia.org/wiki/POSIX) compliance ensures seamless compatibility and interoperability between variants of Unix and other operating systems.

_Usability_ — Commands and shortcuts should feel "natural" when using a [standard 104-key US keyboard layout](https://en.wikipedia.org/wiki/Keyboard_layout).  Where possible, the number of keystrokes have been minimized.

## Usage

```shell
usage: kirc [-s hostname] [-p port] [-c channel] [-n nick] [-r real name] [-u username] [-k password] [-x init command] [-w columns] [-W columns] [-o path] [-h|v|V]
-s     server address (default: 'irc.freenode.org')
-p     server port (default: '6667')
-c     channel name (default: 'kirc')
-n     nickname (required)
-u     server username (optional)
-k     server password (optional)
-r     real name (optional)
-v     version information
-V     verbose output (e.g. raw stream)
-o     output path to log irc stream
-x     send command to irc server after inital connection
-w     maximum width of the printed left column (default: '10')
-W     maximum width of the entire printed stream (default '80')
-h     basic usage information
```

## Features

* No dependencies other than a [C99 compiler](https://gcc.gnu.org/).
* Complies with [RFC 2812](https://tools.ietf.org/html/rfc2812) standard.
* Ability to log the entire chat history  (see _Usage_ section for more information).
* Simple command structure:

```shell
<message>                   Send a message to the current channel.
/m <nick|channel> <message> Send a message to a specified channel or nick.
/M <message>                Send a message to NickServ.
/Q <message>                Send a message and close the host connection.
/x <message>                Send a message directly to the server.
/j <channel>                Join a specified channel.
/p <channel>                Leave (part) a specified channel.
/n                          List all users on the current channel.
/q                          Close the host connection.
/h                          Print a list of available kirc commands.
```

* Color scheme definition via [ANSI 8-bit colors](https://en.wikipedia.org/wiki/ANSI_escape_code). Therefore, one could theoretically achieve uniform color definition across all shell applications and tools.

## Screenshots

![Screenshot 1](/.github/example.png)

## Installation

Building and installing on **KISS Linux** using the Community repository:

```shell
kiss b kirc
kiss i kirc
```

Building and installing on **Arch** and **Arch-based** distros using the AUR:

```shell
git clone https://aur.archlinux.org/kirc-git.git
cd kirc
makepkg -si
```

Building and installing from source (works on **Rasbian**, **Debian**, **Ubuntu** and many other Unix distributions):

```shell
git clone https://github.com/mcpcpc/kirc.git
cd kirc
make
make install
```

## Transport Layer Security (TLS)  Support

There is no native [TLS/SSL](https://en.m.wikipedia.org/wiki/Transport_Layer_Security) support.  Instead, users can achieve this functionality by using third-party tools (e.g. stunnel, socat, ghosttunnel).

* _socat_ example:

```shell
socat -v tcp-listen:6667,reuseaddr,fork,bind=127.0.0.1 ssl:<irc-server>:669
kirc -s 127.0.0.1 -c 'channel' -n 'name' -r 'realname'
```

## Contact

For any further questions or concerns, feel free to reach out to me on `#kirc`
or `#kisslinux` channels of the _irc.freenode.org_ server.
