# DNA Encryption Tool

This Python script is a simple DNA encryption tool that encodes and decodes plaintext messages using DNA sequences. The tool is based on the idea of representing binary data as a DNA sequence.

## How It Works

The tool uses the following steps to encode and decode messages:

1. Define the DNA encoding method: Each of the four nucleotides in DNA (adenine, cytosine, guanine, and thymine) is assigned a unique binary code.

2. Encode the plaintext message as a DNA sequence: The plaintext message is first converted to binary using the ASCII code. Then, the binary string is divided into pairs of two bits, and each pair is mapped to the corresponding nucleotide code.

3. Decode the DNA sequence back to a plaintext message: The DNA sequence is divided into pairs of two nucleotides, and each pair is mapped back to its corresponding binary code. Then, the binary string is converted back to plaintext using the ASCII code.

## Usage

To use the DNA encryption tool, simply run the Python script using a command-line interface or an IDE. The script defines two functions: `encode` and `decode`. 

The `encode` function takes a plaintext message as input and returns the corresponding DNA sequence as output. The `decode` function takes a DNA sequence as input and returns the corresponding plaintext message as output.

Here is an example usage of the script:

```python
import numpy as np
import pandas as pd

# Define the DNA encoding method
ENCODING_METHOD = {
   'A': '00',
   'C': '01',
   'G': '10',
   'T': '11'
}

# Define the function to encode the plaintext message as a DNA sequence
def encode(message):
   binary_message = ''.join([format(ord(char), '08b') for char in message])
   dna_sequence = ''
   for i in range(0, len(binary_message), 2):
       dna_sequence += ENCODING_METHOD[binary_message[i:i+2]]
   return dna_sequence

# Define the function to decode the DNA sequence back to a plaintext message
def decode(dna_sequence):
   binary_message = ''
   for i in range(0, len(dna_sequence), 2):
       for base, code in ENCODING_METHOD.items():
           if dna_sequence[i:i+2] == code:
               binary_message += base
   message = ''.join([chr(int(binary_message[i:i+8], 2)) for i in range(0, len(binary_message), 8)])
   return message

# Test the functions with a sample message
message = "Hello, world!"
dna_sequence = encode(message)
decoded_message = decode(dna_sequence)
print("Original message: ", message)
print("Encoded DNA sequence: ", dna_sequence)
print("Decoded message: ", decoded_message)
```

When the script is run, it will print the original message, the encoded DNA sequence, and the decoded message.