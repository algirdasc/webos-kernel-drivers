# About
LG WebOS USB Serial drivers for **4.4.84-404.glacier.10 kernel**:
 - ch341
 - cp210x

Suitable for HyperSerialEsp8266 / HyperSerialEsp32. 

# Your support
<a href="https://www.buymeacoffee.com/Ua0JwY9" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

# Automatically loading at boot
While you can manually load these drivers with `insmod`, people usually prefer to have them loaded automatically on each boot.

The following is an example of using the Homebrew Channel init system to load the `ch341.ko` driver, assuming it is located in `/home/root`:

```sh
cat >/home/root/insmod_serial.sh <<'__EOF__'
#!/bin/sh

insmod /home/root/ch341.ko
__EOF__
chmod +x /home/root/insmod_serial.sh
ln -s /home/root/insmod_serial.sh /var/lib/webosbrew/init.d/10-insmod_serial
```
*If you are using a different driver, just replace `ch341.ko` with its
  filename.*

This will create a script named `/home/root/insmod_serial.sh` and a symbolic link to it in `/var/lib/webosbrew/init.d`.

If you want to temporarily stop the module from being loaded, you can delete the link:
```sh
rm /var/lib/webosbrew/init.d/10-insmod_serial
```

To re-enable it, create the link again:
```sh
ln -s /home/root/insmod_serial.sh /var/lib/webosbrew/init.d/10-insmod_serial
```

# More drivers:
 - https://github.com/throwaway96/webos-kernel-drivers
