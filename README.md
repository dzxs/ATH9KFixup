ATH9KFixup
==========

An open source kernel extension providing patches for unsupported Atheros cards.
- AR946X (AR9462 & AR9463)
- AR9485
- AR9565


#### Features
Boot args:
- AR946X: (Default)
- AR9485: -ath9485
- AR9565: -ath9565


#### Credits
- [Apple](https://www.apple.com) for macOS  
- [vit9696](https://github.com/vit9696) for [Lilu.kext](https://github.com/vit9696/Lilu) & for patch
- [Pike R. Alpha](https://github.com/Piker-Alpha) for patch
- [lvs1974](https://applelife.ru/members/lvs1974.53809/) for original source code and idea
- [chunnann](http://www.insanelymac.com/forum/user/1977171-chunnann/) for writing the software and maintaining it

#### Usage

```bash
# 读写模式
spctl --master-disable
mount -uw /
killall Finder

# 备份IO80211Family.kext
mv /System/Library/Extensions/IO80211Family.kext ~/Desktop

# 把项目下的IO80211Family.kext复制到/S/L/E
cp -R IO80211Family.kext /System/Library/Extensions

# 重建缓存
sudo touch /System/Library/Extensions/ && sudo kextcache -u /

# 挂载EFI分区
sudo mkdir /Volumes/EFI
sudo mount -t msdos /dev/disk0s1 /Volumes/EFI

# 复制ATH9KFixup.kext到clover
cp -R ATH9KFixup.kext /Volumes/EFI/EFI/CLOVER/kexts/Other
```