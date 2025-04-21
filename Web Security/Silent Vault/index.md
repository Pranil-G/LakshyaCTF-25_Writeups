# Secret Vault

## Description

An internal system recently flagged unusual activity: a standard user was able to perform actions reserved for administrators. No credentials were leaked, and logs show no sign of direct tampering.

Investigate the incident and replicate the behavior to uncover the flag.

## Solve

The challenge began with a web login interface. To test the website, I tried a common set of default credentials:
`admin:admin`
This worked and returned a JWT (JSON Web Token) — hinting that the application used token-based authentication.

I copied the token into jwt.io to decode its structure. The payload included:
`"sub": "admin"`
This suggested the token was identifying the user as an admin. Since JWTs consist of a header, payload, and signature, I focused next on how the signature might be verified.

I used the JWT in a request to the /admin route with the following header:
`Authorization: Bearer <JWT_TOKEN>`

Respnose:
`{"message":"Welcome, admin! You have access to the admin panel."}`

Since `"sub": "admin"` gave access to admin endpoint I deduced that `"sub": "flag"` will give access to /flag endpoint.
JWT requires a signing key I guess common signing keys from web and the correct one was - `supersecretkey`

I used the forged token in a request to the /flag endpoint:
`{"flag":"TGFrc2h5YUNURnt1X3BFckZvTWVEX2pXdF9mT3JHZVJ5fQ=="}`

The flag was Base64-encoded. Decoding it revealed the final flag

Flag - `LakshyaCTF{u_pErFoMeD_jWt_fOrGeRy}`
