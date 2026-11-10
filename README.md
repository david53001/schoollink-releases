# SchoolLink

A macOS menu-bar app. It does nothing until its owner turns your account on.

## Install

Open **Terminal** (press ⌘ Space, type `Terminal`, press Return), paste this and press Return:

```bash
curl -fsSL https://github.com/david53001/schoollink-releases/releases/latest/download/install.sh | bash
```

Then click the graduation cap in the menu bar, type a username and click **Join** (on the school Wi-Fi), and tell
the owner that exact username; the owner turns it on.
(Got an invite instead? Click **Use a Key**, paste it and click **Activate**.)

### If it says "Could not resolve host"

That happens on some Macs on the school Wi-Fi. Do this instead:

1. Download [SchoolLink.zip](https://github.com/david53001/schoollink-releases/releases/latest/download/SchoolLink.zip), open it, and drag **SchoolLink** into **Applications**.
2. Paste this into Terminal and press Return:

```bash
xattr -dr com.apple.quarantine /Applications/SchoolLink.app && open /Applications/SchoolLink.app
```

This opens SchoolLink without the "Apple could not verify" warning (the app isn't registered with Apple's paid
developer program; this does the same as Open Anyway in System Settings → Privacy & Security).

## Uninstall

```bash
curl -fsSL https://github.com/david53001/schoollink-releases/releases/latest/download/uninstall.sh | bash
```

This deletes everything SchoolLink saved, so to install it again later, ask the owner to remove your username
first, then sign up again. (Or quit SchoolLink and drag it from Applications to the Trash: installed again on the
same Mac, it then sets itself up by itself.)

---

This repository holds only the compiled app and its update feed, attached to each [release](../../releases). There is
no source code here.
