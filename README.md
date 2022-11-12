
# Project Title

A brief description of what this project does and who it's for

This project used for signing PDF files and then can be verified by adobe and other tools. 

Mostly tech giants used for signing pdf files so that they can be verified.

For using this project you need to install the required dependencies from requirement.txt

Then add your new certificate here. example(client-identity.p12)

Cirtificate can be created using openssl library

To create p12 certificate you can use these following steps:

```bash
openssl genrsa -out key.pem 2048
```
Generate a Certificate Signing Request: 

```bash
openssl req -new -sha256 -key key.pem -out csr.csr
```

Generate a self-signed x509 certificate suitable for use on web servers:
```bash
openssl req -x509 -sha256 -days 365 -key key.pem -in csr.csr -out certificate.pem
```

Create SSL identity file in PKCS12 as mentioned:
```bash
openssl pkcs12 -export -out client-identity.p12 -inkey key.pem -in certificate.pem
```
Here after generating certificate you can run the python script using command line: 
```bash
python3 pdf-signer.py certificate-path password pdf logo-path
```