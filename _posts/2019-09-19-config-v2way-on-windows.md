# Build V2Ray Server
Follow [main document] to build a V2Ray server.
# Config V2Ray on Mac
* Download V2Ray client for MacOS from link in [main document] and configure it.
* After checking V2Ray's working state, click its icon and choose **View current config.json...**.

<img src="/assets/images/click_v2ray_icon_on_mac.png" alt="Cick V2Ray icon on Mac" height="200"/>

* Copy all text in the opened page to an editor and save it.
# Make it work on Windows
* Download V2Ray client for Windows from link in [main document].
* Find all lines which have a path in the config text of V2Ray client on Mac.
* Replace all path with path on Windows. Because Windows uses backslash "\\" while every OS else uses slash "/". We can simply change path to the present working directory.For example, before replacement, some lines may looked like this:
```
"log" : {
    "error" : "\/var\/folders\/8j\/4tjqkzrs7s3bn75175z53_z80000gn\/T\/cenmrev.v2rayx.log\/error.log",
    "loglevel" : "none",
    "access" : "\/var\/folders\/8j\/4tjqkzrs7s3bn75175z53_z80000gn\/T\/cenmrev.v2rayx.log\/access.log"
  }
```
After repalcement, they will be something like this:
```
"log" : {
    "error" : "error.log",
    "loglevel" : "none",
    "access" : "access.log"
  }
```
* Replace configuration file in the directory of V2Ray (maybe named 'config.json') with the configuration we just edited.
* Download Firefox. Because Chrome doesn't has proxy configuration.
* Open settings of Firefox and search 'proxy'. Configure it like following image. Attention that 'SOCKS HOST' and corresponding 'Port' should be the same as the configuration we just edited.

<img src="/assets/images/firefox_proxy_setting.png" alt="Set Firefox proxy" height="500"/>

* Run **v2ray.exe** and browse with Firefox.

[main document]: https://github.com/Alvin9999/new-pac/wiki/%E8%87%AA%E5%BB%BAv2ray%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%95%99%E7%A8%8B
