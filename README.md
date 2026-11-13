# Portfolio Frank Verberne

Live op **https://frankautomatiseert.nl**, gehost op GitHub Pages vanuit deze repo (`FVMF/portfolio`, branch `main`).

Eén `index.html` met inline CSS: geen build, geen dependencies, geen JavaScript.

## Lokaal bekijken

```bash
python3 -m http.server 8123
```

Open daarna http://localhost:8123 in je browser. Stoppen doe je met `Ctrl+C`.

## Een wijziging publiceren

Git logt in via `gh`, met het account dat daar actief is. Zet dus eerst FVMF actief en daarna weer terug:

```bash
gh auth switch --user FVMF
git add index.html
git commit -m "feat(cases): voeg case X toe"
git push
gh auth switch --user Verandert-Gewoon
```

GitHub Pages zet de nieuwe versie binnen ongeveer een minuut online. Browsers kunnen de oude versie nog tot 10 minuten tonen; ververs dan de pagina.

## Een case toevoegen

Kopieer in `index.html` een volledig `<article class="case">`-blok, geef het een nieuw `id` en vul Probleem, Wat ik bouwde, Wat ik leerde en Resultaat in.

Het schema per case bestaat uit rijen (`.graph-row`) met nodes (`.node`):

```html
<div class="graph-row" style="--n:2">
  <div class="node"><strong>Titel</strong><span>toelichting</span></div>
  <div class="node out"><strong>Eindresultaat</strong></div>
</div>
```

- `--n` is het aantal nodes in de rij.
- Tussen twee rijen ontstaat vanzelf een splitsing of samenvoeging.
- `class="graph-row lanes"` laat elke kolom 1-op-1 doorlopen naar de volgende rij.
- `node out` geeft het eindresultaat een gevulde kleur.

## Domein

`frankautomatiseert.nl` is geregistreerd bij Hostnet. Het bestand `CNAME` vertelt GitHub Pages welk domein bij deze repo hoort; niet verwijderen.

DNS-records bij Hostnet:

| Type | Naam | Waarde |
|---|---|---|
| A (4x) | frankautomatiseert.nl | 185.199.108.153, .109.153, .110.153, .111.153 |
| AAAA (4x) | frankautomatiseert.nl | 2606:50c0:8000::153 t/m 2606:50c0:8003::153 |
| CNAME | www.frankautomatiseert.nl | fvmf.github.io |
| TXT | _github-pages-challenge-FVMF.frankautomatiseert.nl | verificatiecode van GitHub |
| TXT | frankautomatiseert.nl | `v=spf1 -all` (geen e-mail op dit domein) |
| TXT | _dmarc.frankautomatiseert.nl | `v=DMARC1; p=reject` |

## Alles is openbaar

Deze repo is publiek, inclusief dit bestand. Zet er geen adres, telefoonnummer, volledige geboortedatum, namen van collega's, interne URL's of ID's in.
