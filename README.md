# duf

ابزار Disk Usage/Free (لینوکس، BSD، macOS و ویندوز)

![duf](/duf.png)

## ویژگی‌ها

* [x] خروجی کاربرپسند و رنگی
* [x] تطبیق با تم و عرض ترمینال شما
* [x] مرتب‌سازی نتایج بر اساس نیاز شما
* [x] گروه‌بندی و فیلتر کردن دستگاه‌ها
* [x] امکان خروجی راحت به فرمت JSON

## نصب

### بسته‌ها

#### لینوکس

* Arch Linux: `pacman -S duf`
* Ubuntu (22.04 و بالاتر) / Debian (12 و بالاتر): `apt install duf`
* Fedora Linux: `dnf install duf`
* Nix: `nix-env -iA nixpkgs.duf`
* Void Linux: `xbps-install -S duf`
* Gentoo Linux: `emerge sys-fs/duf`
* Solus: `eopkg it duf`
* [بسته‌ها](https://github.com/muesli/duf/releases) برای Alpine، Debian و فرمت RPM

#### BSD

* FreeBSD: `pkg install duf`
* OpenBSD: `pkg_add duf`

#### macOS

* با [Homebrew](https://brew.sh/): `brew install duf`
* با [MacPorts](https://www.macports.org): `sudo port selfupdate && sudo port install duf`

#### ویندوز

* با [Chocolatey](https://chocolatey.org/): `choco install duf`
* با [scoop](https://scoop.sh/): `scoop install duf`

#### اندروید

* اندروید (از طریق termux): `pkg install duf`

### باینری‌ها

* [باینری‌ها](https://github.com/muesli/duf/releases) برای لینوکس، FreeBSD، OpenBSD، macOS و ویندوز

### از سورس

مطمئن شوید که محیط Go شما آماده است (نیازمند Go 1.23 یا بالاتر).
دستورالعمل نصب [اینجا](https://golang.org/doc/install.html) موجود است.

ساخت duf ساده است:

```bash
git clone https://github.com/muesli/duf.git
cd duf
go build
```

## استفاده

می‌توانید بدون آرگومان duf را اجرا کنید:

```bash
duf
```

برای لیست کردن دستگاه‌ها و نقاط مانت مشخص:

```bash
duf /home /some/file
```

برای نمایش همه موارد (شامل سیستم‌فایل‌های شبه، تکراری و غیرقابل دسترسی):

```bash
duf --all
```

### فیلتر کردن

نمایش یا مخفی کردن جدول‌های خاص:

```bash
duf --only local,network,fuse,special,loops,binds
duf --hide local,network,fuse,special,loops,binds
```

نمایش یا مخفی کردن سیستم‌فایل‌ها:

```bash
duf --only-fs tmpfs,vfat
duf --hide-fs tmpfs,vfat
```

یا نقاط مانت مشخص:

```bash
duf --only-mp /,/home,/dev
duf --hide-mp /,/home,/dev
```

از wildcard درون کوتیشن‌ها نیز می‌توان استفاده کرد:

```bash
duf --only-mp '/sys/*,/dev/*'
```

### گزینه‌های نمایش

مرتب‌سازی خروجی:

```bash
duf --sort size
```

کلیدهای معتبر: `mountpoint`, `size`, `used`, `avail`, `usage`, `inodes`, `inodes_used`, `inodes_avail`, `inodes_usage`, `type`, `filesystem`.

نمایش یا مخفی کردن ستون‌های خاص:

```bash
duf --output mountpoint,size,usage
```

اطلاعات inode به جای بلاک‌ها:

```bash
duf --inodes
```

اگر رنگ ترمینال به درستی شناسایی نشد، می‌توانید تم تنظیم کنید:

```bash
duf --theme light
```

### رنگ‌بندی و آستانه‌ها

duf ستون‌های availability و usage را با رنگ‌های قرمز، سبز یا زرد بسته به میزان فضای موجود نمایش می‌دهد. می‌توانید آستانه‌های خود را تنظیم کنید:

```bash
duf --avail-threshold="10G,1G"
duf --usage-threshold="0.5,0.9"
```

### خروجی JSON

اگر خروجی JSON می‌خواهید:

```bash
duf --json
```

## عیب‌یابی

کاربران `oh-my-zsh` باید بدانند که این ابزار از قبل یک alias با نام `duf` تعریف کرده است، که باید حذف شود:

```bash
unalias duf
```

## بازخورد

اگر بازخورد یا پیشنهادی دارید، لطفاً یک issue باز کنید یا پیام دهید!

* [Twitter](https://twitter.com/mueslix)
* [Fediverse](https://mastodon.social/@fribbledom)
