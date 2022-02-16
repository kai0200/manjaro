This is a tutorial how to write an ISO file correctly to an USB stick.

Download the ISO and the checksum file.

First, verify the checksum:

sha1sum -c manjaro.iso.sha1

It should print a line which says “OK”.
If it’s not okay, it might be a bad download, so download it again.

Print out the checksum, we’ll need it later on:

sha1sum manjaro.iso

dc7427636040e9469861251858aae820c2ae16cc manjaro-kde-20.0.3-200606-linux56.iso

Plug in your USB stick.

Check the device name it got associated with:

ls -l /dev/disk/by-id | grep usb

[…] usb-Flash_USB_Disk_37271228A5E0216322818-0:0 → …/…/XdA

Start the write process with dd:

sudo dd if=manjaro.iso of=/dev/XdA bs=1M oflag=sync status=progress

For old and slow USB2 sticks you can use a lower block size (bs) value like 128K;
for faster sticks you can use 4M.

You get a confirmation when the transfer has been finished:
xxx bytes (yyy MB, zzz MiB) copied, … s, … MB/s

Now you can check whether the file has been correctly copied to the stick:

sudo dd if=/dev/XdA iflag=count_bytes count=xxx | sha1sum

Adjust the count parameter xxx to represent the number of bytes written which you
get from the confirmation above in point 7.
xxx bytes (yyy MB, zzz MiB) copied, … s, … MB/s
dc7427636040e9469861251858aae820c2ae16cc

Compare the checksum with the one you got in step 3, if they match, you’re good to go!

Notes:

a) It’s recommended also to check the signature of the ISO with gpg.
That does not only verify the integrity, but also the authenticity.

b) Instead of writing to /dev/XdA, you can also write to /dev/disk/by-id/usb-xxx (see point 5).
This helps to avoid confusion especially if you have lots of devices.
