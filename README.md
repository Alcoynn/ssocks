About:

sSocks is a package which contains: a socks5 server implements RFC 1928 (SOCKS V5) 
and RFC 1929 (Authentication for SOCKS V5), a reverse socks server and client, 
a netcat like tool, which supports socks5 with authentication 
and a socks5 relay (run a server and send to a another socks5 server).

------------------------------------------------------------------------

Status on windows:

All tools have been ported and "work". They are still in alpha stage and may not work as expected in all circumstances.
Daemon / background options are disabled on windows for now.

------------------------------------------------------------------------

Building on Windows:

From VS Dev Command Prompt run

```console
mkdir build
cd build
cmake ..
msbuild ssocks.sln /p:Configuration=Release
```

------------------------------------------------------------------------

Building on linux:

```console
mkdir build
cd build
cmake -DCMAKE_C_FLAGS=-fcommon ..
make
```

------------------------------------------------------------------------

Original README:

------------------------------------------------------------------------
Features:
  - Configuration file
  - Authentication file
  - Generate a connection log file
  - Daemon mode
  - Server support bind mode
  - Socks4 support (if authentication is enable socks4 is disable)
  - Support choose of interface to bind

------------------------------------------------------------------------
TODO:
  - IPV6 support
  - UDP support
  - Stock password with a hash ( md5 or sha256 )
  - GSSAPI auth support ( maybe )
  - Set number of client max ( actually 255 is in client.h MAXCLI var )
  - Add --pid-file option to server 
  - ssocks bind localhost, not all
  - SSL implements out of RFC

------------------------------------------------------------------------
Software:
  - nsocks is a netcat like through a socks5 (usefull to test socks server)
  - ssocksd is the socks5 server
  - ssocks is a socks5 relay, it run a socks server on your localhost interface,
 and relay all data to the server specified in parameter (works but under dev)
  - rssocks is a reverse socks5 server ( POC under dev )
  - rcsocks is a reverse socks5 client ( POC under dev )

File:
  - /etc/ssocksd.conf is server configuration file
  - /etc/ssocksd.auth is password file
  - /var/log/ssocksd.log is default log (specified in configuration file)
  - /var/run/ssocksd.pid is create in daemon mode and delete
 when it receive SIGTERM

------------------------------------------------------------------------
Copyright (C) 2011 by Hugo Caron

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
 THE SOFTWARE.

------------------------------------------------------------------------
