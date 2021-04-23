# Image Steganography
Image steganography refers to hiding information i.e. text or images files in another image file. This hidden information can be retrieved only through proper decoding technique.

The method commonly used is the LSB method which involves changing the least significant bits(LSB) of the cover image pixels with the least significant bits(LSB) of the secret message/image.
We have used more secure methods of image steganography:
* [Discrete Cosine Transform(DCT)](DCT)
* [Discrete Wavelet Transform(DWT)](DWT)

## Discrete Cosine Transform(DCT) method of Image Steganography
We have used Discrete Cosine Transform(DCT) method for hiding test message in a cover image.

#### Algorithm to embed text message:-
Step 1: Read cover image and split into its RGB(red, green, blue) channels(the original DCT works on the cover image itself but in order to enhance security we have split it into RGB and then performed the operations).
Step 2: Read secret message and convert it in binary.
Step 3: The blue channel image is broken into 8×8 block of pixels(blue channel is an arbitary channel choosen, you may choose any).
Step 4: Subtract 128 from each pixel in a block.
Step 5: Apply DCT to each block.
Step 6: Compress each block using quantization matrix.
Step 7: Extract the first pixel of each block
Step 8: Find the LSB of the first pixel
Step 7: Replace each LSB with bit of secret message.
Step 8: Expand each block using quantization matrix.
Step 8: Apply inverse DCT to each block.
Step 9: Add 128 from each pixel in a block.
Step 10: Merge the blocks to form an image
Step 11: Write stego image.
Step 12: The stego image is then send to the other person

#### Algorithm to retrieve text message:-
Step 1: Read stego image.
Step 2: Stego image is split into its RGB(red, green, blue) channels
Step 3: The blue channel is broken into 8×8 block of pixels.
Step 4: Subtract 128 from each block of pixels.
Step 5: Apply DCT to each block.
Step 6: Compress each block through quantization table.
Step 7: Find the LSB of the first pixel fo each block and store in a list
Step 6: Merge the LSBs in group of 8 to find the binary code hidden
Step 7: Convert each 8 bit into character.

