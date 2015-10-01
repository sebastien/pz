# Stateless password manager
## Usage
```
Box:code burrows$ pz-master 5
Creating password with 89.24 bits of entropy...
excursioner poikilothermism ecclesiology telarian cymbling 
Box:code burrows$ pz-get gmail.com
Password: <enter master password>
Password: <confirm master password>
password ready (7 seconds to paste password)
. . . . . . . 
wiped
```

Generate (or otherwise choose) one master password.  Use this password, the
website domain (tag) and pz-get to retrieve your password for
the given service.  pz-get copies your password to the clipboard, gives you
a few seconds to paste your password, then removes the password from the
clipboard.

## Installation
`make install`

## Uninstallation
`make uninstall`

## pz-master
Generate master passwords.  It randomly chooses phrases from the OS X dictionary
which has ~250,000 words. The master password should have
log2(250000**WORD_COUNT) bits of entropy.

## pz-get
Retrieve passwords for individual sites.  It uses PBKDF2 to generate keys from a
master password and the website domain. We use the first 16 characters after
base64 encoding the key because most webservices have a small maximum password
size and only support a subset of characters. Each site password should have
16*6 = 96 bits of entropy.

## System Requirements
Uses OS X specific technology (pbcopy, path to dictionary); tested on 10.10
