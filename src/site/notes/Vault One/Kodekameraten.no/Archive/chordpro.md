---
{"dg-publish":true,"permalink":"/vault-one/kodekameraten-no/archive/chordpro/"}
---



Chordpro brukes når man vil ha nøyaktig plassering av akkorder i tekst-dokumentet, og ha mulighet til å transponere når som helst.

![Chordpro eksempel](data:image/md;base64,)

Chordro er bare vanlige *.txt*-filer, men man kan generere (blant annet) pdf ut av det.

## App-er?
Det er mange programmer som støtter å vise chordpro-notering. 
### OnSong
https://onsongapp.com/

## Installasjon

Se [https://www.chordpro.org](https://www.chordpro.org/chordpro/ChordPro-Installation.html) for hjelp til installasjon.

Dersom du har Mac kan du installere *Chordpro Cli*-programmet ved å skrive ``sudo /usr/bin/cpan chordpro`` i terminalen din.

## Generere sanger i alle tonearter

Dette er "scriptet" jeg kjører i terminalen for å generere sanger i alle tonearter:

```bash
# Gå inn i txt mappen med alle chordpro.txt-filene
cd TXT 
#For hver fil som er av type .txt, 
#generer pdf-er vha. chordpro-programmet
for f in *.txt; do
    chordpro $f    
    chordpro $f -x 1 -o "$f+1.pdf"
    chordpro $f -x 2 -o "$f+2.pdf"
    chordpro $f -x 3 -o "$f+3.pdf"
    chordpro $f -x 4 -o "$f+4.pdf"
    chordpro $f -x 5 -o "$f+5.pdf"
    chordpro $f -x 6 -o "$f+6.pdf"
    chordpro $f -x 7 -o "$f+7.pdf"
    chordpro $f -x 8 -o "$f+8.pdf"
    chordpro $f -x 9 -o "$f+9.pdf"
    chordpro $f -x 10 -o "$f+10.pdf"
    chordpro $f -x 11 -o "$f+11.pdf"
done
# For hver fil som er en pdf, flytt den til PDF-mappen.
for f in *.pdf; do 
    mv $f ../PDF/ 
done
# For hver fil som er .txt, lag pdf-er med bare tekst uten akkorder.
for f in *.txt; do 
    chordpro $f -l 
done
# For hver fil som er en pdf, flytt den til Lyrics-mappen.
for f in *.pdf; do 
    mv $f ../Lyrics/ 
done
```


