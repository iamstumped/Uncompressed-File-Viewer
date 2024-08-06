# Uncompressed-File-Viewer
Some older games may use unencoded images to allow support on older GPUs that don't support compression (Such as the Matrox G400/G450/G550). These files may have little to no metadata, causing most image software to display a header error. 

## How It Works
This program was intended for the assets of [Tenerezza](https://www.myabandonware.com/game/tenerezza-gun) and has only been tested here. It is unknown if this will work anywhere else. 
The uncompressed files use groups of four bytes, each corresponding to the blue, green, red, and alpha values for a given pixel.

### Using the Program
1. Select the file. Any file can be selected, but most will not display very well.\
  ![image](https://github.com/user-attachments/assets/9030c362-7d38-4f09-ba73-6ccc85b6b2d4)
2. Adjust the offset. If the file has header data, use this to skip it. The hex values skipped this way will be shown below. You can save this step for later if you choose.\
  ![image](https://github.com/user-attachments/assets/e4486fa4-1264-494d-a37b-744a55c3d7ca)
3. Identify if the file has alpha (transparency) data. If it does, choose an option with `A`.\
  ![image](https://github.com/user-attachments/assets/b997656b-69b3-47fd-bc40-a1ff06ed3c13)
   - It's easiest to use a hex editor. If every four bytes are `FF`, it likely has transparency.
   - Don't worry about RGB vs BGR for now. 
4. Set the width. It will likely be a simple value, like an exponent of two.\
  ![image](https://github.com/user-attachments/assets/5a9d1f0e-ee25-4b29-a527-2428f7aedfe9)
5. Click `View` and look at the result to the right:
    - If the image is cleanly doubled, try dividing the width by two.
    - If it appears interlaced, try multiplying the width by two.
    - If it appears as diagonal lines, the image is not a multiple of that width.
    - If you can see shapes in black and white, try switching to a pixel format to one with or without alpha.
    - If the colours appear inverted, try switching between RGB and BGR formats.
    - If the image appears heavily tinted, try adjusting the offset, or skip for now.
6. Once the result looks right, look at the number next to the `View` button:\
  ![image](https://github.com/user-attachments/assets/9c72bdc6-95f5-4cff-8401-4cfd6380dbff)
    - If it is zero, your result perfectly fits the input.
    - If it is negative, the result is likely cut off. Try increasing the height.
    - If it is positive, it likely looks fine. Reducing the height will affect the saved image, as well as help with the offset.
    - If it is somewhat close to zero, try setting your offset to that number (if negative, make it positive)
7. You can save the image as a PNG. Use `File > Save Image`.
    - **The program currently does not alert you when overwriting a file at this point. Be careful!**

## Known Issues
**These may or may not get fixed:** 
- Saving images does not alert the user when overwriting a previously existing file.
- Interface will resize upon clicking `View`
