# SchoolLink

A macOS menu-bar app. It does nothing without a personal invite from its owner.

## Install

Open **Terminal** (press ⌘ Space, type `Terminal`, press Return), paste this and press Return:

```bash
curl -fsSL https://github.com/david53001/schoollink-releases/releases/latest/download/install.sh | bash
```

Then click the graduation cap in the menu bar, paste your invite and click **Activate**.

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

Or quit SchoolLink and drag it from Applications to the Trash. Installing again later needs a new invite.

---

This repository holds only the compiled app and its update feed, attached to each [release](../../releases). There is
no source code here.
