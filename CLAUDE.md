# CLAUDE.md

Dit project gebruikt BEM en ITCSS voor alle CSS.

## Bestand en lagen

- Alle CSS staat in css/screen.css, geen inline styles.
- screen.css is opgedeeld in 7 ITCSS-lagen met commentaar-headers, in deze volgorde:
  Settings, Tools, Generic, Elements, Objects, Components, Utilities.
- Nieuwe stijlen komen in de juiste laag, nooit zomaar onderaan het bestand.
- Generic bevat de reset: `box-sizing: border-box` op `*`, `*::before` en `*::after`,
  en `margin: 0` op `*`.
- Elements bevat `img { max-width: 100%; display: block; }`.
- Objects bevatten enkel structuur (layout, spacing), geen kleur of typografie.
- Utilities bevatten minstens één zinvolle utility-class.

## Naamgeving (BEM)

- Class-namen volgen BEM: block, block\_\_element, block--modifier, in kebab-case en
  altijd in het Engels. Geen ITCSS-prefixes zoals `o-`, `c-` of `u-` voor de laag: de
  naam zelf zegt genoeg.
- Een modifier staat in de HTML altijd samen met de base class, en in de CSS staat de
  base-regel vóór de modifier-regel.

## Selectors en specificiteit

- Geen id-selectors.
- Geen geneste selectors in components: gebruik `.post-card__title`, niet
  `.post-card h3`.
- CSS nesting met `&` enkel voor states (`:hover`, `:focus`).
- !important mag enkel in Utilities.
- Specificiteit stijgt enkel geleidelijk doorheen het bestand, van boven naar onder.

## Afmetingen

- Gebruik `max-width` in plaats van `width`, zodat elementen meekrimpen op kleine
  schermen.
- Centreer met `max-width` en `margin: auto` in een object.
- Een container met `padding-inline` en `box-sizing: border-box` telt de padding mee in
  `max-width`: tel die er met `calc()` bij op, zodat de inhoud zo breed is als in het
  ontwerp.
- Gebruik `rem` voor alle afmetingen. `px` enkel voor borders en shadows.

## Variabelen

- Kleuren, fonts, font-sizes, spacing en radius staan als CSS-variabelen in Settings.
- Spacing is een schaal op één basisvariabele met `calc()`.

## HTML

- Gebruik semantische HTML, `alt` op elke `<img>` en koppen zonder sprongen.
- Webfonts komen via een `<link>` naar Google Fonts in de `<head>`, icons via Material
  Symbols.

## Werkwijze

- Verzin geen teksten of waarden. Ontbreken ze, vraag ernaar.
- Haal waarden (kleuren, fonts, spacing, radius) uit de Variables van de Figma-kopie of
  via de Figma-MCP, nooit uit een screenshot.
- Werk sectie per sectie en controleer elke sectie in de browser naast het Figma-ontwerp.
- Staat een hover- of focus-waarde niet in Figma, vraag dan naar de kleur.
