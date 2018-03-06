**fix ubuntu eeepc**

- [all index](/indexed/tde/journal-tde.md)
- dates: [2018-03-06](/indexed/tde/journal-tde.md#dates-2018-03-06)
- tags: [eeepc](/indexed/tde/journal-tde.md#tags-eeepc), [ubuntu](/indexed/tde/journal-tde.md#tags-ubuntu), [graphic](/indexed/tde/journal-tde.md#tags-graphic), [problem](/indexed/tde/journal-tde.md#tags-problem)
- nodes: [eeepc-1000h](/indexed/tde/journal-tde.md#nodes-eeepc-1000h)
- actors: [tde](/indexed/tde/journal-tde.md#actors-tde)



# Table of Contents

-   [Fixes graphic problem on eeepc-1000he with ubuntu-1710](#fixes-graphic-problem-on-eeepc-1000he-with-ubuntu-1710)


# Fixes graphic problem on eeepc-1000he with ubuntu-1710

Apply [Bug in Kernel 4.13 : Intel Mobile Graphics 945 shows 80 % black screen][] proposed workaround

First reboot with a working kernel (4.10), then

```
echo "GRUB_GFXPAYLOAD_LINUX=text" | sudo tee /etc/default/grub
sudo update-grub
sudo shutdown -r now
```

[Bug in Kernel 4.13 : Intel Mobile Graphics 945 shows 80 % black screen]:
	https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724639 "bugs.launchpad.net"
