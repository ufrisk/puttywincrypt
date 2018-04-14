PuTTYwincrypt Summary:
=======================
PuTTYwincrypt enables the user to use any private RSA key related to a certificate in the Windows user personal certificate store to perform public key ssh authentication. This includes private RSA keys related to certificates that are stored in software, smartcards or yubikeys.

For ease of use and flexibility PuTTYwincrypt Pageant is recommended over PuTTYwincrypt itself.

The original PuTTY is found at: http://www.chiark.greenend.org.uk/~sgtatham/putty/

Except for Windows certificate store integration PuTTYwincrypt is identical to PuTTY.

<img src="https://gist.githubusercontent.com/ufrisk/8dec5a98bcf875a6254f9e3aa35d12a0/raw/edad0efadd158d1226ebbf4d5587ed4b69f68242/putty_auth.png" height="250"/><img src="https://gist.githubusercontent.com/ufrisk/8dec5a98bcf875a6254f9e3aa35d12a0/raw/edad0efadd158d1226ebbf4d5587ed4b69f68242/putty_pageant_addcert.png" height="250"/>

Download:
=========
Download the binaries and the patch file stored in the root folder of this repository.

PageantWincrypt Usage:
======================
Start Pageant by clicking on it. To add a key stored in Windows crypto API right click on Pageant in the systray and select "Add Certificate" in the menu. Whenever the private key is accessed the user may or may not be prompted by Windows to enter a passphrase/PIN depending on whether the key is protected or not.

Please note that it is not possible to add keys backed by Windows from the Pageant main GUI at the moment, only from the systray menu.

To export the public key in the ssh authorized_keys format load the key into Pageant and double click on it. The public key will be copied into the clipboard in the authorized_keys format.

PuTTYwincrypt Usage:
====================
To use a key backed by Windows please specify this key in the "Private key file for authentication:" text box found in PuTTYwincrypt. This text box is found at Connection > SSH > Auth.

To select ANY key backed by Windows type (in the text box):

`cert://*`

In order to select a specific key by certificate thumbprint type:

`cert://thumbprint=<thumbprint_in_hex>`

In order to select a specific key by part of certificate common name type:

`cert://cn=<part_of_common_name_to_search_for>`

Searching for all certificates may take a long time and "hang" PuTTYwincrypt if there exist many certificates on slow smart cards in the certificate store.

Background:
===========
The PuTTYwincrypt patch was created in order to ease the use of public key RSA SSH authentication with smartcards. The easiest way to go with this seemed to be using the windows crypto api for this. This enabled PuTTYwincrypt to function without bothering with any direct card drivers and pkcs#11 implementations. PuTTYwincrypt also works for soft certificates and keys as well as with other non-smartcard hardware devices.

Building:
=========
Check out [build.md](BUILD.md) for build instructions.

Version History:
================

Earlier versions are found at [PuTTYwincrypt sourceforge](https://sourceforge.net/projects/puttywincrypt/).

v0.70
  - Main repository moved from Sourceforge to Github.
  - Patch updated to version 0.70 and recompiled binaries.
