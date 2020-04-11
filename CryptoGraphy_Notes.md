# Cryptography - Pluralsight

Link to the course -

## Modules Covered

* Understanding Cryptography
* Cryptography tools
* PKI made Simple
* Encrypting Emails,Files, and Disk Drives
* Attacks against Cryptography
* Countermeasures

# Module 1 - All about Crypto

## Purpose Of Crypto

```
The purpose of cryptography is to protect data transmitted in the likely presence of an adversary a cryptography transformation of data is a procedure by which plain text data is disguised, or encrypted, resulting in an altered text, called ciphertext, that does not reveal the original input.

What Does it Bring to the Table :- 
1. Nonrepudiation - 
2. Integrity - 
3. Authrntication - 
4. Confidentiality - 
```

## The Process of Crypto - 

```
Senders Side process
------------     ------------          ------------ 
-Plain Text-   + -Encryption-   =====  -Ciphertext-
------------     ------------          ------------ 

Receiver side Process
------------     ------------          ------------ 
-CipherText-   + -Decryption-   =====  -Plain text-
------------     ------------          ------------ 
```

## Types Of Crypto

* Symmetric
* Asymmetric

### Symmetric Crypto

```
Advantages

1.Both Parties use the same Key for encryption and decryption.
2.Super Fast method.
3.Easy to implement.
4.Key is not Transmitted with the data

Downsides

1.Not very secure.
2.Key has to be distirbuted to all the parties.
3.Dictionary Attacks on the key.
4.Manageability - If the key is changed then it needs to be redistributed.
5.Hard to prove Authenticity.
```

### Asymmetric Crypto

```
Advantages

1.Two keys required(Public and private key).
	-Public key to encrypt the data and private key to decrypt te data. 
	-We dont have to share the private key at all so its very secure with us.
	-Public key can be distributed without any issues.
2.More Convenient.
3.Digital Signatures.
4.Better security.

Downsides

1.Slower and more CPU power.
2.Huge issues if private Key is exposed.
3.MITM and Brute-force attacks possible.
4.No decryption if the Private key is lost. 
```

## Breaking the LAW 

```
1.Government Access to the Keys. (GAK)
2.Keys are given up.
3.Requires a using warrant.
4.Key Escrow is used (Third party to store your keys)(SHIT).
```

## CIPHERS

```
In cryptography, a cipher is an algorithm for performing encryption or decryption—a series of well-defined steps that can be followed as a procedure. An alternative, less common term is encipherment. To encipher or encode is to convert information into cipher or code.

There are two types of Ciphers
1.Classic Ciphers.
2.Modern Ciphers.

Classical Cipher :- 
1.Substitution - 
2.Transposition -

Modern Cipher :-
1.Symmetric - 
2.Asymmetric - 
3.Block -
4.Stream - 
```

## Other Algorithms 

```
1.DES - 64 bit block
		56-bit key for encryption/decryption 

2.3DES - Does DES algorithm . Each DES cycle is done using a different key also called the KEY BUNDLE (K1,K2,K3).
		 K1 - DES encrypt using K1
		 K2 - DES decrypt using K2
		 K3 - DES encrypt using K3

3.AES - 128-bit Block size
		128/192/256 bit keys.
		It is Asymmetric algorithm

4.RC4 - (Rivest Cipher 4)
		Variable key size symmetric key cipher
		Used in WEP

5.Blowfish - Symmetric Walk cipher
			 Same key to encrypt/decrypt
			 64-bit block
			 32-448 bit key
			 Super Fast

6.Twofish - 128-bit block
			256 bit key
			Single Key
```

## Standards And Protocols

```
DSA - Digital Sigature Algorithm
1.320-bit for Signatures
2.512-1024 bit for security
3.Private-Public Keys

RSA -  Rivest, Shamir, Adleman
1.Uses two Large Prime Numbers
2.Very secure with larger prime Numbers
=============================================================================
THE MATH (Brain damage)
1.Two large prime numbers are taken a and b
2.c is calculated by c = a.b .C is now called the Modulus
3.Now choose a number e such that 
	1.e is less than (a-1).(b-1)
	2.e is a coprime with c and (a-1).(b-1)
4.choose d such that
	d.e(mod (a-1).(b-1)) = 1
5.Encrypt data using (e,c) and distribute it to others [(e,c) = Public key can be shared no problem]
6.Once they get this data they can decrypt it using (d,c) [(d,c) = Private key]
There you go man have fun stay protected
=============================================================================

Diffie Heliman Algorithm
Allows two parties to form a shared key over a Public Network
1.Uses Public and private key.
2.Works on Modular Arithmetic.

```

