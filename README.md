Procedure
```Part A: Data Hiding & Extraction

1. Hiding Data (Embedding)

    Launch OpenStego and select the Data Hiding tab on the left panel.

    Message File: Click Browse and select the secret file to hide (e.g., secret.txt).

    Cover File: Select the host image file (cover.png) that will carry the hidden payload.

    Output Stego File: Specify the destination path and filename for the generated stego image (e.g., stego_output.png).

    Encryption Options (Optional): Select an encryption algorithm (e.g., AES128 or AES256) and enter a Password to secure the hidden message.

    Click Hide Data. A confirmation dialog appears once embedding completes.

2. Extracting Data (Retrieving)

    Switch to the Extract Data section under the Data Hiding tab.

    Input Stego File: Browse and select the stego_output.png file.

    Output Folder: Choose the directory where the extracted secret file should be saved.

    Enter the Password used during the hiding phase.

    Click Extract Data. Verify that the original secret.txt file is recovered intact.

```

---

```
Part B: Digital Watermarking & Verification

1. Generating a Watermark Signature

    Open OpenStego and select the Digital Watermarking tab on the left panel.

    Go to Generate Signature.

    Signature File: Specify a save location and filename for the signature (e.g., owner_watermark.sig).

    Click Generate Signature.

2. Embedding the Watermark

    Select Embed Watermark under the Digital Watermarking tab.

    File(s) to Watermark: Browse and select the original image (original.png).

    Signature File: Select the previously generated owner_watermark.sig file.

    Output File: Specify the destination path for the watermarked image (e.g., watermarked.png).

    Click Embed Watermark.

3. Verifying the Watermark

    Select Verify Watermark under the Digital Watermarking tab.

    Input File(s): Select the watermarked.png image (or a suspected copy).

    Signature File: Load owner_watermark.sig.

    Click Verify Watermark to check the confidence percentage score confirming ownership.

```
