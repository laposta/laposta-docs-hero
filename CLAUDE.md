# CLAUDE.md, laposta-docs-hero: het zijden doek bovenaan de documentatie

Twee bestanden, `index.html` en `wave-legacy.js`, samen een Three.js-animatie van een bewegend
zijden doek. Hij wordt als iframe ingeladen op de overzichtspagina van de Fern-documentatie
(`fern/pages/overzicht.mdx` in `laposta-docs-fern`). De serverregels
(`/srv/laposta-infra/AGENTS.md`) laden vanzelf en winnen.

## Leesvolgorde, dit is het maximum

1. Dit bestand.
2. `index.html`. Er is verder niets; twee bestanden is de hele repo.

## Wat er draait en waar

| wat | waar |
| --- | --- |
| de gepubliceerde pagina | https://laposta.github.io/laposta-docs-hero/ |
| bron van die pagina | **deze repo, branch `main`, map `/`** (GitHub Pages, build_type `legacy`) |
| waar hij getoond wordt | `laposta/laposta-docs-fern`, `fern/pages/overzicht.mdx`, als iframe |

**Er is geen deploy-script en geen dienst.** GitHub Pages publiceert `main` zelf, binnen een
minuut na een merge. Een merge naar `main` is dus een livegang.

## De commando's

| wat | commando |
| --- | --- |
| lokaal bekijken | `python3 -m http.server 8080` in de repo, dan `http://127.0.0.1:8080` |
| is de publicatie gelukt | `gh api /repos/laposta/laposta-docs-hero/pages --jq .status` (verwacht: `built`) |
| de live pagina ophalen | `curl -sI https://laposta.github.io/laposta-docs-hero/` (verwacht: 200) |

## Wat je niet aan de mappen ziet

- **Deze repo is PUBLIEK, en dat moet ook**: GitHub Pages werkt niet op een privérepo in dit
  plan. Alles wat je hier commit is openbaar, de commit-historie en de commit-berichten
  inbegrepen. Zet er dus geen interne notities, klantnamen, repo-namen of werkwijze in.
- **De fallback-keten is het punt van dit ding.** WebGL is niet overal beschikbaar. Haal de
  terugval niet weg omdat hij "nooit aan gaat": op een machine zonder WebGL is dat het enige
  wat de bezoeker ziet.
- **Het thema komt binnen via `postMessage`** vanuit de Fern-pagina, niet uit een eigen
  voorkeursinstelling. De hero weet dus niet zelf of hij licht of donker moet zijn. Test altijd
  allebei, en test ook wat er gebeurt als er helemaal geen bericht komt.
- **`wave-legacy.js` is de oudere variant en staat er niet per ongeluk.** Kijk in `index.html`
  wanneer hij gebruikt wordt voordat je hem weggooit.

## Werkwijze per ronde

1. Worktree van `origin/main` (`AGENTS.md` §2). `main` is beschermd, dus altijd een PR.
2. Bewijs in de PR: een schermafdruk of een beschrijving van wat je in de browser zag, in beide
   thema's, plus wat er gebeurt zonder WebGL.
3. Na de merge: controleer dat Pages `built` zegt en dat de overzichtspagina van de docs er nog
   goed uitziet. Dat laatste is de echte controle, want daar staat hij.

## Deze gids actueel houden

Raakt je wijziging de publicatie, de fallback of het thema, werk dan in dezelfde PR dit bestand
bij en zet de regel hieronder op je commitdatum.

Actueel per: 22 september 2026

## Waar de geschiedenis staat

De pull requests en commits van voor 22 september 2026 staan in `laposta/laposta-docs-hero-archief`. Die repo is read-only: hij is meeverhuisd zodat de historie niet aan een persoonlijk account blijft hangen. Oude links naar de vorige plek verwijzen er vanzelf naartoe.