## HASHES

```
They are one way functions and once text is hashes they cannot be reversed .
MD2 , MD4 , MD5  - 128 bit
SHA1- Secure Hash Algorithm - 160 bit - PGP,TLS,SSH,SSL
SHA3- Sponge construction (Input is Absorbed and output is squeezed out ).
SHA256
........... many more read online.
```

## Designed for Messages 

```
HMAC - Embedded hash function 
CHAP - Change Handshake Auth Protocol - PPP,3-way Handshake
EAP - Extensable Auth Protocol - Passwords,OTP,ID cards,Smart Tokens.
```

# Module 3 - Tools 

## MD5 Hash Calculators

```
1.MD5 Calculater
2.Hash My Files
3.Online MD5
4.Microsoft FCIV
```

## Cryptography : Folders /Files

```
1.EFS
2.7Zip
3.GnuPG
4.AxCrypt
```

## Cryptography : Drives

```
1.BitLocker
2.VeraCrypt
3.FileVault
4.GNOME Disk Utility
```

## Cryptography : Mobile Devices

```
1.Secret Space Encryptor
2.Sealnote
3.LastPass
```

# Module 4 - PKI - Public Key Infrastructure

## What is PKI ?

```
Public Key Infrastructure (PKI) is a technology for authenticating users and devices in the digital world. The basic idea is to have one or more trusted parties digitally sign documents certifying that a particular cryptographic key belongs to a particular user or device.

PKI consists of -

Certificate Management System - (CMS)
Digital Certificates
Validation Authority (VA)
Certificate Authority (CA)
Registration Authority (RA)
End User
```

# Module 5 - Emails,Files,Disk Drivers

## SSL and TLS 

```
SSL- Secure Socket Layers
	private channel
	Auth Channel
	Reliable Channel

TLS - Transport Layer Security
	Little Complicated see Youtube video instead.
```

## Pretty Good Privacy

```
Encryption messages and files
Signing
Deleting Files
Compression

STEPS :-
1.Users encrypts with PGP - Compression is applied
2.Creates a random key and Encrypts the data
3.Random key is encrypted with recipients publinc key
4.Random key is attached and sent to the recipients
```

# Module 6 - The Attacks Against Cryptography

## Cryptanalysis Methods
```
Types of Analysis 

1.Linear Cryptanalysis:-
	*Blocks ciphers
	*Plaintext attacks
	*More Pairs = Better Successful
2.Diffrential Cryptanalysis:-
	*Symmetric Key algorithm
	*Looks at the differences of input and output
	*Plaintext an ciphertext

3.Integral Cryptanalysis:-
 *Block Ciphers
 *Looks at pairs of input that differ a bit

```

## Code-Breaking Methods

```
1.Frequency Analysis
2.Brute Force
3.One-time Pad
4.Trickery and Deceit(Social Engineering)
```

## The Attacks

```
1.Known-plaintext
2.Chosen Ciphertext
3.Midnight Attack
4.Rubber Hose
5.Chosen-Key
6.Timing
7.MITM attacks
8.Dictionary Attack
9.Related-Key
10.Chosen Plaintext
11.Adaptive Chosen Plaintext
12.Ciphertext-only
13.Rainbow Table
14.Birthday attack(Dont know this ?? WTF is this)
15.Side Channel attack
16.Hash Collisions
17.DUHK- Dont use hard Coded Keys.
```

# Module 7 - Countermeasures

## 12 things you can do 

```
1.Access only Given to app and users directly
2.IDS - logs
3.Passphrases and Passwords
4.No keys inside the source code
5.Dont transfer Private key 
6.Symmetric algo use 168 or 256 bits
7.Message Auth
8.Asymmetric algo use 1536 or 2048 bits
9.Hash algo use 168 or 265 bits
10.No "HOME MADE" Crypto Algorithms
11.Limits on number of operations
12.Hash function outputs large bit length

```

