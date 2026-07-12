## if gpg key not found or skipped error occured while commit
generate gpg key again: 

```bash
gpg --full-generate-key
```
- Options to select: 
 → (1) RSA and RSA (widely compatible but modern tech ed25519 also supported and more secure)
 → 4096 (size)
 → 0 (expiration time)
 → enter your name + email (must match git config user.email & user.name)

Get the keyid and configure it for global use: 

```bash
gpg --list-secret-keys --keyid-format=long
git config --global user.signingkey <KEY-ID>
```
