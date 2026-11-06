# SchoolLink

A macOS menu-bar app. It does nothing without a personal invite from its owner.

## Install

**1. Download SchoolLink:** [SchoolLink.zip](https://github.com/david53001/schoollink-releases/releases/latest/download/SchoolLink.zip)

**2. Open Terminal** (press ⌘ Space, type `Terminal`, press Return). Copy the whole box below with the copy button
in its corner, paste it into Terminal, and press Return:

```bash
bash <<'EOF'
LEAF=46403275b5a9cedbba8cc2944487397b15e25c77   # SchoolLink's signing certificate
DEST=/Applications; [ -w "$DEST" ] || { DEST="$HOME/Applications"; mkdir -p "$DEST"; }
APP=$(ls -d /Applications/SchoolLink.app "$HOME/Applications/SchoolLink.app" 2>/dev/null | head -1)
if [ -z "$APP" ]; then
  TMP=$(mktemp -d); ZIP=$(ls -t "$HOME"/Downloads/SchoolLink*.zip 2>/dev/null | head -1)
  NEW=$(ls -dt "$HOME"/Downloads/SchoolLink*.app 2>/dev/null | head -1)
  if [ -n "$ZIP" ]; then ditto -x -k "$ZIP" "$TMP" && NEW="$TMP/SchoolLink.app"; fi
  [ -d "$NEW" ] || { echo "❌ SchoolLink isn't in your Downloads folder. Do step 1 first, then paste this again."; exit 1; }
  codesign --verify --deep --strict -R="certificate leaf = H\"$LEAF\"" "$NEW" 2>/dev/null || { echo "❌ That download isn't the real SchoolLink. Nothing was installed."; exit 1; }
  APP="$DEST/SchoolLink.app"; ditto "$NEW" "$APP" && rm -rf "$TMP"
fi
codesign --verify --deep --strict -R="certificate leaf = H\"$LEAF\"" "$APP" 2>/dev/null || { echo "❌ $APP isn't the real SchoolLink. Delete it and start again."; exit 1; }
xattr -dr com.apple.quarantine "$APP" 2>/dev/null; open "$APP"
echo "✅ SchoolLink is installed. Click the graduation cap in the menu bar, paste your invite, click Activate."
EOF
```

This works without internet access, so it also works on the school Wi-Fi. It checks the app is the real, signed
SchoolLink, puts it in Applications and opens it, without the "Apple could not verify" warning. (That warning appears
because the app isn't registered with Apple's paid developer program; the command does what System Settings →
Privacy & Security → Open Anyway would do.)

**3.** Click the graduation cap in the menu bar, paste your invite and click **Activate**. SchoolLink works only on
the school Wi-Fi, Monday–Friday 07:45–16:00, and starts by itself when you log in. Updates install by themselves.

### At home, one line instead

```bash
curl -fsSL https://github.com/david53001/schoollink-releases/releases/latest/download/install.sh | bash
```

## Uninstall

```bash
curl -fsSL https://github.com/david53001/schoollink-releases/releases/latest/download/uninstall.sh | bash
```

Or quit SchoolLink and drag it from Applications to the Trash. Installing again later needs a new invite.

---

This repository holds only the compiled app and its update feed, attached to each [release](../../releases). There is
no source code here.
