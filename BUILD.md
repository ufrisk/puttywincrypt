Summary
=======
This readme contains information about how to build PuTTYwincrypt from source. The PuTTY version used in the documentation is 0.70. Please substitute with your PuTTY version if using another version of the patch file.

Requirements
============

The putty_wincrypt_070_git.patch is found in the root of this repository.

The PuTTY 0.70 source checked out from git at: ` git clone --branch 0.70 git://git.tartarus.org/simon/putty.git `

Microsoft Visual C compiler (visual studio)

(Cygwin, BCC5.5 or LCC may also work)

Details
=======

#### 1: Apply the patch

Apply the putty_wincrypt_070_git.patch to the source code.

` patch -p1 -i putty_wincrypt_070_git.patch `

Ignore any patch warnings about offsets.

#### 2: Generate the Makefiles

` ./mkfiles.pl `

#### 3: Set up the build environment (Visual C only)

This can be done by starting the "Visual Studio Command Prompt" in the Visual Studio tools folder in the start menu.

#### 4: Build

In the PuTTY source directory move into the windows sub-directory and compile PuTTY with the wincrypt patch. This is done by executing the following command:

Visual C: ` nmake -f Makefile.vc `

Cygwin: ` make -f Makefile.cyg `

BCC ` make -f Makefile.bcc `

LCC: ` make -f Makefile.lcc `

#### 5: Use

If the build was successful it should now be possible to use the newly compiled versions of PuTTY and Pageant. The executables will be found in the windows sub-directory of the PuTTY source.

#### Notes about the build environment

It is possible to build the wincrypt patched version of PuTTY with Microsoft Visual C. Cygwin / BCC / LCC may also work but aren't tested for each patch. The recommended build environment is Visual C.
