# Digiwake — Réveil numérique Arduino

**Digiwake** est un réveil / horloge intelligent réalisé sur **Arduino**.
Il affiche l'heure, gère un menu de navigation, une alarme avec mélodies, et permet
de **repousser l'alarme par un geste** grâce à un capteur à ultrasons.

---

## Fonctionnalités

- ⏰ **Horloge temps réel** (module RTC) avec format **12h / 24h**
- 🖥️ **Affichage** sur écran **OLED SSD1306 128×64** + **matrices LED MAX7219** (4 modules)
- 🧭 **Menu de navigation** à 4 boutons (haut, bas, choix, retour)
- 🔧 **Réglage de l'heure** et des paramètres directement depuis le menu
- 🔔 **Réveil / alarme** avec heure programmable et activation ON/OFF
- 🎵 **Mélodies de sonnerie** mémorisées en **EEPROM** (plusieurs mélodies au choix)
- 👋 **Snooze par geste** : le **capteur à ultrasons** détecte un mouvement pour reporter l'alarme
- 💡 **LED** de signalisation (clignotement)
- ⏱️ Sonnerie limitée dans le temps + bouton **stop**

## Matériel

| Composant | Rôle |
|-----------|------|
| Arduino (Uno / Nano) | Microcontrôleur principal |
| Écran OLED SSD1306 (I²C) | Affichage de l'heure et des menus |
| 4× Matrices LED MAX7219 | Affichage grand format de l'heure |
| Module RTC (DS1307 / DS3231) | Horloge temps réel |
| Buzzer | Sonnerie / mélodies |
| Capteur à ultrasons (HC-SR04) | Détection de geste pour le snooze |
| Boutons ×5 | Haut, bas, choix, retour, stop |
| LED | Indicateur visuel |

### Brochage (d'après le code)

| Élément | Broche |
|---------|--------|
| Bouton haut | 7 |
| Bouton choix | 6 |
| Bouton bas | 5 |
| Bouton retour | 4 |
| Bouton stop | 9 |
| Buzzer | 3 |
| Capteur ultrason (trig / echo) | 2 / 12 |
| LED | 8 |
| Matrices MAX7219 (DIN / CLK / CS) | 11 / 13 / 10 |
| Écran OLED | I²C (SDA / SCL) |

## Bibliothèques Arduino requises

- `Wire` (I²C)
- `U8glib` (écran OLED)
- `LedControl` (matrices MAX7219)
- `RTClib` (horloge temps réel)
- `EEPROM` (mémorisation des mélodies)
- `Adafruit_GFX`

## Structure du dépôt

```
.
├── CODE VERSION FINALE      # Code Arduino final et fonctionnel du réveil
├── Code temporaire/         # Versions de travail / brouillons et essais (.docx, .txt)
└── README.md
```

- **`CODE VERSION FINALE`** : la version aboutie à téléverser sur l'Arduino.
- **`Code temporaire/`** : historique des essais (matrice, écran, EEPROM, mélodies,
  gestion de l'heure, capteur…) conservé à titre de documentation. *Non destiné à être
  utilisé en production.*

## Installation

1. Installer l'**IDE Arduino** et les bibliothèques listées ci-dessus.
2. Ouvrir le fichier **`CODE VERSION FINALE`** (le copier dans un sketch `.ino`).
3. Câbler les composants selon le brochage ci-dessus.
4. Sélectionner la carte et le port, puis téléverser.

## Utilisation

- Naviguer dans le menu avec **haut / bas**, valider avec **choix**, revenir avec **retour**.
- Régler l'heure, le format (12h/24h), l'alarme et la mélodie depuis le menu.
- Lorsque l'alarme sonne : appuyer sur **stop**, ou **passer la main devant le capteur**
  pour reporter (snooze).

---

*Projet Arduino — réveil numérique Digiwake.*
