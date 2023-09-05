---
{"dg-publish":true,"permalink":"/vault-one/kodekameraten-no/archive/howtomac/"}
---

# ---
# title: I'm Sorry
# date: 2019-03-12T10:12:21+01:00
# draft: false
# tags: Norsk
# dg-publish: true
# ---

I vennekretsen min er jeg kjent som den som har oversikt om hva som finnes av programmer og ulike løsninger.
Her er en liste over programmer som jeg ofte bruker.

- [Pakkehåndtering](#pakkeh%C3%A5ndtering)
  - [Homebrew](#homebrew)
- [Vindushåndtering](#vindush%C3%A5ndtering)
  - [Spectacle](#spectacle)
  - [Amethyst](#amethyst)
- [Nettlesere](#nettlesere)
  - [Firefox](#firefox)
    - [Plugins/Add-Ons/Extensions](#pluginsadd-onsextensions)
- [Passordhåndtering](#passordh%C3%A5ndtering)
- [MedieAvspilling](#medieavspilling)
  - [iina](#iina)
  - [Spotify](#spotify)
  - [ZSH](#zsh)
  - [Spark](#spark)
  - [GitKraken](#gitkraken)
  - [Appcleaner](#appcleaner)
  - [Gemini 2](#gemini-2)
  - [GrandPerspective](#grandperspective)
  - [Musikk](#musikk)
    - [Ableton](#ableton)
    - [Splice](#splice)
- [Synkronisering og deling av data](#synkronisering-og-deling-av-data)
  - [Resilio Sync](#resilio-sync)
    - [Pros & Cons](#pros--cons)
- [Akkordnotering](#akkordnotering)
  - [Chordpro](#chordpro)
    - [Installasjon](#installasjon)
    - [Generere sanger i alle tonearter](#generere-sanger-i-alle-tonearter)

# Pakkehåndtering
## Homebrew
Homebrew er det første jeg anbefaler å installere på en ny maskin.
Homebrew er en pakkehåndterer, ikke ulik `apt-get` i Ubuntu eller `pacman` i Arch.

Med Homebrew kan man installere unix-verktøy og vanlige programmer uten å måtte klikke gjennom installasjonsvinduer.

Det er også lett å holde alt oppdatert.
```bash
brew upgrade && brew cask upgrade
```

# Vindushåndtering
Jeg vil personlig anbefale Spectacle for de fleste. Dersom du er mer nørd enn resten kan du sjekke ut Amethyst.
## Spectacle
```bash 
brew cask install spectacle
```

## Amethyst
```bash 
brew cask install amethyst
```
# Nettlesere
## Firefox
Regular version
```bash
brew cask install firefox
```

Developer version
```bash
brew cask install firefox-developer-edition
```

### Plugins/Add-Ons/Extensions
LastPass
AdNauseum
VimVixen
DuckDuckGo Privacy Essentials
LanguageTool

# Passordhåndtering
Det er en dårlig idé å bruke det samme passordet, eller lignende passord flere steder. Bruk heller en passordhådterer.
Det er ikke så farlig hvilken du velger, bare at du bruker en. Dersom du ikke vet hvilken du skal bruke, velg LastPass.

Noen Alternativ:

- [Lastpass](https://www.lastpass.com/)
- Keepass
- [OnePassword](https://1password.com/)
- Dashlane

# MedieAvspilling
## iina
Som VLC, bare mer tilpasset din mac.
```bash 
brew cask install iina
```
## Spotify
```bash 
brew cask install spotify
```

## ZSH
ohmyzsh

## Spark
Email
```bash 
brew cask install spark
```

## GitKraken
```bash
brew cask install gitkraken
```
## Appcleaner
```bash 
brew cask install appcleaner
```

## Gemini 2
Gratis alternativ er dupeGuru.

## GrandPerspective 
Betalt alternativ er DaisyDisk.

## Musikk

### Ableton 
### Splice

# Synkronisering og deling av data
## Resilio Sync
I motsetning til Dropbox så lagres ikke filene på nett, men synkroniseres via en direkte tilkobling fra en data- til en annen datamaskin.

### Pros & Cons
Dette har noen fordeler:

1. Ingen plassbegrensning.
2. Gratis (utenom noen få pro-funksjoner)
3. Rask og direkte overføring av store filer.

Men også noen ulemper:

1. For å laste ned filer må en annen datamaskin være på.
2. Noen nettverk kan ha blokkert p2p teknologien som *Resilio Sync* bruker.

# Akkordnotering
## Chordpro
Chordpro brukes når man vil ha nøyaktig plassering av akkorder i tekst-dokumentet, og ha mulighet til å transponere når som helst.

![Chordpro eksempel](/img/user/img/love-me-tender-small.png.md)

Chordro er bare vanlige *.txt*-filer, men man kan generere (blant annet) pdf ut av det.

### Installasjon

Se [https://www.chordpro.org](https://www.chordpro.org/chordpro/ChordPro-Installation.html) for hjelp til installasjon.

Dersom du har Mac kan du installere *Chordpro Cli*-programmet ved å skrive ``sudo /usr/bin/cpan chordpro`` i terminalen din.

### Generere sanger i alle tonearter

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