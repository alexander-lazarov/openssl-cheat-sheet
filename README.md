# OpenSSL cheat sheet

## Generating/manipulating keys

### Generate a `.pem` from `crt` and `key` files

```bash
cat foo.com.crt foo.com.key gd_bundle.crt > foo.com.pem
```

## Testing SSL connections

Run the command, depending on the protocol you want to test. If everything is
OK, you should see output similar to this, ending with `Verify return code: 0
(ok)`:

```
SSL-Session:
    Protocol  : TLSv1
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    Session-ID-ctx:
    Master-Key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    Key-Arg   : None
    Start Time: 1452531417
    Timeout   : 300 (sec)
    Verify return code: 0 (ok)
```

- HTTP / IMAP / POP3 / SMTP
```bash
openssl s_client -connect hostname.com:443
```

- IMAP / POP3/ SMTP (StartTLS)
```bash
openssl s_client -starttls smtp -crlf -connect hostname.name:587
```
