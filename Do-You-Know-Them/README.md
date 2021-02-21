# Do you know them ?
![forensic](https://img.shields.io/badge/analitycs-forensic-green) ![play](https://img.shields.io/badge/Play-CTF-red)

## Description

```desc
We need to few answers from you do you know them?
1. Recently accessced docs folder

2. Last keyword searched

3. Last link entered
Flag Format: darkCON{recently accessced docs folder_last keyword searched_last link entered}
```
[Challenge file](https://mega.nz/file/24txUIQa#iGlF8YNenpmhKfswJJm2C1uaFacACKm_-GCsI65k82M)

## Solution

For this challenge we got `E01` file you can easily analyze `E01` file using ftk imager.

Now the answers of those question lies inside `NTUSR.dat`

extract it and use [regripper](https://github.com/keydet89/RegRipper3.0) or any other tool of your choice.

load it up in `regripper` and extract the information. Now analyze the results.

1.Recently accessced docs folder.

For this you just have to search the term "RecentDocsFolder" and we will get `secluded`

2.Last keyword searched

Same here too just search the "lastKeyword"
and we will get `Anachronistic`

3.last link entered

Search "TypedURLs" and you will get 
`https://www.youtube.com/watch?v=Z1xs1BRBO7Q`

### Flag

`darkCON{secluded_Anachronistic_https://www.youtube.com/watch?v=Z1xs1BRBO7Q}`

watch the video xD
