# Stateless password manager
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
