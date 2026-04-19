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

## Barèmes officiels

Le fichier `bareme_revenus_2025.json` contient les chiffres de la LFI n°2026-103 du 19 février 2026 (revenus 2025, déclaration 2026) : tranches IR, décote, plafond QF, PER, IFI, succession/donation, micro-foncier, micro-BIC LMNP, PEA, assurance-vie.

**Vérification** : chiffres extraits du [BOFiP](https://bofip.impots.gouv.fr) et croisés avec [service-public.gouv.fr](https://www.service-public.gouv.fr). La formule de décote (45,25%) a été vérifiée sur `BOI-IR-LIQ-20-20-30-20260407`.

**Mise à jour annuelle** (chaque janvier après la LFI) :
1. Créer `bareme_revenus_XXXX.json` en copiant le fichier existant
2. Mettre à jour les valeurs depuis le BOFiP (chercher `BOI-IR-LIQ-20-10` pour le barème, `BOI-IR-LIQ-20-20-30` pour la décote)
3. Vérifier avec le simulateur officiel : [simulateur-ir-ifi.impots.gouv.fr](https://simulateur-ir-ifi.impots.gouv.fr)
4. Mettre à jour la référence dans `SKILL.md` (`bareme_revenus_XXXX.json`)

## Avec le serveur MCP irpp-mcp

Si le serveur MCP [irpp-mcp](https://github.com/erwanpaccard/irpp-mcp) est actif, le skill l'utilise automatiquement pour les simulations IR — les calculs s'appuient alors sur le code source officiel DGFiP compilé via [Mlang (OCamlPro/DGFiP)](https://gitlab.adullact.net/dgfip/impots-nationaux-revenu-patrimoine-particuliers/Mlang).

Couverture :
- ✅ Revenus 2023 (déclaration 2024) — compilé et fonctionnel
- ❌ Revenus 2024 (déclaration 2025) — sources DGFiP incompatibles avec la version actuelle de Mlang
- ❌ Revenus 2025 (déclaration 2026) — non disponible

## Installation

```bash
# Cloner dans ton répertoire de skills Claude Code
git clone https://github.com/erwanpaccard/impots ~/.claude/skills/impots
```

Le skill est alors disponible via `/impots` dans Claude Code.

## Philosophie

Focalise sur la **logique des mécanismes**, pas les chiffres. Les barèmes changent chaque loi de finances — le skill demande systématiquement de vérifier les valeurs actuelles sur impots.gouv.fr.
