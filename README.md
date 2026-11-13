# Portfolio Frank Verberne

Persoonlijke portfoliosite, gehost op GitHub Pages. Eén `index.html` met inline CSS: geen build, geen dependencies.

## Lokaal bekijken

```bash
python3 -m http.server 8123
```

Open daarna http://localhost:8123 in je browser. Stoppen doe je met `Ctrl+C`.

## Eerste keer publiceren

Vervang `<account>` door je GitHub-gebruikersnaam in kleine letters, bijvoorbeeld `fvmf`. De repo moet precies `<account>.github.io` heten. Dan staat de site op `https://<account>.github.io`.

1. Log in met het juiste account:

   ```bash
   gh auth login
   ```

   Kies GitHub.com, HTTPS en "Login with a web browser". Heb je meerdere accounts, wissel dan met `gh auth switch --user <account>`. Met `gh auth status` zie je welk account actief is.

2. Maak van deze map een git-repo en doe de eerste commit:

   ```bash
   git init -b main
   git add index.html frank.jpg README.md .nojekyll
   git commit -m "feat: eerste versie portfolio"
   ```

3. Maak de repo op GitHub en push in één stap:

   ```bash
   gh repo create <account>.github.io --public --source=. --push
   ```

4. Controleer of Pages aanstaat:

   ```bash
   gh api repos/<account>/<account>.github.io/pages -q .html_url
   ```

   Krijg je een 404, zet Pages dan aan:

   ```bash
   gh api -X POST repos/<account>/<account>.github.io/pages -f "source[branch]=main" -f "source[path]=/"
   ```

   Via de website kan het ook: Settings, Pages, "Deploy from a branch", branch `main`, map `/ (root)`.

5. Na een à twee minuten staat de site online. De status van de laatste build zie je met:

   ```bash
   gh api repos/<account>/<account>.github.io/pages/builds/latest -q .status
   ```

## Een wijziging publiceren

```bash
git add index.html
git commit -m "feat(cases): voeg case X toe"
git push
```

GitHub Pages zet de nieuwe versie binnen ongeveer een minuut online.

## Een case toevoegen

Kopieer in `index.html` een volledig `<article class="case">`-blok, geef het een nieuw `id` en vul Probleem, Wat ik bouwde, Wat ik leerde en Resultaat in. Elke `<li>` in `<ol class="flow">` is een knooppunt in het schema. Wil je de case vanuit "Mijn route" laten aanklikken, verwijs dan met `href="#jouw-id"`.

## Alles is openbaar

Een GitHub Pages-repo op een gratis account is publiek, inclusief dit bestand. Zet er geen adres, telefoonnummer, geboortedatum, namen van collega's, interne URL's of ID's in.
