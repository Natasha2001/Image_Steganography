# Image Steganography
Image steganography refers to hiding information i.e. text or images files in another image file. This hidden information can be retrieved only through proper decoding technique.

The method commonly used is the LSB method which involves changing the least significant bits(LSB) of the cover image pixels with the least significant bits(LSB) of the secret message/image.
We have used more secure methods of image steganography:
* [Discrete Cosine Transform(DCT)](DCT)
* [Discrete Wavelet Transform(DWT)](DWT)

## Discrete Cosine Transform(DCT) method of Image Steganography
We have used Discrete Cosine Transform(DCT) method for hiding test message in a cover image.

### Algorithm
##### Algorithm to embed text message:-
Step 1: Read cover image and split into its RGB(red, green, blue) channels(the original DCT works on the cover image itself but in order to enhance security we have split it into RGB and then performed the operations).</br>
Step 2: Read secret message and convert it in binary.</br>
Step 3: The blue channel image is broken into 8×8 block of pixels(blue channel is an arbitary channel choosen, you may choose any).</br>
Step 4: Subtract 128 from each pixel in a block.</br>
Step 5: Apply DCT to each block.</br>
Step 6: Compress each block using quantization matrix.</br>
Step 7: Extract the first pixel of each block.</br>
Step 8: Find the LSB of the first pixel.</br>
Step 7: Replace each LSB with bit of secret message.</br>
Step 8: Expand each block using quantization matrix.</br>
Step 8: Apply inverse DCT to each block.</br>
Step 9: Add 128 from each pixel in a block.</br>
Step 10: Merge the blocks to form an image.</br>
Step 11: Write stego image.</br>
Step 12: The stego image is then send to the other person.</br>

##### Algorithm to retrieve text message:-
Step 1: Read stego image.</br>
Step 2: Stego image is split into its RGB(red, green, blue) channels.</br>
Step 3: The blue channel is broken into 8×8 block of pixels.</br>
Step 4: Subtract 128 from each block of pixels.</br>
Step 5: Apply DCT to each block.</br>
Step 6: Compress each block through quantization table.</br>
Step 7: Find the LSB of the first pixel fo each block and store in a list.</br>
Step 8: Merge the LSBs in group of 8 to find the binary code hidden.</br>
Step 9: Convert each 8 bit into character.</br>

### Implementaion
##### To embed the message:-
* Change the directory to [Embed Message](https://github.com/Natasha2001/Image_Steganography/tree/main/DCT/Embed_Message)
* Save the cover image with the name cover_image
* Save the message to embed in message.txt file
* Run the notebook
* The image with the message hidden will be saved in the same directory with name "stego_img.png"

##### To retrieve the message:-
* Change the directory to [Retrieve Message](https://github.com/Natasha2001/Image_Steganography/tree/main/DCT/Retrieve_Message)
* Save the stego image generated in the [Retrieve Message Directory](https://github.com/Natasha2001/Image_Steganography/tree/main/DCT/Retrieve_Message) here
* Run the notebook
* The hidden message will be saved in the [secret_message file](https://github.com/Natasha2001/Image_Steganography/blob/main/DCT/Retrieve_Message/secret_message.txt)

## Discrete Wavelet Transform(DWT) method of Image Steganography
We have used Discrete Wavelet Transform(DWT) method for hiding a secret image in a cover image.

### Algorithm
##### Algorithm to embed the image:-
Step 1: Read cover image and split into its RGB(red, green, blue) channels(the original DWT works on the cover image itself but in order to enhance security we have split it into RGB and then performed the operations).</br>
Step 2: Read secret image and split into its RGB(red, green, blue) channels(the original DWT works on the secret image itself but in order to enhance security we have split it into RGB and then performed the operations).</br>
Step 3: Each channel of the cover image is then decomposed using DWT into 4 non-overlapping sub-bands.These are LL (approximation coefficients), LH (vertical details), HL (horizontal details) and HH(diagonal details). The division is done by employing Haar filters.
Step 4: Secret image is also disintegrated into four sub-bands (LL, LH, HL, HH). 
Step 5: Information contained in the LL sub-band of secret image is embedded into LL bands of cover image.
Step 6: Inverse transformation (IDWT) is performed to merge the sub-bands.
Step 7: The RGB channel images are then merged to form the stego image.

##### Algorithm to retrieve the image:-
Step 1: Read stego image and cover image.</br>
Step 2: Stego and cover image is split into its RGB(red, green, blue) channels.</br>
Step 3: Each channel of the cover image is then decomposed using DWT into 4 non-overlapping sub-bands.These are LL (approximation coefficients), LH (vertical details), HL (horizontal details) and HH(diagonal details). The division is done by employing Haar filters.
Step 4: Stego image is also disintegrated into four sub-bands (LL, LH, HL, HH). 
Step 5: Information contained in the LL sub-band of stego image is retrieved using the cover image and stego image.
Step 6: Inverse transformation (IDWT) is performed to merge the LL sub-band of stego image and LH,HL,HH sub-band of stego image.
Step 7: The RGB channel images are then merged to form the secret image.

### Implementaion
##### To embed the image:-
* Change the directory to [Embed Image](https://github.com/Natasha2001/Image_Steganography/tree/main/DWT/EmbedImage)
* Save the cover image with the name cover_img
* Save the secret image with the name secret_img
* Run the notebook
* The image with the image hidden will be saved in the same directory with name "img_with_secret.png"

##### To retrieve the image:-
* Change the directory to [Retrieve Image](https://github.com/Natasha2001/Image_Steganography/tree/main/DWT/RetrieveImage)
* Save the stego image and cover image generated in the [Embed  Directory](https://github.com/Natasha2001/Image_Steganography/tree/main/DWT/RetrieveImage)
* Run the notebook
* The secret will be saved in the same directory
