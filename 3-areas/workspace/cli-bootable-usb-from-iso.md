+++
date = 2024-03-31T09:29:19-23:53
+++

# CLI: Bootable USB From ISO

A fast guide to make your portable device into a bootable USB from an ISO file.

Check if flash drive is properly plugged and identify its label (something like `/dev/sda`):

```bash
sudo fdisk -l
```

Run `dd` command to make a bootable USB from the ISO file:

```bash
sudo dd bs=4M if=/path/to/file.iso of=/dev/sdX status=progress oflag=sync
```

Replace `/path/to/file.iso` with the path to your ISO file and replace `/dev/sdX` with the name of your device.
