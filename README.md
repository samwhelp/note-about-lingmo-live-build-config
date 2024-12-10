

# 首頁

> Lingmo Live Build Config 探索筆記

| Link | GitHub |
| ---- | ------ |
| [Lingmo Live Build Config 探索筆記](https://samwhelp.github.io/note-about-lingmo-live-build-config/) | [GitHub](https://github.com/samwhelp/note-about-lingmo-live-build-config) |
| [Lingmo OS 探索筆記](https://samwhelp.github.io/note-about-lingmo/) | [GitHub](https://github.com/samwhelp/note-about-lingmo) |




## 主題

* [相關討論](#相關討論)
* [專案](#專案)
* [Boot ISO By GRUB](#boot-iso-by-grub)
* [Lingmo OS / Live System](#lingmo-os--live-system)
* [連結](#連結)
* [相關筆記](#相關筆記)




## 相關討論

* [[分享] 如何運用「lingmo-live-build-config」來「自訂產生 Lingmo OS Live ISO」](https://github.com/orgs/LingmoOS/discussions/26)




## 專案

> 關於「`Lingmo OS / [live-build-config`」這個專案，是「Lingmo OS Live ISO 產生架構」。

| Link |
| ---- |
| Lingmo OS / [live-build-config](https://github.com/LingmoOS/live-build-config) |


> 以下的專案，則是會複製「`Lingmo OS / live-build-config`」這個專案。

> 並將「自訂的設定檔」，覆蓋到「`Lingmo OS / [live-build-config`」這個專案。

> 最後再進行「製作 Lingmo OS Live ISO」的流程。

### Prototype

| Link | GitHub |
| ---- | ------ |
| [lingmo-live-build-config-using](https://samwhelp.github.io/lingmo-live-build-config-using/) | [GitHub](https://github.com/samwhelp/lingmo-live-build-config-using) |
| [lingmo-live-build-config-remix](https://samwhelp.github.io/lingmo-live-build-config-remix/) | [GitHub](https://github.com/samwhelp/lingmo-live-build-config-remix) |
| [lingmo-live-build-config-basic](https://samwhelp.github.io/lingmo-live-build-config-basic/) | [GitHub](https://github.com/samwhelp/lingmo-live-build-config-basic) |
| [lingmo-live-build-config-enhance](https://samwhelp.github.io/lingmo-live-build-config-enhance/) | [GitHub](https://github.com/samwhelp/lingmo-live-build-config-enhance) |


### Respin

| Link | GitHub |
| ---- | ------ |
| [lingmo-live-build-respin-theme-lingmo-icon-citrus](https://samwhelp.github.io/lingmo-live-build-respin-theme-lingmo-icon-citrus/) | [GitHub](https://github.com/samwhelp/lingmo-live-build-respin-theme-lingmo-icon-citrus) |


| Link | GitHub |
| ---- | ------ |
| [lingmo-live-build-respin-theme-vimix](https://samwhelp.github.io/lingmo-live-build-respin-theme-vimix/) | [GitHub](https://github.com/samwhelp/lingmo-live-build-respin-theme-vimix) |
| [lingmo-live-build-respin-theme-orchis](https://samwhelp.github.io/lingmo-live-build-respin-theme-orchis/) | [GitHub](https://github.com/samwhelp/lingmo-live-build-respin-theme-orchis) |
| [lingmo-live-build-respin-theme-graphite](https://samwhelp.github.io/lingmo-live-build-respin-theme-graphite/) | [GitHub](https://github.com/samwhelp/lingmo-live-build-respin-theme-graphite) |
| [lingmo-live-build-respin-theme-fluent](https://samwhelp.github.io/lingmo-live-build-respin-theme-fluent/) | [GitHub](https://github.com/samwhelp/lingmo-live-build-respin-theme-fluent) |




## Boot ISO By GRUB

> 將產出的「iso檔案」放置到「`/opt/iso/lingmo/latest/lingmo.iso`」這個路徑

> 產生一個檔案「`/boot/grub/custom.cfg`」，內容如下

``` sh
menuentry "Lingmo OS" --class Debian {
	set iso_file="/opt/iso/lingmo/latest/lingmo.iso"
	search --set=iso_partition --no-floppy --file $iso_file
	probe --set=iso_partition_uuid --fs-uuid $iso_partition
	set img_dev="/dev/disk/by-uuid/$iso_partition_uuid"
	loopback loop ($iso_partition)$iso_file

	set extra_option=""
	#set extra_option="components quiet splash"

	set locale_option=""
	#set locale_option="locales=en_US.UTF-8"
	#set locale_option="locales=zh_TW.UTF-8"
	#set locale_option="locales=zh_CN.UTF-8"
	#set locale_option="locales=zh_HK.UTF-8"
	#set locale_option="locales=ja_JP.UTF-8"
	#set locale_option="locales=ko_KR.UTF-8"

	set boot_option="${locale_option} ${extra_option}"
	linux	(loop)/live/vmlinuz boot=live buuid=${iso_partition_uuid} findiso=${iso_file} ${boot_option}
	initrd	(loop)/live/initrd.img
}
```

> 重新開機後，就會在「GRUB」的開機選單，看到「`Lingmo OS`」這個選項。




## Lingmo OS / Live System

| Account  | Value  |
| -------- | ------ |
| Username | `lingmo` |
| Password | `live` |

若想要移除目前帳號的密碼，可以執行下面指令

``` sh
sudo passwd -d $(whoami)
```




## 連結

| 連結  | GitHub |
| ---- | ------ |
| [Debian Live Manual](https://live-team.pages.debian.net/live-manual/html/live-manual/index.en.html) |  |
| [Lingmo OS Adjustment](https://samwhelp.github.io/lingmo-adjustment/) | [GitHub](https://github.com/samwhelp/lingmo-adjustment) |





## 相關筆記

| Link | GitHub |
| ---- | ------ |
| [Debian 探索筆記](https://samwhelp.github.io/note-about-debian/) | [GitHub](https://github.com/samwhelp/note-about-debian) |
| [EznixOS 探索筆記](https://samwhelp.github.io/note-about-eznixos/) | [GitHub](https://github.com/samwhelp/note-about-eznixos) |
| [Lika OS 探索筆記](https://samwhelp.github.io/note-about-lika/) | [GitHub](https://github.com/samwhelp/note-about-lika) |
| [Lika Live Build Config 探索筆記](https://samwhelp.github.io/note-about-lika-live-build-config/) | [GitHub](https://github.com/samwhelp/note-about-lika-live-build-config) |




## Samwhelp

* [個人筆記](https://samwhelp.github.io/book/)
