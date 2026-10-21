# linkedin-posts

My LinkedIn posts, signed with my PGP key.

Key fingerprint:

```
5CF7 03CE A890 84A7 283C  3A3E D810 5826 0CF4 4A4E
```

## Verifying a post

Each post `<post>.txt` has a clearsigned copy, `<post>.txt.asc`, which holds
the text and the signature together.

```sh
# 1. Import my public key (only needed once)
curl https://git.emilio-mendoza.com/emiliomendoza.gpg | gpg --import

# 2. Download the signed post (replace <post> with the post name, e.g. git)
curl -O https://git.emilio-mendoza.com/emiliomendoza/linkedin-posts/raw/branch/main/<post>.txt.asc

# 3. Verify it
gpg --verify <post>.txt.asc

# 4. Print exactly the text that was signed
gpg --decrypt <post>.txt.asc
```

Images have detached signatures (`<image>.sig`). Download both files, then:

```sh
gpg --verify "<image>.sig" "<image>"
```

You should see `Good signature from "Emilio Mendoza (Free the Internet)
<contact@emilio-mendoza.com>"`, and the primary key fingerprint should match
the one above.

gpg will also warn that the key "is not certified with a trusted signature".
That's expected. It only means you haven't marked my key as trusted in your
own keyring.
