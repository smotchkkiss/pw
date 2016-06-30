# pw
Tiny command line password manager script for linux

Generate, read and save passwords to and from gpg encrypted files, one password per file

## Dependencies
gpg, xclip and pwgen

## Installation
Put the pw file into $HOME/bin/ or /usr/local/bin/ or something. Change the gpg_recipient variable at the top of the file to a PGP ID you’d like to encrypt your passwords for

## Usage
```
usage: pw [option] file

options:

--new|-n            generate a new random password,
                    encrypt it, save it to file and
                    copy it to the clipboard

--set|-s <password> encrypt the given password,
                    save it to file and copy it
                    to the clipboard

if no options are specified: read the password
from file, decrypt, copy to the clipboard
```

I keep my passwords in a folder called "passwords" in my home directory.

Whenever a website asks me to create a new password, I hit `Ctrl+Alt+T` to fire up a new terminal and type `pw -n pas<TAB>/example.com` and close the terminal with `Ctrl+D`. Back in the website, I then just paste the new password from the clipboard as often as needed.

The command used for password generation is `pwgen -s 32`. 32-character random passwords are long enough for my paranoia and the length is accepted on most sites.

If I need a password with particular properties or want to save a password I already have without changing it now, I use `pw -s <PASSWORD> passwords/example.com` or, for example, `pw -s $(pwgen -s0 12)`passwords/example.com` for a 12-character password without digits.

Then when the password is asked, I just fire up a new terminal again, type `pw pas<TAB>/$name_of_webs<TAB>`, type my PGP key’s passphrase, hit enter, close the terminal and paste the password wherever needed.

pw doesn’t sync passwords to the cloud or your smartphone :(

