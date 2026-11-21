# SimCoach — Jeff, ton coach de pilotage (ACC, Le Mans Ultimate, F1 25)

Jeff est un ingénieur de piste qui tourne **sur ton PC**. Il lit la télémétrie du jeu en direct, analyse
chaque virage (freinage, corde, remise des gaz, sortie), te compare à ton meilleur tour et aux IA, propose
des réglages pendant les essais libres, et **te parle à la radio uniquement dans les zones calmes**
(lignes droites, jamais au freinage).


## Installer

1. Télécharge **[SimCoach-Setup.exe](https://github.com/SimCoachDev/simcoach-releases/releases/download/lanceur/SimCoach-Setup.exe)** et lance-le.
2. Windows peut afficher « Windows a protégé votre ordinateur » (le programme n'est pas signé) :
   clique **Informations complémentaires → Exécuter quand même**.
3. Le lanceur installe tout dans ton dossier utilisateur (aucun droit administrateur), crée les raccourcis
   **SimCoach** sur le Bureau et dans le menu Démarrer, puis télécharge ce qu'il faut pour ton PC :
   - le programme (environ 200 Mo) ;
   - la voix de Jeff et la reconnaissance vocale ;
   - avec une **carte NVIDIA** : la reconnaissance vocale précise sur la carte graphique (environ 3 Go en tout) ;
     sans carte NVIDIA : une version plus légère sur le processeur.
4. Ensuite, lance toujours SimCoach par le raccourci. **Les mises à jour sont automatiques** : à chaque
   lancement, le lanceur vérifie s'il y a une nouvelle version et ne télécharge que ce qui a changé.
   Sans Internet, la version installée démarre normalement.

Configuration conseillée : Windows 10 ou 11, un casque avec micro. Une carte NVIDIA récente améliore la
compréhension des phrases libres, mais n'est pas obligatoire.

## Premier lancement

Un **assistant** s'ouvre dans la fenêtre de SimCoach :

1. **Micro** : choisis le micro de ton casque et clique *Tester* (parle 3 secondes) : Jeff te dit si le niveau est bon.
2. **Voix de Jeff** : choisis une voix (les voix « en ligne » sont les plus naturelles, « Tom » marche sans Internet)
   et le volume, puis *Écouter Jeff*. Si le jeu couvre sa voix, monte le volume.
3. **Volant et pédalier** : la marque de ton volant (Fanatec, Logitech, Thrustmaster, Moza, Simucube, Simagic…) et ton type de pédale de frein (load cell ou classique, comme sur un G29) : les conseils de freinage parlent de ton matériel et du bon logiciel. En option, un bouton du volant pour changer d'onglet.
4. **Jeux** : ce que Jeff trouve sur ton PC (jeux, dossiers de setups).

Tu peux rouvrir l'assistant à tout moment : onglet **AFFICHAGE → Assistant de configuration**.

## Préparer les jeux

| Jeu | À faire |
|---|---|
| **Assetto Corsa Competizione** | Rien. Au premier lancement, SimCoach active l'**API de diffusion** d'ACC (fichier `broadcasting.json`) pour enregistrer les tours des IA. **Relance ACC une fois** après le premier lancement de SimCoach : ACC lit ce réglage au démarrage. La pastille « IA ACC : connectée » apparaît en bas de l'écran. |
| **Le Mans Ultimate** | Rien : SimCoach lit la mémoire partagée du jeu. |
| **F1 25** | Dans le jeu : *Réglages → Télémétrie* : UDP **activé**, port **20777**, format **2025**, fréquence **60 Hz**. |

Lance SimCoach avant ou après le jeu, peu importe : Jeff se connecte tout seul, annonce la voiture et le
circuit, puis commence à analyser dès le premier tour complet.

## Ce que fait Jeff pendant que tu roules

- **Après chaque virage important** : l'écart avec ta référence et *le* conseil le plus rentable.
- **En fin de tour** : ton temps, l'écart à ton meilleur, ton **tour idéal** (somme de tes meilleurs virages).
- **Tous les 3 tours**, il propose un **point complet** (réponds « oui » ou « non »). Au stand, le point est automatique.
- **Références** : ton meilleur tour, ton record sur ce circuit et cette voiture, et les **IA** de ta catégorie
  (leurs tours sont enregistrés pendant tes séances avec IA).
- **Incidents** : tête-à-queue et grosses glisses sont expliqués (pilotage ou voiture), et le tour est écarté des analyses.
- **Ingénieur de setup** (essais libres) : quand un problème se répète, Jeff t'appelle au box et écrit un fichier
  de réglages **Jeff_01, Jeff_02…** à côté de ton setup dans le jeu. Charge-le, fais quelques tours, et dis-lui
  si c'est mieux.
- **Course** : rythme, régularité, carburant, pneus.
- **Fin de séance** : le débrief complet s'ouvre dans ton navigateur (et dans l'onglet BILAN).

## Parler à Jeff

Commence chaque phrase par **« Jeff »** (il comprend aussi « Jef », toujours, et « Chef »). Deux façons de
l'appeler, au choix :
- **d'une traite** : « Jeff, virage trois » ;
- **avec un temps d'arrêt** : « Jeff »… (il se tait, le tableau de bord affiche « Jeff t'écoute… »), puis ta
  demande dans les **7 secondes**, sans répéter son nom.

