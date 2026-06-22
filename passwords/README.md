# Multi-Device Offline KeePassXC Sync

A highly secure, 100% private, and cloud-free workflow for synchronizing KeePassXC databases across multiple devices using LocalSend. 

This method completely avoids big-tech cloud providers (Google Drive, iCloud, Dropbox) and self-hosted servers (Nextcloud, Vaultwarden). Instead, it relies on local network peer-to-peer transfers and KeePassXC's native database merging capability.

---

## The Core Philosophy
* **Zero Cloud Footprint:** Your password database (`.kdbx`) never touches the internet or third-party servers.
* **True Local Ownership:** Your devices hold the only copies of your data.
* **Low Friction P2P:** Uses LocalSend to instantly drop files between devices over local Wi-Fi without manual USB swapping or directory mounting.
* **Cryptographic Syncing:** Relies on KeePassXC’s intelligent merge feature to combine entries without losing data or creating manual sync conflicts.

---

## Prerequisites

1. **[KeePassXC](https://keepassxc.org):** Installed on your desktop/laptop computers. *(Note: Compatible mobile apps like KeePassium/Strongbox on iOS or Keepass2Android can adapt to this workflow).*
2. **[LocalSend](https://localsend.org):** Installed on all devices you intend to sync. LocalSend is open-source and cross-platform (Windows, macOS, Linux, Android, iOS).
3. **Network:** All devices must be connected to the same local network (e.g., your home Wi-Fi).

---

## Step-by-Step Sync Workflow

### Step 1: Make Changes on Device A
Add, edit, or delete passwords on your active device (e.g., your laptop) as you normally would. Press **Save** to update your primary database file (`passwords.kdbx`).

### Step 2: Send via LocalSend
1. Open **LocalSend** on Device A and select your `passwords.kdbx` file.
2. Open **LocalSend** on Device B (e.g., your desktop) so it is discoverable.
3. Send the file from Device A to Device B.

### Step 3: Receive and Name Temporarily
On Device B, accept the incoming file. Save it to a temporary directory (like your Downloads folder) and name it something distinct, such as `mergeme.kdbx`.

### Step 4: Merge in KeePassXC
1. Open your main database on Device B.
2. In the top menu, navigate to **Database** > **Merge from KeePassXC database...**
3. Select the `mergeme.kdbx` file from your temporary folder.
4. Enter the master password for the incoming file. KeePassXC will intelligently merge any new or updated entries chronologically without deleting or duplicating existing records.

### Step 5: Post-Sync Cleanup
Delete the temporary `mergeme.kdbx` file from your Downloads folder to prevent clutter and avoid accidental modifications to the wrong file in the future.

> **Security Note on File Deletion:** Explicitly "shredding" or overwriting the temporary file on modern SSDs is generally redundant. Because `.kdbx` files are heavily encrypted (ChaCha20/AES-256) by default, the raw data left on the disk is entirely unreadable without your master passphrase. Full-disk encryption (BitLocker/FileVault) is recommended for hardware-level security.

---

## Best Practices & Tips

* **Unify Master Passwords:** Ensure the database files across all your devices share the exact same strong master passphrase. This keeps the merging process seamless, as you can reuse the same credentials to open the temporary file during a merge.
* **The "Reverse Sync" Habit:** Merging is a one-way operation. Once Device A is merged into Device B, Device B holds the most up-to-date master copy. To keep Device A mirrored perfectly, immediately use LocalSend to send the newly merged file *back* to Device A and overwrite its old file.
* **Speed Up Transfers:** In LocalSend's settings, add your frequent devices to your "Favorites" list to bypass the network scan phase and send files with just two clicks.
