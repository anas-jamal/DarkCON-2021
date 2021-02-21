# Scattered Pieces

```desc
Pieces are scattered can you collect them and get the flag?
Note: There's a fake flag inside the challenge
```

[Challenge file](https://mega.nz/file/WslhUApJ#RtygpM5wd5aghceTS108hT1F7kkTwLX860mBuUYZkcA)

## Solution

open the file in ftkimager after surfing through it you will get pcap file in `wolf > favourites > sup fav`.

first piece collected now let's find other pieces we will get `sslkeylogfile` in `Default > Desktop`.

ok now we can decrypt it the `https` traffic and we will get `mega.nz` link now we need decryption key.

That means we need to find one more piece let's search the files again and we will get in `wolf > documents`.

After getting the full mega link we will get zip file again correct it using `hexeditor`.

I accept that i forgot to mention anything about cracking the zip sorry about that :( .
use john for cracking the password.

`zip pass: lovehurts`

### Flag

darkCON{Decrypting_packets_1s_c00L}

