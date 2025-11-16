# EX-NO-11-ELLIPTIC-CURVE-CRYPTOGRAPHY-ECC

## Aim:
To Implement ELLIPTIC CURVE CRYPTOGRAPHY(ECC)


## ALGORITHM:

1. Elliptic Curve Cryptography (ECC) is a public-key cryptography technique based on the algebraic structure of elliptic curves over finite fields.

2. Initialization:
   - Select an elliptic curve equation \( y^2 = x^3 + ax + b \) with parameters \( a \) and \( b \), along with a large prime \( p \) (defining the finite field).
   - Choose a base point \( G \) on the curve, which will be used for generating public keys.

3. Key Generation:
   - Each party selects a private key \( d \) (a random integer).
   - Calculate the public key as \( Q = d \times G \) (using elliptic curve point multiplication).

4. Encryption and Decryption:
   - Encryption: The sender uses the recipient’s public key and the base point \( G \) to encode the message.
   - Decryption: The recipient uses their private key to decode the message and retrieve the original plaintext.

5. Security: ECC’s security relies on the Elliptic Curve Discrete Logarithm Problem (ECDLP), making it highly secure with shorter key lengths compared to traditional methods like RSA.

## Program:
```
# Minimal ECC Key Exchange in Python
from tinyec import registry
import secrets

# Choose curve
curve = registry.get_curve('secp192r1')

# Private keys (random integers)
alicePrivKey = secrets.randbelow(curve.field.n)
bobPrivKey = secrets.randbelow(curve.field.n)

# Public keys = privKey * G
alicePubKey = alicePrivKey * curve.g
bobPubKey = bobPrivKey * curve.g

# Shared secrets
aliceShared = alicePrivKey * bobPubKey
bobShared = bobPrivKey * alicePubKey

print("--- ECC Key Exchange ---")
print("Curve:", curve.name)
print("Alice private key:", alicePrivKey)
print("Bob private key:", bobPrivKey)
print("Alice public key: (", alicePubKey.x, ",", alicePubKey.y, ")")
print("Bob public key:   (", bobPubKey.x, ",", bobPubKey.y, ")")
print("Shared secret (Alice):", aliceShared.x)
print("Shared secret (Bob):  ", bobShared.x)

```


## Output:
<img width="626" height="284" alt="image" src="https://github.com/user-attachments/assets/ccc8f610-a493-4e67-9a53-4708138cb680" />


## Result:
The program is executed successfully

