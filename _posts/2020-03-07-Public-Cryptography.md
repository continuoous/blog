---
layout: post
title: RSA Algorithm
description: Keeping secrets is fundamental for democracies
summary: Our world would be very different if tech giants and banks couldn't guard passwords. RSA is the workhorse algorithm of this secret keeping. Lets explore how it works.
tags: [Tech]
img: https://source.unsplash.com/EPeK7w5Eeic/200x150/
---

![Unsplash](https://source.unsplash.com/EPeK7w5Eeic/800x450/ "Source: unsplash.com/@proxyclick")

1. **RSA algorithm** is the workhorse technique for public cryptography. **How** it works can be understood with elementary number theory. Understanding **why** it works is a whole another topic.


2. Consider this. Sending a secret message in a sealed envelope is insecure because the mailman can unseal the envelope.

3. So, your banker builds a public mailbox available to the entire world. Anybody can drop envelopes into it. But, only the banker has a private key to open this public mailbox.
  ![Unsplash](https://source.unsplash.com/SHeN-2puD7s/800x450/ "Source: unsplash.com/@groovelanddesigns")
  
4. This **analogy** explains how RSA algorithm works. The Bank publishes a public key to **encrypt** messages and guards the private key to **decrypt** those messages.

5. Before we talk about RSA mechanics - lets clarify what **Modulo Operation** does. It returns the remainder resulting from any $$x/y$$. For example, `=MOD(17,5)` returns $$2$$ in Excel. Its math notation is $$17\bmod 5 = 2$$
![Unsplash](https://source.unsplash.com/hecib2an4T4/800x450/ "Source: unsplash.com/@jeswinthomas")

6. RSA algorithm needs three elements to encrypt a **message** $$m$$ to its **cipher text** $$c$$ and decrypt it back to $$m$$: 
- A public modulus, $$n$$
- A public encryption key, $$e$$ 
- A private decryption key, $$d$$

7. With these elements,
  - $$m$$ is encrypted to $$c$$ with function $$m^e \bmod n$$.
  - $$c$$ is decrypted back to $$m$$ with function $$c^e \bmod n$$
  - You can see the two functions combined gives us: $$(m^e \bmod n)^ d \bmod n = m$$ 

8. For example, if $$n$$ = $$33$$,  $$e$$ = $$7$$,   $$d$$ = $$3$$ and  $$m$$ = $$31$$. <br> $$m$$ is encrypted to $$c$$ with : $$ m^e \bmod n \\ \equiv {31^7} \bmod {33} \\ \equiv remainder \ of \ {31^7}/{33} \\ = 4$$

9. $$c$$ is decrypted back to $$m$$ with : $$ c^d \bmod n \\ \equiv {4^3} \bmod {33} \\ \equiv remainder \ of \ {4^3} / {33} \\ = 31$$
![Unsplash](https://source.unsplash.com/_U-x3_FYxfI/800x450/ "Source: unsplash.com/@punttim")

10. The algorithm holds true only in the bounds of 4 constraints.
  - $$n$$ must be $$ p \times q$$ where 
    > both $$p$$ and $$q$$ are prime numbers.
  - $$e$$ must such that it is
    > a *co-prime* of $$ (p-1) \times (q-1)$$ and $$>1$$.
  - $$d$$ must be such that 
    > $$ ( d \times e) \bmod ((p-1) \times (q-1)) \equiv 1 $$. 
  - $$m$$ must be less than $$n$$

11. These constraints hold for $$n$$ = $$33$$,  $$e$$ = $$7$$,   $$d$$ = $$3$$ and $$m = 31$$
  - $$n$$ is $$3 \times 11 $$
    > both $$3$$ and $$11$$ are prime numbers;
  - $$7$$ is a co-prime of $$20$$. 
    > $$20$$ is $$(p-1) \times (q-1)$$; 
  - $$21 \bmod 20$$ is $$1$$
    > $$21$$ is $$( d \times e) \equiv (3 \times 7)$$ <br>
    and $$20$$ is $$(p-1) \times (q-1)$$; 
  - $$m \equiv 31$$ is less than $$n \equiv 33$$