Un **bip radio** (deux tons courts, façon radio d'équipe à la télé) confirme qu'il t'écoute : à l'appel et
quand tu lui coupes la parole, dans ton casque, sur la même sortie que sa voix. Pour le couper :
`"wake_sound": false` dans `voice_input` de `config.json` (volume : `"wake_sound_volume"`, de 0 à 1).

S'il parle, dis « Jeff » pour lui couper la parole, ou « stop » pour qu'il se taise. Tout reste sur ton PC : aucun son n'est envoyé sur Internet.

**Infos sur ton tour**

| Tu dis « Jeff, … » | Jeff répond |
|---|---|
| répète · pardon | le dernier message |
| chrono · dernier tour · mon temps | ton dernier temps et l'écart |
| écart · delta · mon meilleur · tour idéal | meilleur tour, tour idéal, temps à gagner |
| virage 3 (ou virage trois) | l'écart et la consigne pour ce virage |
| conseil · où je perds · comment progresser | la priorité du moment |
| comparaison · référence · plus rapide | où tu perds le plus face à la référence |
| comment fait l'IA au virage 5 | comment la référence passe ce virage, par rapport à tes repères |
| comment prendre le virage 4 | la méthode pour ce virage (type, corde, vibreurs) |
| vibreurs · vibreur virage 2 | ton usage des vibreurs |
| pourquoi · pourquoi j'ai fait un tête-à-queue · qu'est-ce qui s'est passé au virage 9 | l'explication de ta dernière erreur |
| pneus · pressions | pressions et températures |
| essence · carburant · conso | carburant, consommation, tours restants |
| sorties | tes sorties de piste |
| objectif · palier · mon niveau | ton niveau et le prochain objectif de chrono |
| détail · point complet · débrief | le point complet |
| récap · bilan | le récapitulatif de ce circuit |
| mes réglages · répartiteur · antipatinage | les réglages au volant lus dans le jeu |

**Coaching**

| Tu dis « Jeff, … » | Effet |
|---|---|
| guide-moi · coaching · annonce les virages | il annonce chaque virage juste avant, avec la consigne |
| arrête le guide · stop coaching | fin du guide |
| ménage les pneus · économise le carburant | où gagner, ce que ça coûte |
| sous-virage · survirage · traction · mieux freiner · je bloque | la cause probable et le remède |
| explique le freinage · explique le sous-virage · explique la trajectoire… | l'explication du principe |
| question | il écoute une phrase libre pendant 8 secondes |

**Ton ressenti** (Jeff s'en sert pour les réglages) : décris ce que fait la voiture, avec le virage si tu peux.
Exemples : « Jeff, **l'arrière bloque au freinage virage 5** », « Jeff, **la voiture glisse à l'accélération au virage 3** »,
« Jeff, **ça sous-vire en entrée** », « Jeff, **ça patine en sortie** ».

**Réglages (essais libres)**

| Tu dis « Jeff, … » | Effet |
|---|---|
| setup · réglages | les conseils de réglage du moment |
| règle la voiture · propose un setup | il prépare un nouveau setup (fichier Jeff_NN) |
| qu'est-ce qui manque à la voiture · le setup est optimal ? | ta voiture face à la plus rapide de ta catégorie |
| setup agressif · setup doux · setup automatique | gros changements, un cran à la fois, ou selon la situation |
| il est prêt le setup ? · où en est le setup · ça avance le setup ? | combien de tours propres il lui faut encore |
| charge le setup · donne-moi le setup (même pas fini) | il écrit le setup tout de suite avec ce qu'il sait déjà, même après un ou deux tours |
| mieux · pareil · moins bien | ton avis après quelques tours avec un nouveau setup |
| la voiture · le vibreur | ta réponse quand il demande la cause d'un incident |

**L'application s'adapte à ton écran** : elle est dessinée pour 1920×1080 en plein écran et grandit
avec l'écran (×1,33 en 1440p, ×2 en 4K). Sur un écran ultrawide (3440×1440), un rail fixe à droite garde
le circuit, la radio de Jeff et le chrono visibles sur tous les onglets.

**Télémétrie détaillée (ACC et LMU)** : Jeff lit aussi le débattement des suspensions, la charge et le
carrossage de chaque pneu, la température à cœur, la position au classement ; sur LMU en plus l'appui aéro
avant / arrière, les 3es éléments et la largeur exacte de la piste (sorties mesurées au centimètre).
L'onglet SETUP montre le débattement utilisé et l'histogramme des amortisseurs (compression / détente,
lente / rapide) ; l'ingénieur s'en sert pour les butées, la compression rapide et la plateforme.
La vue « Châssis » ajoute le transfert de charge (l'avant pousse ou l'arrière est vif), la roue intérieure
qui se déleste, le roulis et la plongée au freinage, l'essieu sur lequel l'ABS travaille, la glisse des
pneus (LMU), les passages de rapports, l'adhérence de la piste et le vent : l'ingénieur en tire des
réglages (barres, répartiteur, compression lente) et confirme ou non le sous-virage mesuré.

**Passages de rapports (v0.34)** : Jeff compare la poussée de la voiture juste avant et juste après chaque
montée de rapport, à fond et à la même vitesse. Si le rapport suivant pousse nettement plus fort, tu passes
trop tard ; s'il pousse nettement moins fort alors qu'il restait de la marge avant le rupteur, trop tôt.
Il repère aussi le rupteur au même endroit tour après tour et les rétrogradages en sur-régime (si le jeu
publie le régime maxi : ACC, LMU). Une consigne à la radio tous les 3 tours (`coach.shifting_every_laps`),
le détail dans le débrief (section « Passages de rapports »).

**Comparer tes tours (onglet TARGET)**

Tu essaies une autre trajectoire ou un autre freinage ? L'onglet TARGET montre deux tours côte à côte
(par défaut ton dernier tour contre ton meilleur) : les deux trajectoires sur le circuit, les points de
freinage, la vitesse à la corde, et sur le tour B, en vert là où tu gagnes du temps et en rouge là où tu
en perds. Choisis les tours et la zone (tour, secteur, virage) en haut de l'onglet.

| Tu dis « Jeff, … » | Effet |
|---|---|
| regarde les tours · qu'est-ce qui a changé | ton dernier tour contre ton meilleur, sur tout le tour |
| regarde le secteur 1 | zoom sur le secteur, et ce qui a changé à la radio |
| regarde le virage 5 | zoom sur le virage : freinage, corde, sortie, trajectoire |
| compare le tour 5 et le tour 7 | ces deux tours-là |

Quand tu le demandes, Jeff **montre** : le circuit A s'agrandit et zoome sur le freinage du virage qui compte,
puis le circuit B passe en grand avec les courbes de frein des deux tours. Un clic ou Échap arrête l'animation.
Chaque panneau de l'application s'agrandit d'un **double-clic** (ou bouton ⤢ en haut à droite) ; Échap le referme.

**Largeur de piste et sorties** : avec les positions exactes du jeu (ACC, LMU), Jeff apprend la largeur que tu
utilises et le vrai bord là où tes roues sont sorties. Les cartes montrent la piste avec sa largeur, une croix
rouge à chaque sortie, et Jeff dit de combien tu es passé plus large que sur tes tours propres. Une limite de
piste effleurée (sortie légère) compte pour moitié dans le mode reconstruction. Côté setup, les passages hors
piste ne faussent plus la mesure d'équilibre, et des sorties larges répétées à la remise des gaz renforcent un
sous-virage en sortie mesuré, sinon Jeff te dit que c'est le pilotage.

**Séance et radio**

| Tu dis « Jeff, … » | Effet |
|---|---|
| box (je rentre ce tour) · box box (tout de suite) · stand | prévient Jeff que tu rentres |
| pas de briefing au box | pas de point complet au stand |
| essais · qualif · course | change le mode de séance (normalement détecté tout seul) |
| silence · tais-toi · chut · reprends | coupe / rétablit la radio |
| moins · encore moins · plus | règle la quantité de messages |
| stop · arrête · ça suffit | coupe la phrase en cours |
| oui · non · plus tard | réponse à ses questions |

**Affichage**

| Tu dis « Jeff, … » | Effet |
|---|---|
| onglet tour · onglet virages · onglet cible · rythme · onglet setup · onglet comparer · affichage | change d'onglet |
| affichage normal · onglet live | retour à l'écran principal |
| affichage bandeau · affichage module · coupe l'affichage | affichage par-dessus le jeu (jeu en plein écran fenêtré) |
| assigne un bouton | apprend un bouton du volant pour changer d'onglet |

## Le tableau de bord

La fenêtre SimCoach affiche le tableau de bord. Tu peux aussi l'ouvrir **sur ton téléphone** (même Wi-Fi) :
l'adresse est affichée en bas à droite.

| Onglet | Contenu |
|---|---|
| **LIVE** | delta en direct, tour en cours, derniers tours, pneus, freins, carburant, dernier message de Jeff |
| **TOUR** | ton tour comparé à la référence (vitesse, frein, gaz) |
| **VIRAGES** | chaque virage : écart, type, consigne, vibreurs |
| **TARGET** | carte du circuit colorée selon le temps perdu ou gagné, objectifs de chrono |
| **RYTHME** | régularité, tendance, carburant, stratégie |
| **SETUP** | diagnostic de l'ingénieur, réglages proposés, essais de setups |
| **COMPARER** | tes courbes superposées à celles de la référence |
| **AFFICHAGE** | affichage par-dessus le jeu, messages de Jeff à couper ou garder, **journal de Jeff**, assistant de configuration |

En bas de l'écran : *Point détaillé*, *Répéter*, *Objectif*, *Récap*, *Terminer la session* ; à la fin de la
séance : *Nouvelle session*, *Ouvrir le débrief*, *Quitter*. Les informations importantes (connexion au jeu,
nouvelles références IA, incidents, erreurs) apparaissent aussi en notification en bas à droite.

## Tes données

Tout reste sur ton PC, dans `%LOCALAPPDATA%\SimCoach` : tes tours, records, enregistrements de séances,
références des IA, cartes de circuits, journal de setups et réglages (`config.json`). Rien n'est envoyé sur
Internet (seules les voix « en ligne » transmettent le texte que Jeff prononce au service de synthèse vocale ;
choisis « Tom » pour tout garder en local). Les mises à jour ne touchent jamais à tes données.

## Dépannage

| Problème | Solution |
|---|---|
| Jeff ne m'entend pas | AFFICHAGE → Assistant → Micro → *Tester*. Vérifie le volume du micro dans Windows (*Paramètres → Son*). Commence bien par « Jeff ». |
| Je n'entends pas Jeff | Assistant → Voix → *Écouter Jeff*, monte le volume. Vérifie la sortie audio de Windows. |
| Le jeu n'est pas détecté | Lance une séance (pas seulement le menu). F1 25 : vérifie les réglages UDP. Le panneau « Avant de rouler » indique ce qui manque. |
| Pas de pastille « IA ACC » | Relance ACC une fois après le premier lancement de SimCoach. |
| Une mise à jour a échoué | Relance SimCoach : le téléchargement reprend où il s'était arrêté. Si une nouvelle version ne démarre pas, le lanceur revient tout seul à la précédente. |
| SimCoach se ferme tout seul, ou « Programme introuvable » | L'antivirus (Windows Defender) a sans doute supprimé un fichier de SimCoach. Relance SimCoach : le fichier manquant est retéléchargé. Si ça recommence : *Sécurité Windows → Protection contre les virus → Historique de protection* → **Restaurer**, puis ajoute le dossier `%LOCALAPPDATA%\SimCoach` aux exclusions. |
| L'affichage par-dessus le jeu n'apparaît pas | Mets le jeu en *plein écran fenêtré* ou *fenêtré sans bordure* (Windows n'affiche rien au-dessus du plein écran exclusif). |

Le **journal de Jeff** (onglet AFFICHAGE) montre tout ce que fait le programme : utile pour comprendre un problème.

## IA (facultatif)

Une IA peut répondre aux questions que Jeff ne connaît pas (« Jeff, question… ») et écrire le débrief de fin
de séance. Assistant → étape **IA** : choisis le fournisseur, puis *Enregistrer* et *Tester*.

- **Ollama** (gratuit, sur ton PC) : installe [Ollama](https://ollama.com), puis dans un terminal
  `ollama pull qwen2.5:7b` (ou un modèle qui tient dans ta carte graphique).
- **Claude** (Anthropic) : colle ta clé API ([console.anthropic.com](https://console.anthropic.com)).
- **Autre fournisseur compatible OpenAI** (OpenAI, Mistral, OpenRouter, LM Studio…) : adresse de l'API,
  nom du modèle et clé.

La clé reste sur ton PC. Avec un fournisseur en ligne, chaque question est facturée par lui.

## Désinstaller

Supprime le dossier `%LOCALAPPDATA%\SimCoach` (colle ce chemin dans la barre d'adresse de l'Explorateur) et
les raccourcis SimCoach du Bureau et du menu Démarrer. Pour garder tes données, copie d'abord le dossier `data`.

## Licence

**Utilisation gratuite, tous droits réservés.** Tu peux télécharger et utiliser SimCoach gratuitement
depuis cette page. Toute reproduction, redistribution, modification ou revente, totale ou partielle, est
interdite sans l'accord de l'auteur : pour faire découvrir SimCoach, partage le lien de cette page plutôt
que les fichiers. Les composants libres utilisés (Python, pygame-ce, Vosk, Piper, Whisper…) restent sous
leur propre licence. Texte complet : [LICENSE](LICENSE).

© 2026 SimCoachDev
