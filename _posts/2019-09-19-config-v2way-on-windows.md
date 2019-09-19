# Build V2Ray Server
Follow [main document] to build a V2Ray server.
# Config V2Ray on Mac
* Download V2Ray client for MacOS from link in [main document] and configure it.
* After checking V2Ray's working state, click its icon and choose **View current config.json...**.

![Click V2Ray icon on Mac][click_v2ray_icon_on_mac]

* Copy all text in the opened page to an editor and save it.
# Make it work on Windows
* Download V2Ray client for Windows from link in [main document].
* Find all lines which have a path in the config text of V2Ray client on Mac.
* Replace all path with path on Windows. Because Windows uses backslash "\\" while every OS else uses slash "/". We can simply change path to the present working directory.
* Download Firefox. Because Chrome doesn't has proxy configuration.
* Open settings of Firefox and search 'proxy'. Configure it like following image. Attention that 'SOCKS HOST' and corresponding 'Port' should be the same as the configuration we just edited.

![Set Firefox proxy][firefox_proxy_setting]

* Run **v2ray.exe** and browse with Firefox.

[main document]: https://github.com/Alvin9999/new-pac/wiki/%E8%87%AA%E5%BB%BAv2ray%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%95%99%E7%A8%8B
[click_v2ray_icon_on_mac]: ../assets/images/click_v2ray_icon_on_mac.png
[firefox_proxy_setting]: ../assets/images/firefox_proxy_setting.png
