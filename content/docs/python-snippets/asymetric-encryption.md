# Using Public/Private Key Pairs for Encryption and Decryption with Python

In this blog post, we’ll take a look at how to use the cryptography library in Python to generate a public/private key pair and use them for encryption and decryption.

The cryptography library provides a simple and easy-to-use API for performing common cryptographic operations. In our example script, we use the rsa module from the cryptography.hazmat.primitives.asymmetric package to generate a public/private key pair and perform RSA encryption with OAEP padding.

First, we generate a private/public key pair using the rsa.generate_private_key() method. We then serialize the private key to PEM format using the private_key.private_bytes() method. This allows us to save the private key to disk or transmit it over a network.

Next, we demonstrate how to load a private key from PEM format using the serialization.load_pem_private_key() method. This allows us to load a previously generated private key from disk or receive it over a network.

Once we have our public/private key pair, we can use them to encrypt and decrypt messages. In our example script, we encrypt a simple “Hello World!” message using the public key and then decrypt it again using the private key.

This is just one example of how you can use Python for cryptography tasks. There are many other libraries available that provide more advanced functionality for encryption, decryption, hashing, digital signatures, etc.

```python
from cryptography.hazmat.primitives.asymmetric import rsa
from cryptography.hazmat.primitives import serialization
from cryptography.hazmat.primitives.asymmetric import padding
from cryptography.hazmat.primitives import hashes

# Generate a private/public key pair
private_key = rsa.generate_private_key(
    public_exponent=65537,
    key_size=2048,
)

public_key = private_key.public_key()

# Serialize the private key to PEM format
pem = private_key.private_bytes(
    encoding=serialization.Encoding.PEM,
    format=serialization.PrivateFormat.PKCS8,
    encryption_algorithm=serialization.NoEncryption()
)

# Load a private key from PEM format
private_key = serialization.load_pem_private_key(
    pem,
    password=None,
)

# Encrypt a message using the public key
message = b"Hello World!"
encrypted_message = public_key.encrypt(
    message,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)

# Decrypt the message using the private key
decrypted_message = private_key.decrypt(
    encrypted_message,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)
```
This code will use the rsa module from the cryptography.hazmat.primitives.asymmetric package to generate a public/private key pair. It will then use these keys to encrypt and decrypt a message using RSA encryption with OAEP padding.
