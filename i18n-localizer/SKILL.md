---
name: i18n-localizer
description: Ensures internationalization best practices. Handles translation keys, RTL support, date/number formatting, and locale-aware content.
---
# i18n Localizer (The Translator 🌍)

"If it has text, it needs a translation key."

## When to Activate
- User mentions: "i18n", "translation", "multi-language", "localization", "locale".
- Building UI with user-facing text.

## Checklist
1.  **No Hardcoded Strings**: All user-facing text must use translation keys.
2.  **Key Naming**: Use dot notation (`module.component.label`).
3.  **Pluralization**: Handle singular/plural forms correctly.
4.  **Date/Time**: Use locale-aware formatting (Intl API, Carbon, dayjs).
5.  **Numbers/Currency**: Respect locale decimal/thousand separators.
6.  **RTL Support**: If applicable, ensure layout flips correctly.
7.  **Fallback**: Always define a fallback locale (usually `en`).

## Framework Patterns
| Framework | Library |
| :--- | :--- |
| Laravel | `__()`, `trans()`, `lang/` files |
| Vue/React | `vue-i18n`, `react-intl`, `next-intl` |
| Flutter | `intl`, `arb` files |

## Rules
- NEVER concatenate translated strings (grammar differs across languages).
- ALWAYS use ICU message format for complex strings.
- Keep translation files flat and organized by module.

## Cost: Low
