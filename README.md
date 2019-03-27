# HappyHacking

Map Alt+hjkl to Arrow Left/Down/Up/Right in driver level.

## Why I need this?

Mapping keys through X protocol or other GUI technology in Linux is hard and full of bugs. Only modify it in driver level will it cover every input context.

## How to use?

If you don't want to compile linux kernel, you can use `libhid` to detach usb device and `insmod` this mod.

```
make
sudo libhid-detach-device [VENDOR ID]:[PRODUCT ID]
sudo insmod usbkbd.ko
```

You can get `[VENDOR ID]:[PRODUCT ID]` by `lsusb`.

`KERNEL_DIR` in `Makefile` may be not right, it depends on distribution. In some distributions it is `/usr/lib/modules/$(shell uname -r)/build`.

If you can compile linux kernel yourself, you can use this `usbkbd.c` to replace it in linux source file (in `drivers/hid/usbhid/usbkbd.c`).

[A patch](https://gist.github.com/YangKeao/1f5a27de16003343f7b23b1a795abb33) is also provided for gentoo user.
