---
layout: post
title: Public Cryptography
description: Our world would be a very different place if tech giants and banks couldn't guard passwords.
summary: About RSA algorithm and its mechanics
tags: [Math, Tech]
---

![Unsplash](https://source.unsplash.com/EPeK7w5Eeic/800x450/ "Source: unsplash.com/@proxyclick")

If you think about it, keeping secrets is fundamental to how we organize societies.

**RSA algorithm** is the workhorse technique which enables this secret keeping. We can understand **how** this public cryptography works with elementary number theory. Understanding **why** it works is a whole another topic.



## An Analogy

![Unsplash](https://source.unsplash.com/SHeN-2puD7s/800x450/ "Source: unsplash.com/@groovelanddesigns")

One way to send a secret (a password) is to mail a sealed envelope to your banker. This is not secure because the envelope can be sealed and unsealed by anybody with access to it (like the mailman). 

Instead, your banker builds a public mailbox available to the entire world. Anybody can drop envelopes into it. But, only the banker has a private key to open this public mailbox.

In short, the Bank publishes a public key to **encrypt** messages and will keep secret the private key to **decrypt** those messages.

**RSA algorithm** works similar to this analogy.


## Before you read further, this note is Important

**Modulus** is the remainder after a number is divided by a divisor. 

- Since $$1$$ is the remainder resulting from $$ 11/5 $$ or $$ 11/2 $$,  you can write 
    - $$11\bmod 5 \equiv 1$$ or  $$11\bmod 2 \equiv 1$$


## Encryption & Decryption with an example

![Unsplash](https://source.unsplash.com/hecib2an4T4/800x450/ "Source: unsplash.com/@jeswinthomas")

- The RSA algorithm needs 3 elements to work:
  - `n` > A public *modulus* 
  - `e` > A public *encryption key*
  - `d` > A private *decryption key*  

<br>
- With these set of keys 
  - `m`, a  **message** is encrypted using public key into `c`. 
  - `c`, the **cipher text** is then decrypted using private key to return the original message `m`.


<br>
- To illustrate RSA, I'll use: `n` = $$33$$,  `e` = $$7$$,   `d` = $$3$$,  `m` = $$31$$
  - `m` is **encrypted** with the below function
    
    : $$ m^e \bmod n \\ \equiv {31^7} \bmod {33} \\ \equiv remainder \ of \ {31^7}/{33} \\ = 4$$

  So, `c` $$= 4$$


  - `c` is **decrypted** with the below function
    
    : $$ c^d \bmod n \\ \equiv {4^3} \bmod {33} \\ \equiv remainder \ of \ {4^3} / {33} \\ = 31$$

  So, `m` $$= 31$$




## Rules of RSA algorithm

![Unsplash](https://source.unsplash.com/_U-x3_FYxfI/800x450/ "Source: unsplash.com/@punttim")


Joining  encryption and decryption functions, we end up with: <br>
$$  (m^e \bmod n)^ d \bmod n = m $$ 

But, this function holds true only if `n`, `e`, `d` and `m` satisfy four conditions.

Lets verify if `n` $$= 33$$ , `e` $$= 7$$ , `d` $$= 3$$ and  `m` $$= 31$$  satisfy those conditions:

- `n` should be $$ p \times q$$ where both `p` and `q` are prime numbers. 
  - `n` $$= 33$$ satisfies the condition:
  - because, $$ 33 = 3 \times 11 $$, where both $$3$$ and $$11$$ are primes

<br>
- `e` must be $$>1$$ and a **co-prime** of $$ (p-1) \times (q-1) $$.
  - `e` $$= 7$$ satisfies the condition:
  - because, $$ (p-1) \times (q-1)  \\ \equiv (3-1) \times (11-1) = 20 $$
  - $$7$$ and $$20$$ are co-primes since their greatest common divisor is $$1$$

<br>
- `d` must be such that $$ ( d \times e) \bmod ((p-1) \times (q-1)) \equiv 1 $$
  - `d` $$= 3$$ satisfies the condition: 
  - because, $$ ( 3 \times 7) \bmod ((3-1) \times (11-1)) \\ \equiv 21 \bmod 20 \equiv 1$$

<br>
- `m` must be less than `n` 
  - `m` $$= 31$$ satisfies the condition: 
  - because, it is less than `n` $$\equiv 33$$