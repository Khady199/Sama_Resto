# Contraintes MVP — SamaResto

## Persona
Aïda · 34 · Fast-food Manager · Point E, Dakar · feature phone + Wave

## Contraintes Non Négociables

### Contrainte 1
**Critère:** Le MVP DOIT fonctionner sur des tablettes Android grand public (pas de dépendance à du matériel premium type iPad)
**Origine:** Chapeau Blanc (tablet cost 60 000–120 000 FCFA, tight margins)
**Élimine:** Any iOS-exclusive stack, high-end hardware requirement, or per-device licensing that assumes premium tablets

### Contrainte 2
**Critère:** Le MVP DOIT mettre les commandes en file d'attente localement et les synchroniser automatiquement à la reconnexion WiFi (hors-ligne d'abord, sans dépendance exclusive au cloud)
**Origine:** Chapeau Noir (WiFi cuts during rush → orders disappear if cloud-only)
**Élimine:** Real-time-cloud-only architecture; any design where a dropped connection causes silent order loss

### Contrainte 3
**Critère:** Le MVP NE DOIT PAS nécessiter une formation du personnel de plus de 30 minutes (aucune aisance technique préalable supposée)
**Origine:** Chapeau Noir (staff adoption risk, Aïda has no time to run extended onboarding)
**Élimine:** Multi-screen configuration flows, admin panels, or any workflow requiring more than a handful of taps to place/update an order

### Contrainte 4
**Critère:** Le MVP DOIT intégrer Wave/Orange Money comme réalité de paiement (pas une passerelle de paiement générique ou étrangère)
**Origine:** Chapeau Blanc (Wave/Orange Money dominate Senegal's daily payments)
**Élimine:** Credit-card-only checkout, foreign payment processors, or any MVP scope that defers local mobile money to "phase 2"

## Fonctionnalités Éliminées
- Cloud-only real-time sync architecture → eliminated because Contrainte 2 requires local queuing and offline resilience; a pure cloud dependency reintroduces the exact risk (lost orders) the MVP exists to remove.
- Advanced staff/admin configuration screens (roles, permissions, multi-branch settings) → eliminated because Contrainte 3 caps training at 30 minutes; any setup complexity beyond basic order entry and status marking violates that ceiling.
- Foreign/credit-card payment gateway integration → eliminated because Contrainte 4 requires Wave/Orange Money as the day-1 payment layer, not an add-on.
- Premium-hardware-dependent features (e.g., NFC-only workflows requiring specific iPad models) → eliminated because Contrainte 1 mandates commodity Android tablet compatibility.

## Critère de Validation Final
Le MVP est valide si et seulement si : Aïda peut traiter un service de midi en coup de feu (50 à 100 commandes sur 2 heures) sans aucune commande perdue ou dupliquée, en utilisant uniquement les fonctionnalités du MVP, avec son personnel formé en moins de 30 minutes, sur une tablette Android grand public, et en se rétablissant proprement d'au moins une coupure WiFi pendant le test.
