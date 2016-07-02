# Overview

Cryptography can be a bit obscure when dealing with the how and why of
algorithms. I'm hoping to understand in more detail why certain decisions are
being made and how to use these practices to strengthen my own knowledge. The
basis of this are the terms used and below I'll try and outline the terms I
have come across that could use proper explanation.

## Types of Ciphers

The following are descriptions of the types of ciphers used in cryptography.

### Symmetric Key

The basis of symmetric key encryption is that the same key is used for both
encryption and decryption. It is considered a "shared secret" that two or more
parties share to exchange information. Of course, sharing a secret has its own
set of problems and therefore is considered the main drawback of these
algorithms.

There are two main types of ciphers used in this category: stream ciphers and
block ciphers.

#### Stream Ciphers

Stream ciphers combine the bits of the plaintext with the bits of a
pseudorandom generator one at a time creating a ciphertext. Typically these
algorithms maintain an internal state since each byte of ciphertext depends on
the previous bit dubbing this a **state cipher**. In practice we use
exclusive-or (XOR) to combine the keystream bytes with the plaintext bytes to
develop a ciphertext.

#### Block Ciphers

Block ciphers work on a fixed-length group of bits (blocks) instead of going
one by one. The plaintext is then padded so it is a multiple of the block size
selected. This typically comes to 64 bits but AES actually uses 128 bits.

### Public Key

Public key encryption (also known as asymmetric key encryption) uses a pair of
keys: public and private keys. The public key can be passed out but the private
key belongs only to the owner. In this way, anyone can encrypt a message with a
public key but only the proper private key may decrypt the ciphertext. The best
example that I can think of is SSH when using the RSA key pairs. The owner has
the private key locally and place their public key on the server. When SSHing
into a server the user's public key is looked up and matches up with the
private key allowing access to the server.

## Terms

The following are terms I have come across that could use explanation.

### State Cipher

A state cipher is one where each round of encryption is dependent on the
previous round. Stream ciphers typically have an internal state.

### Keystream

A keystream is a stream of random or pseudorandom characters that are combined
with a plaintext message to produce an encrypted message (the ciphertext).
Usually each character in the keystream is either added, subtracted or XORed
with a character in the plaintext to produce the ciphertext.

### Pseudorandom

A pseudorandom process is a process that appears to be random but is not.
Pseudorandom sequences typically show statistical randomness while being
generated by an entirely deterministic process. Such a process is easier
to produce than a genuinely random one, and has the benefit that it can be used
again and again to produce exactly the same numbers - useful for testing and
fixing software.