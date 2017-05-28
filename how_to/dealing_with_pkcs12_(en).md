# PKCS#12

It's an archieve file format for storing many cryptography objects as a single file. It's commonly used to pack a private key and some other certificate data. The file extension is either **.p12** or **.pfx**.

These files can be created, parsed and read out with the OpenSSL `pkcs12` command.

Convert a PKCS#12 file (.pfx .p12) containing a private key and certificates to PEM.
 ```bash
onur@habion:~$ openssl pkcs12 -in keyStore.pfx -out keyStore.pem -nodes
 ```
Also you can extract CA certificate, client certificate and private keys into different files. `pkcs12` has these options:
 ```bash
 onur@habion:~$ openssl pkcs12 --help
    ...
    -clcerts      only output client certificates.
    -cacerts      only output CA certificates.
    -nokeys       don not output private keys.
    -nocerts      don not output certificates.
    ...
 ```
Examples:
 ```bash
 onur@habion:~$ openssl pkcs12 -in store.p12 -cacerts -nokeys -out store_ca.pem
 onur@habion:~$ openssl pkcs12 -in store.p12 -clcerts -nokeys -out store_cl.pem
 onur@habion:~$ openssl pkcs12 -in store.p12 -nocerts -out store_pkey.pem
 ```
 These three files will be useful for some VPN clients like **Shrew**. It wants server certificate authority file, client certificate file and client private key file at its *credentials* tab.
 ![Shrew Credentials](/how_to/images/c_shrew_cert_import.jpg?raw=true "Shrew Credentials")