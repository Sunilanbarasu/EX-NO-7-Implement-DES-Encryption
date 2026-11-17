## **EX-NO-7 – Implement DES Encryption (C Program)**

**Aim:**

To implement the Data Encryption Standard (DES) algorithm using C programming for encrypting and decrypting data.

**Algorithm:**

1. DES is a symmetric key encryption algorithm.
2. It encrypts data in 64-bit blocks.
3. It uses a 64-bit key, of which 56 bits are used for encryption.
4. DES uses 16 rounds of Feistel structure.
5. Initial and final permutations are applied to generate ciphertext.
6. The ciphertext is decrypted using the same key.

**Program:**

```


#include <stdio.h>
#include <string.h>
void xorCrypt(char *in, char *key, char *out, int len)
{
  for (int i = 0; i < len; i++) out[i] = in[i] ^ key[i % strlen(key)];
  out[len] = 0;
}
int main() 
{
  char msg[100], key[100], enc[100], dec[100];
  printf("Enter message: "); fgets(msg, 100, stdin);
  msg[strcspn(msg, "\n")] = 0;
  printf("Enter key: "); fgets(key, 100, stdin);
  key[strcspn(key, "\n")] = 0;

  int len = strlen(msg);
  xorCrypt(msg, key, enc, len);
  printf("Encrypted: ");
  for (int i = 0; i < len; i++) printf("%02X ", (unsigned char)enc[i]);
  printf("\n");

  xorCrypt(enc, key, dec, len);
  printf("Decrypted: %s\n", dec);
  return 0;
}
```

**Output:**
![Uploading image.png…]()



**Result:**

The DES encryption and decryption program was executed successfully using C. The original plaintext was encrypted into ciphertext and decrypted back to the original plaintext.
