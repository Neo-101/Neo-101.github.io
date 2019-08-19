# Slove problems encountered during installing YouCompleteMe on Mac 

Key: Follow README from [YouCompleteMe](https://github.com/ycm-core/YouCompleteMe).

## DO:

1. Install official [MacVim](https://github.com/macvim-dev/macvim).
2. Config git proxy when there is some problem with network.

## NOT DO:

1. Use default vim on Mac.
2. Upgrade default vim on Mac and use it to install YouCompleteMe.

## Details:

### Errors with MacVim installed from Homebrew

#### Action:
Install YouCompleteMe with Macvim which installed from Homebrew.

#### Errors:
```
[2019-08-18 10:37:36] Plugin Valloric/YouCompleteMe
[2019-08-18 10:37:36] $ git clone --recursive 'https://github.com/Valloric/YouCompleteMe.git' '/Users/lujingze/.vim/bundle/YouCompleteMe'
[2019-08-18 10:37:36] > Cloning into '/Users/lujingze/.vim/bundle/YouCompleteMe'...
[2019-08-18 10:37:36] > error: RPC failed; curl 56 LibreSSL SSL_read: SSL_ERROR_SYSCALL, errno 54
[2019-08-18 10:37:36] > fatal: the remote end hung up unexpectedly
[2019-08-18 10:37:36] > fatal: early EOF
[2019-08-18 10:37:36] > fatal: index-pack failed
```
#### Solution:
Do NOT use MacVim installed by Homebrew, but the one by dmg file from official releases in [its github repo](https://github.com/macvim-dev/macvim).

There are several solutions from Internet:
>this issue is most likely related to your git/ curl/ libressl or the proxy behind your internet. Try to update your git/curl/ libressl or try to connect without using proxy.
[link](https://github.com/EOSIO/eos/issues/4536)

>git config http.postBuffer 524288000
[link](https://stackoverflow.com/a/36843260)

But sadly none of them solved our problem.

### Errors with MacVim installed from official dmg

#### Action:
Install YouCompleteMe with MacVim which installed from official dmg.

#### Errors:
```
[2019-08-19 10:08:38] > Cloning into '/Users/lujingze/.vim/bundle/YouCompleteMe/third_party/ycmd/third_party/go/src/golang.org/x/tools'...
[2019-08-19 10:08:38] > fatal: unable to access 'https://go.googlesource.com/tools/': Failed to connect to go.googlesource.com port 443: Operation timed out
[2019-08-19 10:08:38] > fatal: clone of 'https://go.googlesource.com/tools' into submodule path '/Users/lujingze/.vim/bundle/YouCompleteMe/third_party/ycmd/third_party/go/src/golang.org/x/tools' failed
```
#### Solution:

Git failed to connect to go.googlesource.com port 443. The reason might be network constraint in some region. We can hanle it by configureing git
proxy. Detains [here](https://gist.github.com/evantoli/f8c23a37eb3558ab8765).

```
git config --global http.proxy http://proxyUsername:proxyPassword@proxy.server.com:port
```

I use V2ray as my proxy on my MacBook Pro and the proxy server is sock5://127.0.0.1 and port is 1081, so the command is:

```
git config --global https.proxy 'socks5://127.0.0.1:1081'
git config --global http.proxy 'socks5://127.0.0.1:1081'
```

Then we can check whether we can git clone the blocked repo:   

```
cd ~
mkdir tmp/
cd tmp
git clone https://go.googlesource.com/tools/
```

If git successfully clones the blocked repo, then we have configured git proxy correctly.

Then install YouCompleteMe with Vundle.

### Errors with building regex module 

##### Action:
Step 5 of [Full Installation Guide](https://github.com/ycm-core/YouCompleteMe#full-installation-guide)

##### Errors:
```
CMake Error: The source directory "/Users/lujingze/regex_build" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.
```
##### Solution:
[link](https://github.com/ycm-core/YouCompleteMe/issues/3232#issuecomment-454651557)
