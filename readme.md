# How to get Keys

* Generate a key pair (genpkey is the generic replacement for genrsa). Both Private and public key encoded in PKCS8 PEM file).
~~~ openssl genpkey -algorithm rsa -pkeyopt rsa_keygen_bits:2048 -out privkey.pem
~~~

* Extract public key from PKCS8 PEM file containing key pair.
~~~ openssl pkey -in privkey.pem -pubout -out pubkey.pem
~~~

* Extract public key from certificate.
~~~ openssl x509 certfile.pem -pubkey -noout
~~~

* Extract public key from CSR
~~~ openssl req certfile.pem -pubkey -noout
~~~

* Use a public key generated by openssl to create a ssh compatible version of the public key 

~~~~ ssh-keygen -i -m pkcs8 -f pubkey.pem >id_rsa.pub 
~~~~

