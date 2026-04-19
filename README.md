# 🏠 Skill Claude Code — Impôts personnels français

Skill Claude Code pour la fiscalité française des particuliers. Compatible avec [paperasse](https://github.com/romainsimon/paperasse).

## Ce que ça couvre

- **IR** : barème progressif, quotient familial, plafonnement QF, décote, PER, PFU vs barème, CEHR
- **IFI** : assiette, passif déductible, exonérations
- **Plus-values** : immobilières (abattements durée) et mobilières
- **Revenus fonciers** : micro vs réel, déficit foncier, LMNP
- **IS & SASU** : arbitrage salaire/dividendes, piège de modélisation
- **Succession/donation** : abattements, Dutreil, assurance-vie
- **Crypto** : méthode PAMC, fait générateur
- **Déductions vs réductions vs crédits**

## Avec le serveur MCP irpp-mcp

Si le serveur MCP [irpp-mcp](https://github.com/erwanpaccard/irpp-mcp) est actif, le skill l'utilise automatiquement pour les simulations IR — les calculs s'appuient alors sur le code source officiel DGFiP compilé via [Mlang (OCamlPro/DGFiP)](https://gitlab.adullact.net/dgfip/impots-nationaux-revenu-patrimoine-particuliers/Mlang).

## Installation

```bash
# Cloner dans ton répertoire de skills Claude Code
git clone https://github.com/erwanpaccard/impots ~/.claude/skills/impots
```

Le skill est alors disponible via `/impots` dans Claude Code.

## Philosophie

Focalise sur la **logique des mécanismes**, pas les chiffres. Les barèmes changent chaque loi de finances — le skill demande systématiquement de vérifier les valeurs actuelles sur impots.gouv.fr.
