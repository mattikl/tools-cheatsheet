# OpenSSL

## X.509 Certificates

Concepts:

* certificate/key encodings: PEM (ASCII), DER (binary)
* file extension `.crt` can be either
* `.pem` and `.der` are also used as file extensions for the certificate,
  but it's better to use `.crt` to explicitly state that the file is a certificate,
  since PEM and DER are just encodings that can be used for multiple things,
  most specifically to encode the keys
* `.crt` contains the public key and other public information (issuer, expiration),
  `.key` is the private key

View certificate:

```bash
openssl x509 -in file.crt -text -noout
```

Just view the expiration:

```bash
openssl x509 -in file.crt -enddate -noout
```

### PCKS12

Extracting cert and key from PCKS12 (`.p12 .pfx`):

```bash
openssl pkcs12 -nokeys -in file.pkcs12 -out file.crt
openssl pkcs12 -nocerts -nodes -in file.pkcs12 -out file.key
```

Both files will be PEM-encoded.

## Rand

Generate 32 pseudo-random bytes encoded in base64:

```bash
openssl rand -base64 32
```

## Links

* [Certificates and encodings](https://support.ssl.com/Knowledgebase/Article/View/19/0/der-vs-crt-vs-cer-vs-pem-certificates-and-how-to-convert-them)
