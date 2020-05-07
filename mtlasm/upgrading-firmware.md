# Firmware upgrade workflows for Montreal Assembly Pedals

Applicable for the following:

* 856 For Z
* Count 2 Five


## Requirements

You'll need:

1. One of the mtlasm pedals listed above
2. A firmware you want to upload
3. ```dfu-util``` for uploading/downloading firmware to the pedal
4. a USB-to-miniUSB cable

## Using ```dfu-util```

For macOS, install the dfu utility.

```bash
$ brew install dfu-util
```

Displaying help

```bash
$ dfu-util --help
Usage: dfu-util [options] ...
  -h --help			Print this help message
  -V --version			Print the version number
  -v --verbose			Print verbose debug statements
  -l --list			List currently attached DFU capable devices
  -e --detach			Detach currently attached DFU capable devices
  -E --detach-delay seconds	Time to wait before reopening a device after detach
  -d --device <vendor>:<product>[,<vendor_dfu>:<product_dfu>]
                Specify Vendor/Product ID(s) of DFU device
  -p --path <bus-port. ... .port>	Specify path to DFU device
  -c --cfg <config_nr>		Specify the Configuration of DFU device
  -i --intf <intf_nr>		Specify the DFU Interface number
  -S --serial <serial_string>[,<serial_string_dfu>]
                Specify Serial String of DFU device
  -a --alt <alt>		Specify the Altsetting of the DFU Interface
                by name or by number
  -t --transfer-size <size>	Specify the number of bytes per USB Transfer
  -U --upload <file>		Read firmware from device into <file>
  -Z --upload-size <bytes>	Specify the expected upload size in bytes
  -D --download <file>		Write firmware from <file> into device
  -R --reset			Issue USB Reset signalling once we're finished
  -s --dfuse-address <address>	ST DfuSe mode, specify target address for
                raw file download or upload. Not applicable for
                DfuSe file (.dfu) downloads
```

Listing devices connected to the system.

```bash
$ dfu-util -v -l
```

Downloading existing firmware (for backing up purposes) from the device in slot 0.

```bash
$ dfu-util -a 0 -D currently-installed-firmware.dfu
```

Uploading a new firmware file (e.g. new-firmware.dfu) to the device found at slot 0.

```bash
$ dfu-util -a 0 -U new-firmware.dfu
```
