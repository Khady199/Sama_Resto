## 1. Contraintes MVP
 
### Persona
Aïda · 34 ans · Gérante de fast-food · Point E, Dakar · Smartphone + Wave/Orange Money
 
### Contraintes Non Négociables
 
**Contrainte 1**
- **Critère :** Le MVP DOIT fonctionner sur des tablettes Android grand public (pas de dépendance à du matériel premium type iPad)
- **Origine :** Chapeau Blanc (coût tablette 60 000–120 000 FCFA, marges serrées)
- **Élimine :** Toute pile technologique exclusive à iOS, exigence de matériel haut de gamme, ou licence par appareil supposant des tablettes premium
**Contrainte 2**
- **Critère :** Le MVP DOIT mettre les commandes en file d'attente localement et les synchroniser automatiquement à la reconnexion WiFi (hors-ligne d'abord, sans dépendance exclusive au cloud)
- **Origine :** Chapeau Noir (coupures WiFi pendant le rush → commandes disparaissant si tout-cloud)
- **Élimine :** Architecture entièrement cloud en temps réel ; toute conception où une connexion perdue entraîne une perte silencieuse de commande
**Contrainte 3**
- **Critère :** Le MVP NE DOIT PAS nécessiter une formation du personnel de plus de 30 minutes (aucune aisance technique préalable supposée)
- **Origine :** Chapeau Noir (risque d'adoption du personnel, Aïda n'a pas le temps pour un onboarding long)
- **Élimine :** Flux de configuration multi-écrans, panneaux d'administration, ou tout workflow nécessitant plus de quelques appuis pour passer/mettre à jour une commande
**Contrainte 4**
- **Critère :** Le MVP DOIT intégrer Wave/Orange Money comme réalité de paiement (pas une passerelle de paiement générique ou étrangère)
- **Origine :** Chapeau Blanc (Wave/Orange Money dominent les paiements quotidiens au Sénégal)
- **Élimine :** Un paiement uniquement par carte bancaire, des processeurs de paiement étrangers, ou tout périmètre MVP qui reporte le mobile money local à une « phase 2 »
### Fonctionnalités Éliminées
- **Architecture de synchronisation temps réel tout-cloud** → éliminée car la Contrainte 2 exige une file d'attente locale et une résilience hors-ligne ; une dépendance cloud pure réintroduit exactement le risque (commandes perdues) que le MVP doit éliminer.
- **Écrans avancés de configuration personnel/admin** (rôles, permissions, paramètres multi-succursales) → éliminés car la Contrainte 3 plafonne la formation à 30 minutes ; toute complexité de configuration au-delà de la saisie de commande basique et du marquage de statut viole ce plafond.
- **Intégration d'une passerelle de paiement étrangère/carte bancaire** → éliminée car la Contrainte 4 exige Wave/Orange Money comme couche de paiement dès le premier jour, pas en option secondaire.
- **Fonctionnalités dépendant de matériel premium** (ex : workflows NFC uniquement nécessitant des modèles iPad spécifiques) → éliminées car la Contrainte 1 impose la compatibilité avec des tablettes Android grand public.
### Critère de Validation Final
Le MVP est valide si et seulement si : Aïda peut traiter un service de midi en coup de feu (50 à 100 commandes sur 2 heures) sans aucune commande perdue ou dupliquée, en utilisant uniquement les fonctionnalités du MVP, avec son personnel formé en moins de 30 minutes, sur une tablette Android grand public, et en se rétablissant proprement d'au moins une coupure WiFi pendant le test.