# Random

## Threshold random

Threshold random has 3 phases: 
- Public Key phase, 
- Threshold random encrypted part phase, 
- Private key publishing phase

Roles:
- Zero knowlage provider (Subset of validator which will provide public keys and will reveal private keys)
- Random part provider (Subset of validator which will provide parts of random)

### Public Key

Each validator from Zero knowlage validator subset (from 1 to S_ZKP) provide 
1. public key (PubKey)
2. epoch hash 
3. sign hash(public key + epoch hash)

### Threshold random encrypted part

Each validator from Random part validator subset (from 1 to S_RPP):
1. generate random (32 byte data) 
2. Split random to Shamir's secrett (SSSMAX/2 + 1 of SSSMAX)
3. Encrypt each secret by deterministic randomly selected PubKey from Public Key phase

Each validator from Random part validator subset (from 1 to S_RPP) porivide:
1. List of encrypted secrets
2. epoch hash 
3. sign hash(merkle root of merkle tree (List of encrypted secrets) + epoch hash)

### Private key publishing

Each validator from Zero knowlage validator subset (from 1 to S_ZKP) provide 
1. Private key

### Current approach to sum of random

entropy = Random1 (32 byte data) xor random2 (32 byte data) xor random (32 byte data)

function of random data by i

random_i = hash(random_i-1)

### Current cryptography

Rigth now for proof of concept we just use shamir's secret sharing scheme:

https://github.com/blockstack/secret-sharing

For encryption:

https://pypi.org/project/pycrypto/

But in prod we prefer eleptic curve like

https://pypi.org/project/eciespy/

For hashing and we use rigth now sha256 but mb we can use 

https://blake2.net/

or 

https://en.wikipedia.org/wiki/SHA-3

## Commit reveal random

### Commit
### Reveal

## Immutability betwin round

### Random rules

## Rounds list

| Round number | Threshold random | Commit-reveal |
| --- | --- | --- | 
| 1 | Public Key | - |
| 2 | Public Key finalisation | Commit |
| 3 | Threshold random encrypted part | Commit finalisation |
| 4 | Threshold random encrypted finalisation | Reveal |
| 5 | Private key | Reveal finalisation |
| 6 | Private key finalisation | - |