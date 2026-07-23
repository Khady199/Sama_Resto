# Métriques de Succès — SamaResto

## MVP (Description Brève)
Synchronisation en temps réel des commandes de la tablette caisse vers la tablette cuisine, avec résilience hors-ligne (file d'attente locale + synchronisation automatique) et rapport de ventes de fin de journée généré sans saisie manuelle.

## ⭐ Métrique Nord
**Indicateur:** % des commandes qui arrivent en cuisine correctement dès la première transmission (sans perte ni doublon)
**Valeur cible à 30 jours:** 95% ou plus
**Comment mesurer:** Comptage quotidien manuel — commandes saisies à la caisse comparées aux commandes reçues/traitées en cuisine.

## 📈 Métriques de Progression

### Métrique P1
**Indicateur:** Nombre d'employés formés et utilisant activement le système
**Valeur cible à 30 jours:** 3/3 (équipe complète d'Aïda)
**Comment mesurer:** Observation quotidienne + liste de contrôle simple tenue par Aïda.

### Métrique P2
**Indicateur:** Temps moyen entre la saisie de la commande à la caisse et son affichage en cuisine
**Valeur cible à 30 jours:** Moins de 10 secondes
**Comment mesurer:** Chronométrage manuel sur un échantillon de 5 commandes par jour.

### Métrique P3
**Indicateur:** Niveau de stress perçu par Aïda pendant le rush
**Valeur cible à 30 jours:** Nettement plus bas qu'avec le papier (amélioration déclarée)
**Comment mesurer:** Échange hebdomadaire avec Aïda, auto-évaluation sur une échelle de 1 à 5.

## 🚨 Métriques d'Alerte

### Alerte A1
**Signal:** Coupures WiFi cumulées dépassant 2 heures par jour
**Seuil:** Dès qu'un seul jour dépasse ce seuil
**Action corrective:** Prioriser en urgence le renforcement de la résilience hors-ligne (file d'attente locale) avant de poursuivre le reste du build.

### Alerte A2
**Signal:** Moins de 2 employés sur 3 utilisant activement le système au jour 15
**Seuil:** Dès que ce seuil est atteint à mi-parcours du pilote
**Action corrective:** Mener des entretiens rapides avec le personnel, identifier le point de friction et adapter l'interface avant de continuer.

## Tableau de Bord S6 (Démo au Jury)
Nous présenterons ces 3 chiffres :
1. **Métrique Nord:** [valeur réelle] vs [cible 95%] ✅/❌
2. **Métrique P1:** [valeur réelle] vs [cible 3/3] ✅/❌
3. **Alerte A1:** [déclenchée ou non] ⚠️/✅
