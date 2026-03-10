# picoCTF Writeup – Crack the Gate 1

## Challenge Information

Platform: picoCTF
Challenge: Crack the Gate 1
Category: Web Exploitation
Difficulty: Easy
Week: Week-3

Challenge Link:
https://play.picoctf.org/practice/challenge/520

---

# Description

The challenge provides a restricted web portal where a user named **ctf-player** is suspected of hiding sensitive information.

We know the email:

[ctf-player@picoctf.org](mailto:ctf-player@picoctf.org)

However, the password is unknown and normal guessing techniques do not work.
The challenge hint suggests that the developer might have left a hidden clue inside the web application.

---

# Investigation Process

## 1. Launch the challenge

Start the challenge instance from picoCTF and open the login portal.

---

## 2. Inspect the webpage source

Right-click on the webpage and select:

View Page Source
or press:

CTRL + U

Inside the HTML source we find a suspicious developer comment:

```
<!-- ABGR: Wnpx - grzcbenel olcnff: hfr urnqre "K-Qri-Npprff: lrf" -->
```

The text looks scrambled.

---

## 3. Decode the message

The text appears to be **ROT13 encoded**.

Using a ROT13 decoder reveals:

```
NOTE: Jack - temporary bypass: use header "X-Dev-Access: yes"
```

This indicates a **developer backdoor**.

---

## 4. Capture the login request

Open browser developer tools:

Inspect → Network tab

Attempt to login using:

Email: [ctf-player@picoctf.org](mailto:ctf-player@picoctf.org)
Password: anything

This generates a **POST request**.

Copy the request as **cURL**.

---

## 5. Add the developer header

Modify the request by adding the header:

```
X-Dev-Access: yes
```

Example:

```bash
curl -X POST <login-url> \
-H "X-Dev-Access: yes"
```

---

## 6. Retrieve the flag

After sending the modified request, the server bypasses authentication and returns the flag.

---

# Flag

```
picoCTF{brut4_f0rc4_3c6b118b}
```

---

# Proof

Screenshot of the solved challenge is included in this folder:

solution.png

---

# Skills Learned

* Inspecting webpage source code
* Identifying hidden developer comments
* ROT13 decoding
* Understanding HTTP headers
* Basic web exploitation techniques
