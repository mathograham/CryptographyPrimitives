# Cryptography Primitives

In this repository, two related ideas are explored: breaking the vigenere cipher and

# Breaking the Vigenere Cipher

This project demonstrates that the Vigenere Cipher -- while superior to a simple shift cipher -- is still not perfectly secure.

The issue with the Vigenere cipher is that the chosen key can have length smaller than the message. This allowance is what ends up leaking information: the repeated pattern of letters in the key is enough to help determine what the original message was.

In our set up, we are given a cipher text initially. Taking advantage of the fact that english letters are not chosen in words uniformly, we will recover the key. The steps involved in attacking the Vigenere Cipher are as follows:

* Determine the key length

* Determine each byte of the key

Once the key is known, it can be used easily to decrypt the encrypted message.
