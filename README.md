### Introduction

This app was written to be part of the [Retro Newton YouTube Channel](https://www.youtube.com/channel/UC-h0pKj9rmhgRX3KomvSCow) series on Netwon Development.

It is a One Time Password (OTP) Token for Newton OS.  It is, for example, compatible with Google Authenticator tokens.

You need to be on NewtonOS Patch 711000 (to fix the 2010 date issue).  Make sure your timezone is properly set.

**Warning** the "Secret" is stored in the Application Preferences Soup in clear text.  This isn't the most secure method.

### How to Handle Resource Forks in this repository

This is stolen from the [Dash Board README](https://github.com/masonmark/Dash-Board-for-Newton-OS/blob/master/README.md).   This is the process by which you can split the resource forks to standard files for use with git, and then put them back to use with Mac Classic.

1. Clone the repo to your Mac OS X 10.x System
2. In the terminal, cd into the top level folder of the repo
3. To hack on the source code, you must re-assemble all the files, which to be used with git have been split into separate data and resource forks (AppleDouble format). To do so, try this command:

        /System/Library/CoreServices/FixupResourceForks .

  and do not omit that trailing . or who knows what the hell might happen.
4. Use the SheepShaver emulator to boot Mac OS 9, and configure it to mount the OS X folder containing the repo as a disk. *Don't copy the repo to your SheepShaver VM's native storage, because it seems to lose the invisible git dirs when copying it back, thereby corrupting the repo.*
5. Hack, hack, hack, build.
6. Once you have completed a change you want to commit to the git repo, quit out of Newton Toolkit, and then go back to the OS X side of things. Again cd into the repo root dir, and run this command:

        SplitForks .

  This will again split the resource forks off of all files who have one, and store them as a separate invisible file (AppleDouble format). This convoluted dance is necessary because git absolutely doesn't work with resource forks and Newton Toolkit absolutely doesn't work without them.
7. Commit your changes, then treat yourself to a frosty beverage.