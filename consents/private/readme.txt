The encrypted (.gpg) files in here contain proof of agreement to CC0 by contributors who wish to remain anonymous.
They can be decrypted knowing their github username (at the time they contributed / of writing this).

There is one "private*.png.gpg" file per anonymous contributor.

The decryption procedure uses argon2 (as a bruteforce prevention measure) and gpg (for symmetric encryption).


To decrypt the test file:

$ echo 'test' | argon2 my_salt_for_oot_cc0_privacy_encryption_key -v 13 -t 100 -m 20 -p 64 -l 64
Type:           Argon2i
Iterations:     100
Memory:         1048576 KiB
Parallelism:    64
Hash:           281208d1f43ed1cc590357488150242054d4f48b3573ad308ff45974c8c3cf1125a93a90ede577a5f71a38741b6133e4b4aac69f970c519cbd6b5b6db702f328
Encoded:        $argon2i$v=19$m=1048576,t=100,p=64$bXlfc2FsdF9mb3Jfb290X2NjMF9wcml2YWN5X2VuY3J5cHRpb25fa2V5$KBII0fQ+0cxZA1dIgVAkIFTU9Is1c60wj/RZdMjDzxElqTqQ7eV3pfcaOHQbYTPktKrGn5cMUZy9a1tttwLzKA
74.412 seconds
Verification ok

-> Use the hash as the passphrase: 281208d1f43ed1cc590357488150242054d4f48b3573ad308ff45974c8c3cf1125a93a90ede577a5f71a38741b6133e4b4aac69f970c519cbd6b5b6db702f328

(
Encrypt:
$ gpg --symmetric --no-symkey-cache decrypt_test.txt
)

Decrypt:
$ gpg --decrypt --no-symkey-cache decrypt_test.txt.gpg


To decrypt the encrypted private files:

Same as with the test file, but instead of hashing "test" with argon2, hash the github username of the contributor.
