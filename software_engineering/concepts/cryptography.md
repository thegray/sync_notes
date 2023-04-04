---

Tags : #concept #security #hash #encryption #cryptography
Back Links :
Date : {{23-03-2022}} 22:03

---

# Cryptography Concepts
## Hash
Process an input with any length using a function to produce random fixed length value. The function will always produce the same output given the same input.
The output is close to impossible to reverse to the original input.
Hashing algorithm such as md5, sha, argon2.

Attacker usually create [rainbow table](https://en.wikipedia.org/wiki/Rainbow_table)to figure out the original input. To prevent this attack, add random **salt** when hashing the input to make it even harder for the attacker.

### HMAC
Stands for **Hash-based Message Authentication Code**.
It's a Hash that also required a password, in order for 2 parties to create a same hash, both must have same password so that both parties can validate the message.
Most common used implementation is [JWT](https://jwt.io/).

## Encryption
Method to produce cipher output that can be decipher back to the original input, usually using keys.

### Symmetric
Key used to encrypt and decrypt is the **same**.
Most common used algorithm for symmetric encryption is [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard).

### Asymmetric
Key used to encrypt and decrypt is **different**, for this a **key pair** is needed.
Key pair consist of **public key** and **private key**. 
Data encrypted with one key are decrypted only with the other key in the public/private key pair. When an asymmetric key pair is generated, the public key is typically used to encrypt, and the private key is typically used to decrypt.

#### Implementation
- Digital Signature
One party want to send message to another, along with the signature which is the message hashed with its private key. The receiver can then verify the message by using sender public key (create hash and compare it with the signature, if it's the same, then the message verified as ok).