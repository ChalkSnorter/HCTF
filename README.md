# hmmmm_AlmostThere — CTF Writeup

A multi-step OSINT / steganography style challenge involving hidden image data, Instagram clues, Base64 decoding, email interaction, and a final website login.

## Challenge Summary

During an investigation, a strange image was found containing hidden information that eventually leads to a flag.

### Challenge hints

* The challenge name is an Instagram account
* The Instagram bio hints at the encoding used

## Challenge Design

The challenge was built in several stages:

1. A hidden Base64 string was appended to the end of an image file in hex.
2. Decoding that string reveals an Instagram username.
3. The Instagram account bio hints that Base64 was used more than once.
4. A highlight on the Instagram account contains a double-encoded Base64 string.
5. Decoding it reveals an email address.
6. Sending an email to that address returns an automatic reply containing a website link.
7. One of the Instagram posts contains credentials.
8. Those credentials are used on the website login page.
9. The second page of the website contains the flag hidden in the text.

## Step-by-Step Solution

### 1. Inspect the image

Open the challenge image in a hex editor and scroll to the end of the file.

You will find the following Base64 string:

```text
SW5zdGFncmFtVXNlcjogaG1tbW1fQWxtb3N0VGhlcmU=
```

Decoding it gives:

```text
InstagramUser: hmmmm_AlmostThere
```

### 2. Visit the Instagram account

Go to the Instagram account:

```text
hmmmm_AlmostThere
```

The bio contains a hint that says Base64 was used multiple times.

### 3. Check the highlight

Open the highlight on the Instagram profile.

It contains this encoded value:

```text
ZG1WeWVYTmhabVZqZEdadFlXbHNRR2R0WVdsc0xtTnZiUTBLDQo=
```

Decoding it reveals:

```text
verysafectfmail@gmail.com
```

### 4. Send an email

Send an email to:

```text
verysafectfmail@gmail.com
```

An auto-reply returns a link to the website used in the next stage of the challenge.

### 5. Find the credentials

Go back to the Instagram account and inspect the posts.

One of the posts contains plaintext login credentials.

### 6. Log into the website

Open the link from the email reply and enter the credentials from the Instagram post.

After logging in, go to the second page and scroll to the bottom.

### 7. Retrieve the flag

The final sentence contains the flag:

```text
flag{golden_order_shattered_but_not_forgotten}
```

## Final Answer

```text
flag{golden_order_shattered_but_not_forgotten}
```

## Tools / Techniques Used

* Hex editor
* Base64 decoding
* OSINT
* Instagram clue chaining
* Email interaction
* Basic web navigation

## Notes

This challenge combines multiple small clues into one solve path:

* hidden data in an image
* social media investigation
* repeated decoding
* email-based progression
* web login and manual flag discovery

That makes it a good beginner-to-intermediate challenge for players who enjoy chained puzzles.
