# Figuring Out The Past

```desc
After an accident Mr.wolf lost his memory and he is seeking help from you. He is not able to remember his past secret, can you help him figuring out the past mystery ? 
```
[Challenge File](https://mega.nz/file/j0kmwKRT#OfTPR6FfCR6uTlmUPTBaZhkcXoCFqB18RAoGwG5OLlQ)

## Solution

First Imageinfo

`python2 vol.py --plugins=volatility-plugins/ -f ~/Desktop/memdump.mem  imageinfo`

we will get the profile.

Now running prococess.

`python2 vol.py --plugins=volatility-plugins/ -f ~/Desktop/memdump.mem  --profile Win7SP1x64 pslist`

We can see Internet Explorer Running.

let's investigate IE History.

`python2 vol.py --plugins=volatility-plugins/ -f ~/Desktop/memdump.mem  --profile Win7SP1x64 iehistory`

Now from Internet History we will get 2 links .

1. defuse.ca : <https://defuse.ca/b/O3olbxzZ5VZzpEtSYArI21>

2. <https://mega.nz/file/ek0DzIiY>

We got some password from `defuse` let's keep it for future.

ok let's check files on Desktop

`python2 vol.py --plugins=volatility-plugins/ -f ~/Desktop/memdump.mem  --profile Win7SP1x64 filescan | grep Desktop`

we will get `mymistaked.txt` now let's dump it.

`python2 vol.py --plugins=volatility-plugins/ -f ~/Desktop/memdump.mem  --profile Win7SP1x64 dumpfiles -Q 0x000000000042c660 -D ~/Desktop`

Hmm it is saying file is deleted. But it exist in Master File Table or mft there's a plugin in volatility for `mft` that's `mftparser`.

`python2 vol.py --plugins=volatility-plugins/ -f ~/Desktop/memdump.mem  --profile Win7SP1x64 mftparser > ~/parsermft.txt`

Now the file is deleted so just search `Recycle` and we will get `Decryption key` for mega and we will corrupted zip. correct it using `hexeditor` and unzip it and we already got password for it.

### Flag

`darkCON{y0u_sCan_still_Read_Deleted_files}`
