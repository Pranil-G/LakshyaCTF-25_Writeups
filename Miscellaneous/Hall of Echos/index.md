# Hall of Echos

## Description

`In the hall of echoes, eight pillars stand tall, The first whispers “16” as the ancient call. Next, “98” glimmers on the second in line, Then “89” follows, a secret sign. “15” the fourth, then “35” in the lore, “75” echoes next from the old stone door. The last two, “17” and “17”, complete the thrall, Combine them to yield a product, a product of prime. This open testament, known far and wide, Guides many seekers on the cryptic ride.`

`High above in a celestial dance, Seven stars conceal a code at a glance. Begin with “62”, then “78” appears bright, A “04” then “06” in the shimmering night. Follow with “667”, then “94” in sight, Ending with “81” – the exponent of light. Together these values openly impart A dual key’s face that many may chart.`

`Yet whispers linger of an unseen art— A secret mirror that sets the truth apart. For those who dare invert what’s on display, A hidden key awaits to show the way. Unlock that private cipher, subtle yet prime, And inscribe its secret as your flag in time`

The challenge gives two large numbers hidden in poetic form:

`1698891535751717 (interpreted as n)`
`627804066679481 (interpreted as e)`

The first number is described as a product of two primes, hinting at RSA encryption.

Using an online prime factorization tool, we found:

    p = 23285137

    q = 72960341

These are both prime numbers, confirming RSA was the intended encryption scheme.

## Python Script
```
from sympy import mod_inverse

p = 23285137
q = 72960341
e = 627804066679481
phi = (p - 1) * (q - 1)
d = mod_inverse(e, phi)
print(d)
```

Flag - `LakshyaCTF{1216997203097801}`
