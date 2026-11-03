# BlackHole 2.1

> **CWHQ** — "ENJOY NOSTALGiA"

A resurrected copy of the BlackHole 2.1 IP-logger panel, hacked from **empireimpluse.info**. Archived here for the sake of history and vibes.

---

## ⚠️ Archive Notice

This kit was **hacked from empireimpluse.info**. It is old, it is crusty, and it expects a 2013-era stack. Don't expect it to just work on your shiny modern PHP 8 box without babysitting.

---

## 🔐 Archive Password

The archive is password protected:

```
infected
```

---

## 📦 Contents

```
bh/                  (panel source — drop into web root)
ioncube_loaders.zip  (prepacked ionCube loader — vc9 / PHP 5.x)
iNSTALL.txt          (original install notes — capital i)
IonCube License Fixer.exe  (license patch)
hole2.sql.gz         (database dump)
```

The original `iNSTALL.txt` reads:

> THiS BLACKHOLE KiT WAS HACKED FROM empireimpluse.info
>
> HOW TO RUN:
> iNSTALL iONCUBE LOADER (vc9 5.x)
> PATCH THE FUCKER WiTH IonCube License Fixer.exe
> DROP /bh/ iNTO WWW
> iMPORT hole2.sql.gz iNTO SQL
> EDiT config.php
> SET BACK YOUR SYSTEM TiME TO JANUARY 2o13
> ACCESS TO CONTROL PANEL ViA: crisp.php
> ???
> ENJOY NOSTALGiA
>
> CWHQ.

---

## 🛠️ Setup

Follow these in order. Don't skip steps — the ionCube patch is mandatory or the panel won't decode.

1. **Install the ionCube Loader** from the bundled `ioncube_loaders.zip` (vc9, PHP 5.x line). This kit is encoded for it — a modern PHP with a modern loader will choke.
2. **Patch it** using `IonCube License Fixer.exe` so the panel doesn't phone home and die on a dead license server.
3. **Drop the `/bh/` folder** into your web root (`www` / `htdocs` / `public_html`).
4. **Import `hole2.sql.gz`** into a MySQL database (gunzip it first, then import the `.sql`).
5. **Edit `config.php`** with your DB credentials and any path/URL settings.
6. **Set your system clock back to January 2013.** Yes, really — the panel's license/logic checks against the date and behaves badly otherwise.
7. **Access the control panel** at:

```
/bh/crisp.php
```

8. ???
9. **ENJOY NOSTALGiA.**

---

## 🧪 Requirements

- PHP 5.x (with ionCube Loader vc9)
- MySQL (import the provided dump)
- A web server that lets you drop arbitrary PHP in a folder (Apache + mod_php is easiest)
- Patience for 2013-era code
- System time set to Jan 2013

---

## 🚑 Troubleshooting

**White screen / blank panel**
Almost always the ionCube loader version or the system date. Confirm the loader actually loaded (`php -m | grep ioncube`) and that the clock is Jan 2013.

**"The file ... is encoded and requires ionCube"**
Loader not installed or wrong build (vc9/PHP 5.x only). Re-unpack `ioncube_loaders.zip` and point `zend_extension` at it.

**"License error" / panel calls home and dies**
You skipped `IonCube License Fixer.exe`. Run it on the encoded files before serving them.

**`crisp.php` 404s**
You dropped `bh/` in the wrong place or lost the folder name. It must sit exactly at `/bh/` relative to web root.

**Import fails**
Gunzip first (`gunzip hole2.sql.gz`), then import the resulting `.sql`. Importing the `.gz` raw won't work.

**Login / session instantly expires**
System clock drift. Keep it pinned to Jan 2013.

---

## 📝 Notes

- `config.php` is the only file you should need to touch for credentials.
- `crisp.php` is the entry point, not `index.php`. Don't go hunting for a different one.
- Everything is encoded — you're not reading the source without de-ionCube'ing it.

---

## 📜 Credits

- Original kit: **empireimpluse.info**
- Re-hosted/archived: **CWHQ** / ItsWocky

---

*No license, no support, no guarantees — it's an archive. ENJOY NOSTALGiA.*
