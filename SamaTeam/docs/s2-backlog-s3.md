# Backlog S3 — SamaResto

## HMW Définitif (Draft)
Comment pourrions-nous garantir que chaque commande circule instantanément et de façon fiable de la caisse à la cuisine — même quand le WiFi tombe ou que le personnel n'est pas formé — pour qu'Aïda garde le contrôle pendant le rush, avec des données de ventes fiables comme conséquence naturelle ?

## User Stories MUST
*(À construire en S3 pour le MVP)*

### US-01
**Story:** En tant que caissier(ère), je veux saisir une nouvelle commande sur la tablette afin qu'elle arrive instantanément sur la tablette cuisine.
**Priorité:** MUST
**Outil:** Bolt.new (interface) + Dify (agent de dispatch de commande)
**Effort:** medium
**Adresse:** Pain Reliever "transmission digitale instantanée, zéro papier"
**Critère d'acceptation:** La commande s'affiche sur la tablette cuisine en moins de 5 secondes après sa saisie à la caisse.

### US-02
**Story:** En tant que membre de l'équipe cuisine, je veux marquer une commande "en cours" ou "prête" sur la tablette cuisine afin que la caisse voie l'état en temps réel.
**Priorité:** MUST
**Outil:** Bolt.new + machine à états Dify
**Effort:** low
**Adresse:** Gain Creator "statut visible sur les deux tablettes"
**Critère d'acceptation:** Le changement de statut est visible côté caisse en moins de 2 secondes.

### US-03
**Story:** En tant qu'Aïda, je veux que les commandes saisies pendant une coupure WiFi soient mises en file d'attente localement et se synchronisent automatiquement au retour du réseau, afin de ne jamais perdre de commande.
**Priorité:** MUST
**Outil:** Stockage local (tablette) + logique de synchronisation Dify au reconnect
**Effort:** high
**Adresse:** Contrainte 2 (offline-first) et Hypothèse C2 (résilience WiFi)
**Critère d'acceptation:** Lors d'une coupure WiFi simulée, 100% des commandes saisies pendant la coupure apparaissent en cuisine après reconnexion, sans doublon.

### US-04
**Story:** En tant que caissier(ère), je veux encaisser via Wave/Orange Money et imprimer automatiquement le reçu, afin de coller à la réalité de paiement d'Aïda.
**Priorité:** MUST
**Outil:** API Wave/Orange Money + pilote d'impression
**Effort:** medium
**Adresse:** Contrainte 4 (intégration paiement local)
**Critère d'acceptation:** Le paiement est confirmé et le reçu s'imprime en moins de 3 secondes après validation de la commande.

## User Stories SHOULD
*(À construire si le temps le permet)*

### US-05
**Story:** En tant qu'Aïda, je veux qu'un rapport de ventes se génère automatiquement en fin de journée, afin de réconcilier ma caisse sans saisie manuelle.
**Priorité:** SHOULD
**Outil:** Agent de rapport Dify + export CSV
**Effort:** medium
**Adresse:** Gain Creator "génération automatique du rapport de fin de journée"
**Critère d'acceptation:** Le rapport est disponible en fin de service et correspond exactement aux commandes réellement passées.

### US-06
**Story:** En tant que client, je veux être informé quand ma commande est prête (affichage ou SMS), afin de réduire mon impatience pendant l'attente.
**Priorité:** SHOULD
**Outil:** Bolt.new (écran d'affichage) + API SMS optionnelle
**Effort:** medium
**Adresse:** Pain Reliever "statut de commande partagé" côté client, Hypothèse I1
**Critère d'acceptation:** Le statut "prêt" est visible ou notifié au client en moins de 5 secondes après le marquage en cuisine.

## User Stories COULD
*(Roadmap post-MVP, S6+)*

### US-07
**Story:** En tant que membre de l'équipe cuisine, je veux une alerte sonore ou visuelle (voix, LED) en plus de l'affichage digital, afin de percevoir les nouvelles commandes malgré le bruit de la cuisine.
**Priorité:** COULD
**Outil:** Bolt.new + module audio/LED
**Effort:** medium
**Adresse:** Chapeau Vert — idée d'alertes multi-modales

### US-08
**Story:** En tant que membre du personnel sans tablette disponible, je veux recevoir les commandes critiques par SMS, afin de ne jamais être bloqué en cas d'indisponibilité matérielle.
**Priorité:** COULD
**Outil:** API SMS + Dify
**Effort:** medium
**Adresse:** Hypothèse S1 (mode SMS de secours, à confirmer par observation terrain)

## Sprint S3 Plan
**Semaine 1:** US-01 + US-02 — synchronisation de base et statut en temps réel entre caisse et cuisine.
**Semaine 2:** US-03 (file d'attente hors-ligne + sync) — priorité absolue vu le risque WiFi — puis US-04 (paiement/reçu) si US-03 est stabilisée.
**Semaine 3:** US-05 et/ou US-06 si le temps le permet, plus tests terrain et validation des hypothèses critiques.
**Démo S6:** US-01 + US-02 + US-03 démontrées en direct, avec une coupure WiFi simulée pour prouver la résilience hors-ligne devant le jury.
