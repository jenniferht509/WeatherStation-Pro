# WeatherStation Pro

## Membres du groupe
| Nom | Rôle |
| :--- | :--- |
| Mondésir Léa Jennifer | Développeur principal |
| Romains Saïdel Seth Monsael | Programmation |
| Sirenice Ritchy Christopher | Simulation |
| Christophe Raisin | Câblage |

## Description du projet
WeatherStation Pro est une station météo intelligente simulée avec Raspberry Pi Pico et Wokwi.

Le système permet de :
- mesurer la température
- mesurer l’humidité
- comparer deux zones
- détecter le gaz
- afficher les données sur un écran OLED
- déclencher des alertes intelligentes

## Lien de simulation Wokwi
Cliquez ici : https://wokwi.com/projects/464144352519497729

## Capture d'ecran de la simulation


## Composants utilises
| Composant | Quantite | Role |
| :--- | :---: | :--- |
| Raspberry Pi Pico | 1 | |
| DHT22 | 2 | |
| BMP180/BMP280 | 1 | |
| MQ-2 / MQ-135 | 1 | |
| OLED SSD1306 | 1 | |
| LED RGB | 1 | |
| Servo SG90 | 1 | |
| Buzzer | 1 | |
| Boutons poussoirs | 2 | |
| Potentiomètre | 1 | |
| Résistances 10kΩ | 2 | |
| Résistances 220Ω | 3 | |

Informations techniques complémentaires sur les composants (Notes)
* **Fonctionnalités :** Surveillance double zone, Comparaison température/humidité, Détection de gaz, Affichage OLED, LED RGB intelligente, Alertes sonores, Contrôle du servo, Historique min/max, Réglage du seuil d’alerte.
* **Fichiers du projet :** `main.py`, `diagram.json`, `ssd1306.py`
* **Technologies utilisées :** MicroPython, Raspberry Pi Pico, Wokwi, GitHub

### GPIO utilisés
| Fonction | GPIO |
| :--- | :--- |
| DHT22 Zone 1 | GP2 |
| DHT22 Zone 2 | GP3 |
| OLED SDA | GP8 |
| OLED SCL | GP9 |
| LED Rouge | GP10 |
| LED Verte | GP11 |
| LED Bleue | GP12 |
| Servo | GP13 |
| Bouton navigation | GP14 |
| Bouton reset | GP15 |
| Buzzer | GP16 |
| Potentiomètre | GP26 |
| MQ-2 Gaz | GP27 |


## Tests realises
| Test | Resultat attendu | Resultat obtenu | OK/NOK |
| :--- | :--- | :--- | :---: |
| **OLED SSD1306** | L’écran affiche plusieurs pages : 1. Zone 1, 2. Zone 2, 3. Différence, 4. Gaz, 5. Pression, 6. État système. Navigation avec le bouton GP14. | Les pages défilent correctement et dans l'ordre à chaque appui sur le bouton GP14. | OK |
| **LED RGB** | Vert : Normal / Jaune : Alerte moyenne / Rouge : Danger / Bleu : Gaz détecté / Violet : Danger critique. | La LED change instantanément de couleur selon l'état des mesures et des seuils. | OK |
| **Servo SG90** | 0° : Normal / 90° : Alerte / 180° : Danger. | Le servomoteur se positionne précisément aux angles configurés selon la gravité. | OK |
| **Buzzer** | Le buzzer s’active si : gaz dangereux détecté, différence température > 5°C, humidité critique. | Le buzzer émet un signal sonore clair dès qu'une anomalie est détectée. | OK |

## Ameliorations possibles
- Ajouter un module de communication sans fil (comme le Wi-Fi sur Pico W) pour envoyer les données météo vers une interface web ou cloud.
- Intégrer un système de sauvegarde locale (carte SD) pour enregistrer les variations et l'historique des mesures au fil du temps.
- Optimiser le code en utilisant des interruptions matérielles pour une meilleure réactivité des boutons de navigation et de reset.

## Difficultes rencontrees
- Gestion du délai de lecture des capteurs DHT22 qui ralentissait au départ le rafraîchissement global de l'écran OLED lors du changement de page.
- Ajustement précis des seuils de déclenchement (LED, servo et buzzer) pour que les alertes visuelles et sonores fonctionnent de manière synchronisée.
- Configuration initiale des connexions et des adresses I2C pour l'affichage OLED dans l'environnement virtuel Wokwi.
