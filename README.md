<h3>ABOUT</h3>
PuTTYwincrypt is a patched version of PuTTY. PuTTYwincrypt enables the user to use any private key related to a certificate in the user personal certificate store to perform public key ssh authentication.

As long as there exists a certificate in the user personal certificate store that has a corresponding private key it should be possible to use the key to perform a public key ssh authentication.

This enables the use of smart cards in PuTTY and Pageant, as long as the smart card is supported by Windows.

PuTTY is found at: http://www.chiark.greenend.org.uk/~sgtatham/putty/

PuTTYwincrypt is found at: https://sourceforge.net/projects/puttywincrypt/

<h3>REQUIREMENTS</h3>
Windows XP or later. No other requirements.

<h3>USAGE - PuTTY</h3>
To use a key backed by Windows please specify this key in the "Private key file for authentication:" text box found in PuTTYwincrypt. This text box is found at Connection > SSH > Auth.

To select ANY key backed by Windows type (in the text box):

`cert://*`

In order to select a specific key by certificate thumbprint type:

`cert://thumbprint=<thumbprint_in_hex>`

In order to select a specific key by part of certificate common name type:

`cert://cn=<part_of_common_name_to_search_for>`

Searching for all certificates may take a long time and "hang" PuTTYwincrypt if there exist many certificates on slow smart cards in the certificate store.

<h3>USAGE - Pageant</h3>
Start Pageant by clicking on it. To add a key stored in Windows crypto API right click on Pageant in the systray and select "Add Certificate" in the menu. Whenever the private key is accessed the user may or may not be prompted by Windows to enter a passphrase/PIN depending on whether the key is protected or not.

Please note that it is not possible to add keys backed by Windows from the Pageant main GUI at the moment, only from the systray menu.

To export the public key in the ssh authorized_keys format load the key into Pageant and double click on it. The public key will be copied into the clipboard in the authorized_keys format.

The latest version of Pageant can be downloaded from [here](https://sourceforge.net/projects/puttywincrypt/files/latest/download).

<h3>BACKGROUND</h3>
The PuTTYwincrypt patch was written in order to ease the use of public key ssh authentication with smart cards. The easiest way to go with this seemed to be using the windows crypto api for this. This enabled PuTTYwincrypt to function without bothering with any direct card drivers and pkcs#11 implementations.
