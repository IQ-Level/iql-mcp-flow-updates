# IQL Elementor MCP Flow — informacje o wydaniach

To repozytorium zawiera **jeden plik**: [`latest.json`](latest.json) z numerem
najnowszej wersji wtyczki i opisem zmian. Zaglądają tu zainstalowane kopie
wtyczki, żeby sprawdzić, czy jest coś nowszego. Nie ma tu kodu.

```json
{ "version": "1.16.1", "notes": "…", "published": "…" }
```

---

## Czym jest IQL Elementor MCP Flow

Wtyczka WordPress, która wystawia **WordPressa i Elementora jako serwer MCP**
(Model Context Protocol). Dzięki temu Claude — albo dowolny inny klient MCP —
buduje kompletne podstrony end-to-end: strukturę, treść, media, style, ustawienia
strony i wpięcie w menu.

Budowa podstrony w Elementorze to zwykle godziny klikania w edytorze. Tutaj
zamienia się w rozmowę:

> „Zbuduj podstronę usługi *Audyt SEO* według naszego szablonu — hero ze zdjęciem
> po prawej, trzy kafle korzyści, sekcja cennika, formularz kontaktowy. Wepnij
> w menu pod Usługi."

…a agent zwraca gotową, zgodną z brandingiem podstronę.

### Co ją odróżnia

- **37 narzędzi MCP**, nie 200 prymitywów. Każde narzędzie to stały koszt tokenów
  w każdym zapytaniu klienta — celujemy w mocne, komponowalne operacje.
- **Widgety z Waszych wtyczek.** Wtyczka odpytuje żywą instalację o dostępne
  widgety i ich schematy, zamiast zgadywać. Agent używa tego, co realnie jest
  zainstalowane — także z wtyczek dodatkowych i Elementor Pro.
- **Zapis wyłącznie przez Document API Elementora.** Nie dotykamy
  `_elementor_data` przez `update_post_meta`, bo to zostawia nieodświeżony CSS
  i brak rewizji.
- **Siatka bezpieczeństwa.** Każda operacja pisząca ma tryb `dry_run`, robi
  snapshot przed zapisem i zostawia wpis w dzienniku operacji. Każdą zmianę da
  się cofnąć.
- **Podgląd i lint.** Agent widzi wyrenderowany efekt swojej pracy i dostaje
  raport z błędów układu, zamiast zgadywać, czy wyszło.

### Wymagania

| | |
|---|---|
| WordPress | 6.9+ (Abilities API w rdzeniu) |
| PHP | 8.1+ |
| Elementor | 3.16+ (Pro wymagane dla Theme Buildera) |

Zweryfikowane na WordPress 7.0.4, PHP 8.3, Elementor 4.2.2.

### Fundament

Nie piszemy protokołu MCP od zera. Stoimy na oficjalnym stosie WordPressa:
[Abilities API](https://developer.wordpress.org/apis/abilities-api/) z rdzenia
WP 6.9 oraz [WP MCP Adapter](https://github.com/WordPress/mcp-adapter).

---

## Chcecie tego u siebie?

Wtyczka jest **komercyjna i zamknięta** — kod nie jest publiczny. Jeśli
budujecie strony na Elementorze i to brzmi jak coś, co oszczędziłoby Wam
godziny, **załóżcie [Issue](../../issues)** albo napiszcie do
[IQ-Level](https://github.com/IQ-Level) — odpiszemy.

## Aktualizacje

Zainstalowana wtyczka sprawdza wersję sama, po kliknięciu **Sprawdź teraz**
w panelu (WP Admin → IQL Flow). Stąd idzie wyłącznie numer wersji i opis zmian —
paczkę z nową wersją klienci dostają kanałem, którym kupili wtyczkę.
