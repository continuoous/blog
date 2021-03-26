---
layout: post
title: Public Cryptography
description: About why data science  can be learnt through spreadsheets
summary: About why data science  can be learnt through spreadsheets
tags: [Excel, Datascience]
---

Our world would be a very different place if tech giants and banks couldn't guard passwords. If you think about it, **keeping secrets** is fundamental to how we organize societies.

**RSA algorithm** is the workhorse technique which enables this secret keeping. We can understand **how** this *public cryptography* works with elementary number theory. Understanding **why** it works is a whole another topic.

.

___

.


## An analogy

One way to send a secret (a password) is to mail a sealed envelope to your **banker**. This is not secure because the envelope can be *sealed* and *unsealed* by anybody with access to it (like the mailman).

Instead, your banker builds a **public mailbox** available to the entire world. Anybody can drop envelopes into it. But, only the banker has a **private key** to open this **public mailbox**.

In short, the Bank publishes a *public key* to **encrypt ** messages and will keep secret the *private key* to **decrypt ** those messages.

**RSA algorithm** works similar to this analogy.


.

___

.



### Before you read further, this note is Important

* Modulus is the **remainder** after a number is divided by a divisor.
* Since 11 = 2 · 5 + 1,  you can write 
  * 11 mod (5) = 1
  * 11 mod (2) = 1 
* because **1** is the remainder resulting from 11÷5 or 11÷2


.

___

.



## Encryption & Decryption with an example

The RSA algorithm needs 3 elements to work:
1. A public **modulus** `n`
2. A public **encryption** key `e`
3. A private **decryption** key `d`

If our *message* is `m` and the *encrypted message* is `c`. When `c` is decrypted, we must end back with the original message `m`.

* To illustrate RSA mechanics, I'll use 
    * `n=33`
    * `e=7`
    * `d=3`
    * `m=31`

.
___

.

### Encryption
* The message `m` is encrypted with the function: 
    * `m^e mod (n) `
    * Its the same as the **remainder **of `31^7/33` which is `4`
    * So, `c=4`

.

___

.

>> `31^7 = 27512614111 = 833715579 · 33 + 4 `


### Decryption
* The message `c` is decrypted with the function: 
    * `c^d mod(n) `
    * Its the same as the **remainder **of `4^3/33` which is `31`
    * Therefore, `m=31`
.
>> `4^3 = 64 = 1 · 33 + 31 `

.
___

.


## Rules of RSA algorithm

Above, we encrypted the message `m` to `c` and then decrypted `c` back to the original message `m`. If we join the encryption and decryption function, this is what we end up with:

`m^e mod(n)^d mod(n) = m`

But, this function holds true only if `n`, `e`, `d` and `m` satisfy four conditions.

Lets verify if `n=33 , e=7 , d=3 and  m=31`  satisfy those conditions:

- `n` should be `p · q` where both `p` and `q` are prime numbers.
    
    - `n=33` satisfies the condition because
        
        - `33=3·11`, where both `3` and `11` are primes

___

- `e` must be `>1` and `<(p-1)·(q-1)` and a **co-prime** of `(p-1)·(q-1)` 
    
    - `e=7` satisfies the condition because
        
        - `(p-1)·(q-1) = (3-1)·(11-1) = 20`
        
        - `1<7<20`
        
        - `7` and `20` are co-primes since their greatest common divisor is `1`

___

- `d` must be such that `(d·e)   mod ((p-1)·(q-1)) = 1`
    
    - `d=3` satisfies the condition because
        
        - `(3·7)   mod   ((3-1)·(11-1)) = 21   mod   20 = 1`

___

- `m` must be less than `n`
    
    - `m=31` satisfies the condition because it is less than `33`

___