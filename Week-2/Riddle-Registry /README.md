# picoCTF Writeup – Riddle Registry

## Challenge Information

* Platform: picoCTF
* Challenge Name: Riddle Registry
* Category: Forensics
* Difficulty: Easy
* Challenge Link: https://play.picoctf.org/practice/challenge/530

---

## Description

The challenge provides a PDF file called **confidential.pdf**.
The description suggests that the flag is hidden within the **metadata of the PDF file**.

The task is to inspect the file and uncover the hidden flag.

---

## Approach

Since the challenge hint mentions **metadata**, the first step is to inspect the PDF file for hidden information.

PDF metadata can sometimes contain encoded or hidden strings.

---

## Steps to Solve

### 1️⃣ Download the file

Download the file provided in the challenge:

```
confidential.pdf
```

---

### 2️⃣ Inspect the PDF metadata

Open the file using a text viewer or inspect its metadata.

Inside the metadata section we find an **encoded string**.

```
cGljb0NURntwdXJzbDNkX20zdGFkYXRhX2YwdW5kIV8N2JNjBiMH0=
```

---

### 3️⃣ Decode the string

The string appears to be **Base64 encoded**.

Decode it using:

Linux command:

```
echo "cGljb0NURntwdXJzbDNkX20zdGFkYXRhX2YwdW5kIV8N2JNjBiMH0=" | base64 -d
```

Or using an online Base64 decoder.

---

### 4️⃣ Result

After decoding we get the flag:

```
picoCTF{puzzl3d_m3tadata_found!_87be60c0}
```

---

## Flag

```
picoCTF{puzzl3d_m3tadata_found!_87be60c0}
```

---

## Proof

Screenshot of the decoding process is attached as:

```
solution.png
```

---

## Skills Learned

* File metadata analysis
* Base64 decoding
* Basic digital forensics techniques
* Investigating hidden information inside files
