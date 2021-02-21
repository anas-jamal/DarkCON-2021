# Mr.Wolf Darkest Secret
![forense](https://img.shields.io/badge/analitycs-forensic-green) ![play](https://img.shields.io/badge/Play-CTF-red)

```desc
Mr.Wolf is hiding something from us .Can you find Mr.Wolf's Deepest Secret and he was trying to access some other system and we need to gather more information about Mr.Wolf activities
```

[Challenge file](https://mega.nz/file/H092FITb#H5-83lNbzZQbrZsEJCCWwb1RMfJmT0D8Lp-cuSi0Xbo)

## Solution

open file in ftk.
Now wolf was trying to access some system note that there's a rabbit hole i.e. `team viewer`. Wolf was accessing the another using rdp.

I intentionally didn't add lots of files straight forward path to rdp if you didn't fall into rabbit hole.

So In windows cache of rdp is stored.

`Path: %LOCALAPPDATA%\Microsoft\Terminal Server Client\Cache`

Now extract the cache and we can `BMC-Tools` for analyzing the cache.

[BMC-Tools](https://github.com/ANSSI-FR/bmc-tools)

`./bmc-tools.py -s ../Cache0000.bin -d ../data`

Now we have to analyze the result we have lots of images but we can see there's some pieces of `defuse` now we just merge them and get the full link.

`https://defuse.ca/b/OphiXIBtXMpo5j1l9DfXQn`

ok but it asks for password. wait did you checked recycle bin ? yes the password is present in `recycle bin`.

`Password: youwillknowwhenyouhavetouseit`

ok we got `base64` let's decode it we will get a `zip` file and correct the headers first.

but now there's no password but there's a file inside the zip.

if we do simple google search about the other file we can get it [Hacker, Heroes of the computer REvolution](http://www.gutenberg.org/ebooks/729) .

Let's Download it

`wget http://www.gutenberg.org/cache/epub/729/pg729.txt`

rename it to same file which is present inside the zip.

So we know some part of the zip.

Now if we do bit of googling we can figure out it is `known plain text attack`.

Now download [pkcrack](https://github.com/keyunluo/pkcrack)

Final Command for craking the zip file:

```crack
pkcrack -C crack.zip -c Hackers,\ Heroes\ of\ the\ Computer\ Revolution.\ Chapters\ 1\ and\ 2\ by\ Steven\ Levy.txt -P pt.zip -p Hackers,\ Heroes\ of\ the\ Computer\ Revolution.\ Chapters\ 1\ and\ 2\ by\ Steven\ Levy.txt -d cracked.zip -a
```

and finallly we will get our flag.

### Flag

`darkCON{l00k_moMmy_1_f0und_th3_s3cret_4nd_Cracked_1t}`
