# Cryptography Primitives

In this repository, we explore how to use the vigenere cipher, as well as how to break it.

# Implementing the Vigenere Cipher

The Vigenere cipher is a type of encryption scheme similar to a shift cipher, where, given a message M, and a key k of length greater or equal to 1, the key characters are used one at a time as a shift encryption key to a character in the message. If the key length is shorter than the length of the message, once the last character of the key is applied to a character in the message, the key repeats; this continues until the last character in the message is reached.

For example, if we have the following input

message = "cowabunga"

key = "beg"

then the character "c" in message is encrypted using the shift cipher corresponding to the character "b", the character "o" is encrypted according to the shift cipher corresponding to "e", and after the shift cipher corresponding to "g" is applied to character "w", character "a" is encrypted using "b" again.

cowabunga

begbegbeg

The shift cipher uses the following encryption scheme for lower case letters of the alphabet:

a b c d e f g h i j k l m n o p q r s t u v w x y z

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25

The characters of the message and key are converted to the corresponding numbers, and then the numbers are added modulo 26. This produces a ciphertext. For a regular shift cipher encryption scheme, it is easy enough to determine a message, simply by checking all possible 26 keys. Vigenere cipher encryption is much more difficult to carry out a bruteforce attack on.

In this implementation, to keep the environment simple, I am only using the lowercase english letter alphabet as input for both the message and key, but this is easily generalized using an ascii table and hexidecimal representation.

## How to Implement
My outline for implementing the vigenere cipher is as follows.

* Take message and key strings as input

* If length(key) > length(message), Take first amount of key equal to length of message. If length(key)<length(message), repeat key until length(modified key) = length(message). If length(key)=length(message), this step is not needed.

* Define dictionary of lowercase english letters as keys and their corresponding value 0-25 as the value.

* Convert both the message and modified key to a respective list of integers using the dictionary

* Both lists will have the same length. For each index, add the entries from both lists, modulo 26. Save each value as an entry in a new list.

* Use the dictionary to convert back to letters. Concatenate the letters as characters in a string. Return the string

# Breaking the Vigenere Cipher

This project demonstrates that the Vigenere Cipher -- while superior to a simple shift cipher -- is still not perfectly secure.

The issue with the Vigenere cipher is that the chosen key can have length smaller than the message. This allowance is what ends up leaking information: the repeated pattern of letters in the key is enough to help determine what the original message was.

In our set up, we are given a cipher text initially. Taking advantage of the fact that english letters are not chosen in words uniformly, we will recover the key. The steps involved in attacking the Vigenere Cipher are as follows:

* Determine the key length

* Determine each byte of the key

Once the key is known, it can be used easily to decrypt the encrypted message. For simplicity, we assume the encrypted message is written in english.


