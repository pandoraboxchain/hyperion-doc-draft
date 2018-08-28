# Key-evolving cryptography

## Keys structure

Each validator will use 2 key:
- Mastezr-money key
- List or related keys

## Public key chain generation

Public parent key → public child key

The function CKDpub((Kpar, cpar), i) → (Ki, ci) computes a child extended public key from the parent extended public key.
More - https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki

## Private parent key → private child key

The function CKDpriv((kpar, cpar), i) → (ki, ci) computes a child extended private key from the parent extended private key
More - https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki

## Removing key after sign block

1. Validator generate new child key
2. Validator save new child key
3. Validator remove prev key

## Updating chain of pub keys

1. User sign by Mastezr-money key new chain
2. User sign block using old key and new key (!)
3. User delete old key chain