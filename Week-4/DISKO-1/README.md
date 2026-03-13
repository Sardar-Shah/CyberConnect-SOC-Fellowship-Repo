# picoCTF Writeup – DISKO 1

## Challenge Information

* Platform: picoCTF
* Challenge: DISKO 1
* Category: Forensics
* Difficulty: Easy
* Week: Week-4
* Challenge Link: https://play.picoctf.org/practice/challenge/???

---

## Description

The challenge provides a compressed disk image file.
The task is to analyze the disk image and search for the hidden flag.

---

## Steps to Solve

### 1. Download the disk image

```bash
wget https://artifacts.picoctf.net/.../disko-1.dd.gz
```

---

### 2. Extract the compressed file

```bash
gunzip disko-1.dd.gz
```

This produces the disk image file:

```text
disko-1.dd
```

---

### 3. Search for readable strings in the disk image

Since disk images often contain readable text fragments, the `strings` command can reveal hidden data.

```bash
strings disko-1.dd | grep picoCTF
```

---

### 4. Result

The command reveals the flag directly inside the disk image.

---

## Flag

```text
picoCTF{1t5_ju5t_4_5tr1n9_c63b02ef}
```

---

## Proof

Screenshot of the terminal showing the extraction and flag discovery is included as:

solution.png

---

## Skills Learned

* Disk image analysis
* Using `strings` for forensic investigation
* Searching files with `grep`
* Basic digital forensics techniques
