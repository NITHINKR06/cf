- [OpenStego](https://www.openstego.com/)
- [Registry Explorer](https://ericzimmerman.github.io/)



## Experiment 6: Steganography and Watermarking (OpenStego)

### Part A: Data Hiding and Extraction

**Hide data**
1. Open OpenStego and go to the **Data Hiding** tab.
2. Message File: `secret.txt`
3. Cover File: `cover.png`
4. Output Stego File: `stego_output.png`
5. (Optional) Choose AES128 or AES256 and set a password.
6. Click **Hide Data**.

**Extract data**
1. Go to **Extract Data**.
2. Input Stego File: `stego_output.png`
3. Select the output folder.
4. Enter the password.
5. Click **Extract Data** and verify `secret.txt` is recovered intact.

### Part B: Digital Watermarking and Verification

**Generate signature**
1. Open the **Digital Watermarking** tab and select **Generate Signature**.
2. Save the file as `owner_watermark.sig`.
3. Click **Generate Signature**.

**Embed watermark**
1. Select **Embed Watermark**.
2. File to Watermark: `original.png`
3. Signature File: `owner_watermark.sig`
4. Output File: `watermarked.png`
5. Click **Embed Watermark**.

**Verify watermark**
1. Select **Verify Watermark**.
2. Input File: `watermarked.png` (or a suspected copy)
3. Signature File: `owner_watermark.sig`
4. Click **Verify Watermark** and note the confidence percentage.

---

## Experiment 7: Windows Registry Analysis (Registry Explorer)

### 1. Load hives
1. Run Registry Explorer as administrator.
2. Go to **File → Load hive** and select `SYSTEM`, `SOFTWARE`, `SAM`, `NTUSER.DAT`.
3. If prompted to replay transaction logs (`.LOG1` / `.LOG2`), click **Yes** and save the clean hive to a working folder.

### 2. System artifacts

| Artifact | Hive | Key path | What to note |
|---|---|---|---|
| OS info | SOFTWARE | `Microsoft\Windows NT\CurrentVersion` | ProductName, InstallDate, RegisteredOwner |
| Hostname | SYSTEM | `ControlSet001\Control\ComputerName\ComputerName` | Computer name |
| Time zone | SYSTEM | `ControlSet001\Control\TimeZoneInformation` | Time zone bias |
| USB devices | SYSTEM | `ControlSet001\Enum\USBSTOR` | Vendor, model, serial number |
| Network history | SOFTWARE | `Microsoft\Windows NT\CurrentVersion\NetworkList\Profiles` | Past networks, timestamps |

### 3. User artifacts

| Artifact | Hive | Key path | What to note |
|---|---|---|---|
| Local accounts | SAM | `SAM\Domains\Account\Users` | Usernames, RIDs, creation date, last login, failed logins |
| Recent docs | NTUSER.DAT | `Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs` | Recently opened files |
| Typed URLs | NTUSER.DAT | `Software\Microsoft\Internet Explorer\TypedURLs` | URLs typed by the user |
| Typed paths | NTUSER.DAT | `Software\Microsoft\Windows\CurrentVersion\Explorer\TypedPaths` | Folder paths typed by the user |
| Program execution | NTUSER.DAT | `Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist` | Executable paths, run counts, last run time |

### 4. Export findings
Right-click the key or artifact table, choose **Export**, and save as `.csv` or `.txt`.

---

## Notes

- Use the same password for hiding and extracting, otherwise extraction fails.
- Work on copies of the registry hives, never the originals.
- Take a screenshot at each major step for the lab record.
