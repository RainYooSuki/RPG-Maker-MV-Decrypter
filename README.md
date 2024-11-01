# Petschko's RPG-Maker-MV & MZ File-Decrypter

## What's that?

This Project is used to Decrypt (and Re-Encrypt) RPG-Maker-MV-Resource-Files (MZ-Files as well) and that are encrypted with the Build-In-Encryption of the RPG-Maker.

This Project is mostly used for Single-File decryption (But it is able to handle multiple files). >.< Please try out the [Java-Decrypter](https://github.com/Petschko/Java-RPG-Maker-MV-Decrypter) if you want decrypt huge amounts of Files (or more Projects)

### Motivation behind this
As Art-Creator for the RPG-Maker by myself, it is sometimes hard to figure out, if somebody is using Resources from you (and may violate the licence like giving no credit or using a Non-Commercial-Resource in a Commercial Game for example).

I don't have time to play through all the games so i just quick look at the files but its only possible if the files are not encrypted...

Sad for me, more People use the build in Encryption from the RPG-Maker-MV so that's why I wrote this script - to get a quick look at the files without playing the whole game =) May some other artists will find this useful too.

### Legal-Notification
You are **not allowed** to use the Decrypted Files (**if its not allowed by the origin File-Licence**).
Please don't steal and reuse stuff that's not the idea of this Script!
You can save them for Private-Use only. If the origin Licence allow use you can use them of course but please follow the licences!

**If that's your Project** and you simply lost your Origin-Files, **you have the same rights**, to do stuff with them, **as before** =)

## Requirements
- Web-Browser with HTML5 Support

## Installation

This is very easy:

- Download/Clone the Project OR direct use [it on my site](https://petschko.org/tools/mv_decrypter/)
- Extract/Put it where ever you want
- Done :)

## How to use?

### If you downloaded this Script on your Computer (Pre Step)
- You have to open the "**index.html**" file with you Browser like:
  - Use right click and open with... _(Then select your Favorite Browser)_
  - Use double click to open the file. Many Browsers set them as default applications for html files

### Use this Script now

#### Image "Decryption" without the Key
You can restore all image files without having  the decryption Key. If you want to get the Audio, you need to do the [decryption](#decryption)
1. Go to the Tab **Restore-Images (No-Key)**
2. Select any encrypted PNG-Image-File(s) (Extensions: `.rpgmvp` or `.png_`)
3. Click the Button **Restore Original Files**
4. Download or view the Files on the right side. You can open them and/or save them (or just view/listen)

#### Decryption
You want to decrypt Audio or image Files? That is how it works:
1. Check if the Files have one of the File-Extensions:
    - `.rpgmvp`, `.png_` (PNG-Files)
    - `.rpgmvm`, `.m4a_` (m4a-Files)
    - `.rpgmvo`, `.ogg_` (ogg-Files)
2. Get the Encryption-Key (This step isn't needed for Images - Look at `Image "Decryption" without the Key`)
    - Select with the first File-Picker the "**System.json**"-File OR any **.rpgmvp**/**.png_** File from that Project
      - The File is located in `%PROJECT_DIRECTORY%/www/data/System(.json)` for RPG-Maker MV
      - The File is located in `%PROJECT_DIRECTORY%/data/System(.json)` for RPG-Maker MZ
      - You can also use an Encrypted Image-File from the Project (`.rpgmvp` / `.png_`) to detect the Key
    - Click on the Detect-Button - If it finds the Key, it will automatically insert it for you within the next Input-Field
    - You can also manually put the encryption-Key in the Text-Field if you know it.
3. Select the Encrypted Audio/Image-Files to decrypt (You can select multiple here)
4. Click on the Decrypt-Button
    - **IF** you get an invalid Header Warning, turn off the Header Check. Just select "No" under `Verify Fake-Header?` and try again!
5. The Decrypted-File(s) are shown in a File-List. You can open them and/or save them (or just view/listen)
    - Some Browser-Plugins like [UBlockOrigin](https://github.com/gorhill/uBlock) may block previewing the File. Disable it or explicit say `Open in new Tab`

#### Encryption
You want turn back an Image into the Game _(If you have translated text or fixed something on an Image)_?

Here you go:
1. You need to check if you have one of these File-Types to turn back into the Game:
    - PNG-File (`.png`) - _Image-Format **make sure that's PNG** not JPG or something different_
    - m4a-File (`.m4a`) - _Sound Format_
    - ogg-File (`.ogg`) - _Sound and/or Video Format_
2. If you have the Files in these Format you can go on, else turn them into the correct Format. (You should know how or [how to Google](http://www.giyf.com/))
3. Get the Encryption-Key (This step isn't needed for Images - Look at `Image "Decryption" without the Key`)
    - Select with the first File-Picker the "**System.json**"-File OR any **.rpgmvp**/**.png_** File from that Project
        - The File is located in `%PROJECT_DIRECTORY%/www/data/System(.json)` for RPG-Maker MV
        - The File is located in `%PROJECT_DIRECTORY%/data/System(.json)` for RPG-Maker MZ
        - You can also use an Encrypted Image-File from the Project (`.rpgmvp` / `.png_`) to detect the Key
    - Click on the Detect-Button - If it finds the Key, it will automatically insert it for you within the next Input-Field
    - You can also manually put the encryption-Key in the Text-Field if you know it.
4. Make sure that `Verify Fake-Header?` is enabled (on **YES**). If not select it.
    - This checks if the Game can read this File
5. Select the File(s) you want Encrypt
6. Click on the (Re)-Encrypt-Button (Of the RPG-Maker which is used)
    - **IF** you get an Error please check if you did all steps right before! Also check if the Header-Values are on default:
      - Click on `Header-Values (Show)`
      - Click on `Reset Header-Values to default` and click `OK` in the Confirmation box
      - Try again
7. The (Re)-Encrypted-File(s) are shown in a File-List, next to or below _(on tiny screens)_ the De/Encrypt-Button. You can't open them _(because its encrypted)_ but you should save them
8. Overwrite the File in your Game _(Maybe make a backup of the game before doing that)_
9. Start the Game and check if the File has been displayed
    - **If the File is not displayed**: (This is very rare ~1/100 Games - Usually you get a Header-Error while you Decrypt Files from these Games them with the default Header-Values. That's a strong indicator that this Game has different Header-Values)
      - You have to set different Header-Values, for this you have to open this File: `%PROJECT_DIRECTORY%/www/js/rpg_core.js`
        - For RPG-Maker-MZ the File is here: `%PROJECT_DIRECTORY%/js/rpg_core.js`
      - There you find the Decrypter-Class, its an insane long File so use the Search function (Strg/Ctrl + F) and search for this String: `function Decrypter()`
      - There are Values sort below, like this:
      ````js
      Decrypter.hasEncryptedImages = false;
      Decrypter.hasEncryptedAudio = false;
      Decrypter._requestImgFile = [];
      Decrypter._headerlength = 16; // <-- Header-Length (In Bytes)
      Decrypter._xhrOk = 400;
      Decrypter._encryptionKey = "";
      Decrypter._ignoreList = [
          "img/system/Window.png"
      ];
      Decrypter.SIGNATURE = "5250474d56000000"; // <-- Header-Signature
      Decrypter.VER = "000301"; // <-- Header-Version
      Decrypter.REMAIN = "0000000000"; // <-- Header-Remain
      ````
      Make sure that you copy the values (which have similar names to the fields in the Header-Info Form - I showed you them in my example above)
      - Try to encrypt the File(s) again

## Credits

- [Petschko](https://gitlab.com/Petschko) _(Me xD)_ - For creating this Project
- [Stuk](https://github.com/Stuk) - For the ZIP-Library ([jszip @ Github](https://github.com/Stuk/jszip))
- [pieroxy](https://github.com/pieroxy) - For the LZ-String-Library ([lz-string @ Github](https://github.com/pieroxy/lz-string))
- [eligrey](https://github.com/eligrey) - For the FileSaver.js-Library ([FileSaver.js @ Github](https://github.com/eligrey/FileSaver.js))
- [Bootstrap](https://getbootstrap.com/docs/3.4/getting-started/) - For a bit more user-Friendly Interface
- **Anonymous** - For the tip with the No-Key-"decryption" for PNGs *(This user want to remain anonymous, but this belongs to them)*
- [r4sas](https://github.com/r4sas) - Helping with the Chrome "View-File" bug

## Contact

- E-Mail me if you have questions (no bug reporting please): peter@petschko.org
- Please report Bugs here on github.com use the "[Issue](https://github.com/Petschko/RPG-Maker-MV-Decrypter/issues)"-Section on this Project
