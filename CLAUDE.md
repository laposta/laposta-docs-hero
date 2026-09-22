# CLAUDE.md, laposta-docs-hero: het zijden doek bovenaan de documentatie

<!-- LET OP: deze repo is publiek. Alles in dit bestand is openbaar. Geen interne paden,
     repo-namen, accountnummers of werkwijze. Houd het bij deze twee bestanden. -->

Twee bestanden, `index.html` en `wave-legacy.js`, samen een Three.js-animatie van een bewegend
zijden doek. Hij wordt als iframe ingeladen bovenaan de Laposta-documentatie.

## Leesvolgorde

1. Dit bestand.
2. `index.html`. Er is verder niets; twee bestanden is de hele repo.

## Publiceren

| wat | waar |
| --- | --- |
| de gepubliceerde pagina | https://laposta.github.io/laposta-docs-hero/ |
| bron | deze repo, branch `main`, map `/` (GitHub Pages) |

**Er is geen buildstap en geen deploy-script.** GitHub Pages publiceert `main` zelf, binnen een
minuut na een merge. Een merge naar `main` is dus een livegang.

## De commando's

| wat | commando |
| --- | --- |
| lokaal bekijken | `python3 -m http.server 8080`, dan `http://127.0.0.1:8080` |
| is de publicatie gelukt | `gh api /repos/laposta/laposta-docs-hero/pages --jq .status` (verwacht `built`) |
| de live pagina ophalen | `curl -sI https://laposta.github.io/laposta-docs-hero/` (verwacht 200) |

## Wat je niet aan de bestanden ziet

- **De fallback-keten is het punt van dit ding.** WebGL is niet overal beschikbaar. Haal de
  terugval niet weg omdat hij "nooit aan gaat": op een machine zonder WebGL is dat het enige wat
  de bezoeker te zien krijgt.
- **Het thema komt binnen via `postMessage`** vanuit de pagina die de hero insluit, niet uit een
  eigen voorkeursinstelling. De hero weet dus zelf niet of hij licht of donker moet zijn. Test
  altijd allebei, en test ook wat er gebeurt als er helemaal geen bericht binnenkomt.
- **`wave-legacy.js` staat er niet per ongeluk.** Kijk in `index.html` wanneer hij gebruikt
  wordt voordat je hem weggooit.
- **Deze repo is publiek** en moet dat blijven, want GitHub Pages publiceert geen privérepo op
  dit plan. Alles wat je commit is openbaar, de commit-berichten en PR-titels inbegrepen.

## Werkwijze

1. Werk op een feature-branch; `main` is beschermd, dus altijd via een pull request.
2. Zet in de PR wat je in de browser zag, in beide thema's, en wat er gebeurt zonder WebGL.
3. Controleer na de merge dat Pages `built` zegt en dat de documentatiepagina waar de hero
   staat er nog goed uitziet. Dat laatste is de echte controle.

Actueel per: 22 september 2026

## Waar de geschiedenis staat

De pull requests en commits van voor 22 september 2026 staan in de read-only repo
`laposta/laposta-docs-hero-archief`. Oude links verwijzen daar vanzelf naartoe.
