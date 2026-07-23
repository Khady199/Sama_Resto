# Hypothèses de Validation — SamaResto

## HMW Définitif (Draft)
Comment pourrions-nous garantir que chaque commande circule instantanément et de façon fiable de la caisse à la cuisine — même quand le WiFi tombe ou que le personnel n'est pas formé — pour qu'Aïda garde le contrôle pendant le rush, avec des données de ventes fiables comme conséquence naturelle ?

## Hypothèses CRITIQUES
*(Si fausse → le MVP ne fonctionne pas, le projet s'arrête)*

### Hypothèse C1
**Affirmation:** Nous pensons qu'Aïda peut former ses 2-3 employés à la saisie de commandes sur tablette en moins de 30 minutes, sans expérience technique préalable.
**Indicateur:** Nous saurons si, après la session de formation, le personnel peut saisir 5 commandes consécutives sans assistance et sans erreur.
**Méthode:** Test terrain — session de formation chronométrée suivie d'un test de saisie supervisé.
**Qui valide:** Aïda et son personnel de caisse/cuisine.
**Délai S3:** Semaine 1.

### Hypothèse C2
**Affirmation:** Nous pensons que le système se rétablit correctement après une coupure WiFi : les commandes en cours sont mises en file d'attente localement et se synchronisent automatiquement au retour de la connexion, sans aucune perte.
**Indicateur:** Nous saurons si, lors d'une coupure simulée pendant le rush, 100% des commandes saisies pendant la coupure apparaissent en cuisine après reconnexion, sans doublon.
**Méthode:** Test terrain — simulation de coupure WiFi pendant un service, vérification manuelle des commandes avant/après.
**Qui valide:** Équipe SamaTeam + Aïda (observation conjointe).
**Délai S3:** Semaine 2.

### Hypothèse C3
**Affirmation:** Nous pensons que le personnel de cuisine adopte le système sans résistance majeure et le perçoit comme une aide, pas une contrainte.
**Indicateur:** Nous saurons si, après une semaine d'usage, le personnel utilise le système pour au moins 90% des commandes sans revenir au papier.
**Méthode:** Observation terrain + entretiens courts en fin de semaine 1.
**Qui valide:** Personnel de cuisine et de caisse.
**Délai S3:** Semaine 1.

## Hypothèses IMPORTANTES
*(Si fausse → l'expérience se dégrade mais le MVP fonctionne encore)*

### Hypothèse I1
**Affirmation:** Nous pensons que les clients perçoivent une attente plus courte grâce aux mises à jour de statut de commande.
**Indicateur:** Nous saurons si le score de satisfaction déclaré par les clients concernant le temps d'attente s'améliore par rapport à la situation avant le MVP.
**Méthode:** Sondage rapide auprès des clients pendant le pilote (avant/après).
**Qui valide:** Clients du point de vente.
**Délai S3:** Semaine 3.

### Hypothèse I2
**Affirmation:** Nous pensons que l'imprimante de reçus s'intègre correctement avec la tablette sans contournement manuel.
**Indicateur:** Nous saurons si l'impression du reçu se déclenche automatiquement et sans erreur pour au moins 95% des commandes testées.
**Méthode:** Test matériel direct dans le commerce d'Aïda avec l'imprimante réelle.
**Qui valide:** Équipe SamaTeam.
**Délai S3:** Semaine 2.

## Hypothèses SECONDAIRES
*(À valider après le MVP)*

### Hypothèse S1
**Affirmation:** Nous pensons qu'un mode SMS de secours serait utile pour un membre du personnel ne disposant pas de tablette ou de smartphone.
**Indicateur:** Nous saurons si ce besoin se manifeste réellement en observant si un membre du personnel se retrouve bloqué faute d'accès à une tablette pendant le pilote.
**Méthode:** Observation terrain pendant le pilote, sans développement dédié en S3.
**Qui valide:** Aïda et son équipe.
**Délai S3:** Semaine 3 (observation seulement, pas de build).

## Priorité de Validation S3
La première chose à tester en semaine 1 de S3 : organiser la session de formation de 30 minutes avec l'équipe d'Aïda et mesurer si elle peut saisir des commandes sans assistance (Hypothèse C1), en parallèle d'une première observation d'adoption par le personnel de cuisine (Hypothèse C3).
