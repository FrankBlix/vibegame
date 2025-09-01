# 🏆 Online Highscore Setup Guide

For å aktivere online highscores som kan deles mellom alle spillere, følg disse stegene:

## 🔧 Setup Instructions

### Step 1: Opprett JSONBin Account
1. Gå til [jsonbin.io](https://jsonbin.io)
2. Registrer en gratis konto
3. Logg inn på dashboard

### Step 2: Opprett en ny Bin
1. Klikk "Create Bin"
2. Skriv inn følgende JSON:
```json
{
  "highscores": []
}
```
3. Klikk "Create"
4. Kopier **Bin ID** fra URL (f.eks. `68b5a75343b1c97be933289f`)

### Step 3: Få API Key
1. Gå til "API Keys" i dashboard
2. Kopier din **Master Key**

### Step 4: Oppdater Spill-koden
Åpne `gravity.html` og finn denne linjen (rundt linje 110):

```javascript
// Online highscore API (using JSONBin.io as a simple database)
const HIGHSCORE_API = {
    url: 'https://api.jsonbin.io/v3/b/REPLACE_WITH_YOUR_BIN_ID', 
    headers: {
        'Content-Type': 'application/json',
        'X-Master-Key': 'REPLACE_WITH_YOUR_API_KEY'
    }
};
```

Erstatt:
- `REPLACE_WITH_YOUR_BIN_ID` med din Bin ID
- `REPLACE_WITH_YOUR_API_KEY` med din Master Key

Du må også oppdatere to andre steder i koden hvor Bin ID og API key er hardkodet.

### Step 5: Push til GitHub
1. Commit endringene
2. Push til GitHub
3. Aktiver GitHub Pages hvis ikke allerede gjort

## 🌍 Sharing Your Game

Når online highscores er aktivert:
- Alle som spiller samme URL deler highscore-listen
- Scores lagres både lokalt og online
- Del GitHub Pages URL med venner!

## 🔒 Security Note

API-nøkkelen din vil være synlig i kildekoden. For et hobby-prosjekt som dette er det OK, men bruk gjerne "Read & Write" permissions i stedet for "Master" for ekstra sikkerhet.

## 🐛 Troubleshooting

- **Scores lagres ikke online**: Sjekk at Bin ID og API key er riktige
- **CORS errors**: JSONBin.io støtter CORS, så dette skal ikke være et problem
- **Ingen internet**: Spillet fungerer fortsatt med lokale highscores

## 🎮 Alternative Solutions

Hvis JSONBin.io ikke fungerer, kan du bruke:
- Firebase Realtime Database
- Supabase
- GitHub Gists (med personal access token)
- Din egen server med enkel API

Erstatt bare API-kallene i koden med din foretrukne tjeneste!
