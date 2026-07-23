# 6 Chapeaux de Bono — SamaResto S2

## Contexte: Les 3 HMW
1. Comment pourrions-nous faire en sorte que chaque commande arrive en cuisine instantanément et sans erreur, même pendant le coup de feu ?
2. Comment pourrions-nous réduire le temps d'attente perçu par les clients tout en gardant un service au comptoir fluide ?
3. Comment pourrions-nous donner à Aïda des relevés de ventes clairs et fiables, sans effort supplémentaire ?

---

## 🤍 Chapeau Blanc — Faits & Données
- À Point E, le rush de midi (12h-14h) concentre 50 à 100 commandes en 2 heures chez Aïda ; aujourd'hui tout transite par bons papier écrits à la main entre caisse et cuisine, un mode qui échoue visiblement dès que le volume dépasse le rythme d'un seul poste (HMW1).
- Le WiFi à Point E est partagé et instable aux heures de pointe (coupures fréquentes en journée), les tablettes commodity coûtent 60 000 à 120 000 FCFA et doivent survivre à la chaleur, aux mains grasses et aux chocs en cuisine ; l'imprimante de reçus, quand elle existe, est souvent un modèle bas de gamme sujet aux bourrages (HMW1, HMW3).
- Les concurrents mieux capitalisés (chaînes internationales) utilisent déjà des caisses digitales, alors que la majorité des fast-foods indépendants dakarois restent au papier ; Wave et Orange Money dominent les paiements du quotidien à Dakar et sont désormais une attente client implicite, pas une option (HMW3).

## ❤️ Chapeau Rouge — Émotions & Intuitions
- Pendant le coup de feu, Aïda ressent une tension entre la fierté de garder le contrôle de son commerce et une anxiété réelle de perdre une commande ou un client sans s'en rendre compte (HMW1).
- Ses 2-3 employés vivent le rush comme une source de stress et de frustration quand les commandes orales ou les bouts de papier se contredisent ; à l'inverse, un système clair leur donnerait un sentiment d'ordre et de compétence (HMW1, HMW2).
- Les clients ressentent de l'impatience et un doute croissant ("ma commande a-t-elle été prise ?") pendant l'attente silencieuse ; un simple signal de progression suffirait à transformer cette anxiété en confiance (HMW2).

## 🖤 Chapeau Noir — Risques & Critique
- Une coupure WiFi pendant le rush peut faire disparaître ou bloquer des commandes en cours si le système dépend entièrement du cloud, sans plan de repli local (HMW1).
- Les employés, peu familiers avec la technologie, peuvent résister à un nouvel outil par méfiance ou manque de temps pour se former, surtout si l'interface est complexe (HMW1, HMW2).
- Les données de ventes stockées numériquement posent une question de confidentialité et de sécurité (accès non autorisé, perte de l'historique) ; par ailleurs, le coût d'un tel système peut peser lourd sur les marges serrées d'Aïda, et une tablette volée, cassée ou en panne pendant le rush paralyserait le service (HMW1, HMW3).

## 💛 Chapeau Jaune — Optimisme & Valeur
- Aïda gagne une visibilité instantanée sur l'état de chaque commande : plus de commandes perdues, un contrôle retrouvé même en pleine cohue (HMW1).
- Les employés se sentent responsabilisés par des commandes écrites et claires, réduisant les cris et la confusion en cuisine, ce qui améliore l'ambiance de travail (HMW1, HMW2).
- Les clients perçoivent une attente plus courte grâce à des mises à jour de statut visibles, et en fin de journée Aïda dispose d'un rapport de ventes instantané qui lui donne une meilleure lecture de sa trésorerie sans saisie manuelle (HMW2, HMW3).

## 💚 Chapeau Vert — Créativité & Idées
- Et si le système fonctionnait en mode "offline-first", mettant les commandes en file d'attente locale puis les synchronisant automatiquement dès le retour du WiFi ? (HMW1)
- Et si l'écran cuisine était complété par une alerte sonore ou visuelle simple (voix, LED) pour percer le bruit ambiant de la cuisine, en plus de l'affichage digital ? (HMW1, HMW2)
- Et si un mode SMS basique existait en secours pour un membre du personnel avec un téléphone simple, garantissant qu'aucune commande ne reste bloquée même sans smartphone ni tablette disponible ? (HMW1, HMW3)

## 💙 Chapeau Bleu — Processus & Organisation
- Le HMW1 (Rush Hour) est le plus critique à résoudre pour le MVP car il conditionne tout le reste : sans transmission fiable des commandes, ni la réduction du temps d'attente perçu (HMW2) ni un relevé de ventes fiable (HMW3) ne peuvent exister.
- Les deux risques prioritaires venus du Chapeau Noir sont la résilience hors-ligne (WiFi) et l'adoption par le personnel (formation, confiance) : les deux doivent être traités dès la conception du MVP, pas après coup.
- Le périmètre minimal viable se limite à la synchronisation instantanée caisse→cuisine avec file d'attente locale en cas de coupure, et un affichage de statut simple — tout le reste (rapports avancés, SMS client, etc.) peut attendre.

## 🔵 Synthèse Chapeau Bleu

**HMW révisé ou confirmé:**
Comment pourrions-nous garantir que chaque commande circule instantanément et de façon fiable de la caisse à la cuisine — même quand le WiFi tombe ou que le personnel n'est pas formé — pour qu'Aïda garde le contrôle pendant le rush, avec des données de ventes fiables comme conséquence naturelle ?

**Risques prioritaires:**
[Risque 1 — Résilience WiFi/Hors-ligne] / [Risque 2 — Adoption par le personnel]

**Question ouverte pour S3:**
Une file d'attente de commandes hors-ligne (stockage local + synchronisation à la reconnexion) peut-elle être construite avec Bolt.new + Dify dans le délai de S3, et l'équipe d'Aïda peut-elle être formée à l'utiliser en moins de 30 minutes ?
