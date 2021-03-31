---
layout: post
title: Public Cryptography
description: About why data science  can be learnt through spreadsheets
summary: About why data science  can be learnt through spreadsheets
tags: [Excel, Cryptography]
---

Our world would be a different place if tech giants and banks couldn't guard passwords. If you think about it, *keeping secrets* is fundamental to how we organize societies.

**RSA algorithm** is the workhorse technique which enables this secret keeping. We can understand **how** this public cryptography works with elementary number theory. Understanding **why** it works is a whole another topic.


## An Analogy

One way to send a secret (a password) is to mail a sealed envelope to your banker. This is not secure because the envelope can be *sealed* and *unsealed* by anybody with access to it (like the mailman). 

Instead, your banker builds a public mailbox available to the entire world. Anybody can drop envelopes into it. But, only the banker has a *private key* to open this *public mailbox*.

In short, the Bank publishes a *public key* to **encrypt** messages and will keep secret the *private key* to **decrypt** those messages.

**RSA algorithm** works similar to this analogy.


## Before you read further, this note is Important

**Modulus** is the *remainder* after a number is divided by a divisor. 

- Since $$1$$ is the remainder resulting from $$ \cfrac{11}{5} $$ or $$ \cfrac{11}{2} $$,  you can write 
    - $$11\bmod 5 \equiv 1$$ or  $$11\bmod 2 \equiv 1$$


## Encryption & Decryption with an example

- The RSA algorithm needs 3 elements to work:
  - `n` > A public *modulus* 
  - `e` > A public *encryption* key 
  - `d` > A private *decryption* key

- With these set of keys 
  - `m`, a  *message* is *encrypted* using *public key* into *cypher text* `c`. 
  - `c` is then decrypted using *private key* to return the original message `m`.

- To illustrate RSA mechanics, I'll use: 
  - `n` = 33,  
  - `e` = 7,  
  - `d` = 3, 
  - `m` = 31

- **Encryption**: 
  - `m` is encrypted with the function: $$ m^e \bmod n $$
      * Its the same as the **remainder** of $$ \cfrac {31^7} {33} $$ which is $$ 4 $$
      * So, `c` = $$4$$

- **Decryption**:
  - `c` is decrypted with the function: $$ c^d \bmod n $$ 
    * Its the same as the **remainder** of $$ \cfrac {4^3} {33} $$ which is $$31$$
    * Therefore, `m` = $$31$$



## Rules of RSA algorithm

Above, we encrypted the message `m` to `c` and then decrypted `c` back to the original message `m`. If we join the encryption and decryption function, this is what we end up with:

$$  (m^e \bmod n)^ d \bmod n = m $$ 

But, this function holds true only if `n`, `e`, `d` and `m` satisfy four conditions.

Lets verify if `n` = 33 , `e` = 7 , `d` = 3 and  `m` = 31  satisfy those conditions:

1. `n` should be $$ p \times q$$ where both `p` and `q` are prime numbers.
  - `n` = 33 satisfies the condition because
  - $$ 33 = 3 \times 11 $$, where both $$3$$ and $$11$$ are primes
2. `e` must be $$>1$$ and a **co-prime** of $$ (p-1) \times (q-1) $$
  - `e` = 7 satisfies the condition
    - because $$ (p-1) \times (q-1)  \equiv (3-1) \times (11-1) = 20 $$
      - $$7$$ and $$20$$ are co-primes since their greatest common divisor is $$1$$
3. `d` must be such that $$ ( d \times e) \bmod ((p-1) \times (q-1)) \equiv 1 $$
  - `d` = $$3$$ satisfies the condition 
    - because $$ ( 3 \times 7) \bmod ((3-1) \times (11-1)) \equiv 21 \bmod 20 \equiv 1$$
4. `m` must be less than `n` 
  - `m` = $$31$$ satisfies the condition because it is less than $$33$$