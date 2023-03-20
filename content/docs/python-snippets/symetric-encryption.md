
# Encrypting and Decrypting Messages with Python

In this blog post, we’ll take a look at how to use the cryptography library in Python to encrypt and decrypt messages.

The cryptography library provides a simple and easy-to-use API for performing common cryptographic operations. In our example script, we use the Fernet class from the cryptography.fernet module to perform symmetric encryption and decryption.

First, we define two functions: encrypt_message() and decrypt_message(). The encrypt_message() function takes in a message as input and generates a key using the Fernet.generate_key() method. It then creates an instance of the Fernet class using this key and uses it to encrypt the message. The encrypted message and key are returned as output.

The decrypt_message() function takes in an encrypted message and key as input. It creates an instance of the Fernet class using the provided key and uses it to decrypt the encrypted message. The decrypted message is returned as output.

In our example script, we demonstrate how to use these two functions by encrypting a simple “Hello World!” message and then decrypting it again.

This is just one example of how you can use Python for cryptography tasks. There are many other libraries available that provide more advanced functionality for encryption, decryption, hashing, digital signatures, etc.

# Code example

```python
from cryptography.fernet import Fernet

def encrypt_message(message):
    key = Fernet.generate_key()
    f = Fernet(key)
    encrypted_message = f.encrypt(message.encode())
    return encrypted_message, key

def decrypt_message(encrypted_message, key):
    f = Fernet(key)
    decrypted_message = f.decrypt(encrypted_message).decode()
    return decrypted_message

message = "Hello World!"
encrypted_message, key = encrypt_message(message)
print(f"Encrypted message: {encrypted_message}")

decrypted_message = decrypt_message(encrypted_message, key)
print(f"Decrypted message: {decrypted_message}")
```
