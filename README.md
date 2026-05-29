# WeatherStation Project

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
Cliquez ici : https://wokwi.com/projects/465292447307710465

## Capture d'ecran de la simulation


## Composants utilises
| Composant | Quantite | Role |
| :--- | :---: | :--- |
| Raspberry Pi Pico | 1 | Microcontrôleur principal exécutant le script MicroPython. |
| DHT22 | 2 | Capteurs numériques de température et d'humidité pour les deux zones. |
| BMP180/BMP280 | 1 | Capteur de pression barométrique pour le suivi atmosphérique. |
| MQ-2 / MQ-135 | 1 | Capteur de gaz pour le contrôle de la qualité de l'air. |
| OLED SSD1306 | 1 | Écran d'affichage pour visualiser les mesures et l'état du système. |
| LED RGB | 1 | Indicateur visuel multicolore pour signaler le niveau de danger. |
| Servo SG90 | 1 | Actionneur mécanique pour indiquer physiquement l'état d'alerte. |
| Buzzer | 1 | Signal sonore d'avertissement en cas de dépassement de seuil critique. |
| Boutons poussoirs | 2 | Boutons dédiés à la navigation des pages OLED et au reset. |
| Potentiomètre | 1 | Composant analogique pour ajuster manuellement les seuils d'alerte. |
| Résistances 10kΩ | 4 | Résistances de tirage pour la stabilisation des boutons poussoirs. |
| Résistances 220Ω | 3 | Résistances de protection pour les broches de la LED RGB. |

## GPIO utilisés
| Fonction | GPIO |
| --- | --- |
| DHT22 Zone 1 | GP2 |
| DHT22 Zone 2 | GP3 |
| OLED SDA | GP8 |
| OLED SCL | GP9 |
| LED Rouge | GP10 |
| LED Verte | GP11 |
| LED Bleue | GP12 |
| Servo SG90 | GP13 |
| Bouton navigation | GP14 |
| Bouton reset | GP15 |
| Buzzer | GP16 |
| Potentiomètre | GP26 |
| MQ‑135 Gaz | GP27 |

## Tests réalisés
| Test | Résultat attendu | Résultat obtenu | OK/NOK |
| --- | --- | --- | --- |
| **OLED SSD1306** | Affiche 6 pages : Zone 1, Zone 2, Différence, Gaz, Seuil réglable, État système. Navigation avec le bouton GP14. | Les pages défilent correctement et dans l’ordre à chaque appui sur le bouton GP14. | OK |
| **LED RGB** | Vert : Normal / Jaune : Différence zones / Rouge : Température élevée / Bleu : Humidité forte / Violet : Gaz dangereux. | La LED change instantanément de couleur selon l’état des mesures et des seuils. | OK |
| **Servo SG90** | 0° : Normal / 90° : Alerte / 180° : Danger. | Le servomoteur se positionne précisément aux angles configurés selon la gravité. | OK |
| **Buzzer** | S’active si : gaz dangereux détecté, température > 35°C, humidité critique, ou différence entre zones > seuil. | Le buzzer émet un signal sonore clair et répétitif dès qu’une anomalie est détectée. | OK |
| **Boutons** | GP14 : navigation / GP15 : reset min/max et confirmation sonore. | Les boutons réagissent correctement, avec bip et affichage “RESET OK” sur l’OLED. | OK |

## Ameliorations possibles
- Ajouter un module de communication sans fil (comme le Wi-Fi sur Pico W) pour envoyer les données météo vers une interface web ou cloud.
- Intégrer un système de sauvegarde locale (carte SD) pour enregistrer les variations et l'historique des mesures au fil du temps.
- Optimiser le code en utilisant des interruptions matérielles pour une meilleure réactivité des boutons de navigation et de reset.

## Difficultes rencontrees
- Gestion du délai de lecture des capteurs DHT22 qui ralentissait au départ le rafraîchissement global de l'écran OLED lors du changement de page.
- Ajustement précis des seuils de déclenchement (LED, servo et buzzer) pour que les alertes visuelles et sonores fonctionnent de manière synchronisée.
- Configuration initiale des connexions et des adresses I2C pour l'affichage OLED dans l'environnement virtuel Wokwi.
