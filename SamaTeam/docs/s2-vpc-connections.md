# Connexions 6 Chapeaux → VPC — SamaResto

## Profil Client — Traçabilité

### Jobs To Be Done
| Job | Chapeau Source | Citation |
|---|---|---|
| Traiter 50-100 commandes sans erreur pendant le rush | Chapeau Blanc | "À Point E, le rush de midi (12h-14h) concentre 50 à 100 commandes en 2 heures chez Aïda ; aujourd'hui tout transite par bons papier écrits à la main entre caisse et cuisine, un mode qui échoue visiblement dès que le volume dépasse le rythme d'un seul poste." |
| Communiquer clairement avec l'équipe cuisine | Chapeau Rouge | "Ses 2-3 employés vivent le rush comme une source de stress et de frustration quand les commandes orales ou les bouts de papier se contredisent." |
| Suivre les ventes et réconcilier la caisse | Chapeau Jaune | "En fin de journée Aïda dispose d'un rapport de ventes instantané qui lui donne une meilleure lecture de sa trésorerie sans saisie manuelle." |
| Garder le contrôle et la sérénité pendant le coup de feu | Chapeau Rouge | "Pendant le coup de feu, Aïda ressent une tension entre la fierté de garder le contrôle de son commerce et une anxiété réelle de perdre une commande ou un client sans s'en rendre compte." |

### Pains
| Pain | Chapeau Source | Citation |
|---|---|---|
| Commandes perdues ou dupliquées sur papier | Chapeau Blanc | "Tout transite par bons papier écrits à la main entre caisse et cuisine, un mode qui échoue visiblement dès que le volume dépasse le rythme d'un seul poste." |
| La cuisine ne reçoit pas les commandes à temps | Chapeau Rouge | "Les commandes orales ou les bouts de papier se contredisent" — source de confusion et de retard en cuisine. |
| Absence de visibilité, Aïda court entre les postes | Chapeau Rouge | "Pendant le coup de feu, Aïda ressent une tension entre la fierté de garder le contrôle de son commerce et une anxiété réelle de perdre une commande." |
| Suivi manuel des ventes source d'erreurs et de stress | Non directement tracé dans un Chapeau | Dérivé de la carte d'empathie S1 ("no reliable sales tracking, everything on paper") — à confirmer en S3. |

### Gains
| Gain | Chapeau Source | Citation |
|---|---|---|
| Flux de commandes rapide pendant le rush | Chapeau Jaune | "Aïda gagne une visibilité instantanée sur l'état de chaque commande : plus de commandes perdues, un contrôle retrouvé même en pleine cohue." |
| Zéro commande perdue ou dupliquée, confiance dans le système | Chapeau Vert | "Et si le système fonctionnait en mode 'offline-first', mettant les commandes en file d'attente locale puis les synchronisant automatiquement dès le retour du WiFi ?" |
| Visibilité en temps réel, tranquillité d'esprit | Chapeau Jaune | "Aïda gagne une visibilité instantanée sur l'état de chaque commande." |
| Rapport de ventes fiable en fin de journée | Chapeau Jaune | "En fin de journée Aïda dispose d'un rapport de ventes instantané qui lui donne une meilleure lecture de sa trésorerie sans saisie manuelle." |

## Proposition de Valeur — Traçabilité

### Pain Relievers
| Reliever | Pain Addressed | Chapeau Source |
|---|---|---|
| Transmission digitale instantanée, zéro papier | Commandes perdues ou dupliquées sur papier | Chapeau Noir (risque WiFi/cloud) + Chapeau Vert (idée offline-first) |
| Affichage instantané de la commande en cuisine | La cuisine ne reçoit pas les commandes à temps | Chapeau Rouge (confusion des commandes orales/papier) + Chapeau Jaune (empowerment employés) |
| Statut de commande partagé en temps réel | Absence de visibilité, Aïda court entre les postes | Chapeau Jaune (visibilité instantanée) |
| Rapport de ventes automatique | Suivi manuel des ventes source d'erreurs et de stress | Chapeau Jaune (rapport de ventes instantané) |

### Gain Creators
| Creator | Gain Addressed | Chapeau Source |
|---|---|---|
| Synchronisation instantanée caisse↔cuisine | Flux de commandes rapide pendant le rush | Chapeau Vert (idée offline-first / sync temps réel) |
| File d'attente locale hors-ligne | Zéro commande perdue ou dupliquée, confiance | Chapeau Vert (offline-first) + Chapeau Noir (risque WiFi à mitiger) |
| Statut visible sur les deux tablettes | Visibilité en temps réel, tranquillité d'esprit | Chapeau Jaune (visibilité) + Chapeau Vert (alertes multi-modales) |
| Génération automatique du rapport de fin de journée | Rapport de ventes fiable en fin de journée | Chapeau Jaune (rapport instantané) |

## Éléments Non Tracés
- **Pain "Suivi manuel des ventes source d'erreurs et de stress"** : ne provient pas directement d'un insight Chapeau explicite en Phase 1 ; il est hérité de la carte d'empathie S1 (pain "no reliable sales tracking, everything on paper"). À valider explicitement lors des tests terrain S3 — aucune Hypothèse dédiée ne le couvre encore directement, ce qui est un angle mort à surveiller.

## Synthèse de Cohérence
**Alignement:** Fort — la quasi-totalité des Jobs, Pains et Gains du profil client, ainsi que tous les Relievers et Creators de la proposition de valeur, se rattachent directement à un insight des 6 Chapeaux.
**Tension principale:** Le risque de coupure WiFi (Chapeau Noir) entre en tension avec l'hypothèse d'une synchronisation "temps réel" (Chapeau Vert / Gain Creators) — cette tension est résolue par le choix architectural "offline-first" (file d'attente locale), mais reste le point le plus fragile du MVP.
**Recommandation avant S3:** Valider en priorité l'architecture offline-first (Hypothèse C2) avant tout autre développement, car c'est l'élément qui réconcilie la promesse de "temps réel" avec la réalité du terrain à Point E.
