---
# Projet : *Les Archives Miroirs* -Jeu narratif et de décryptage basé sur **Phaser 3**
---
### Mots-clés
`Phaser` · `Jeu narratif` · `IA et patrimoine` · `Décryptage` · `Data storytelling` · `Humanités numériques`

## Objectif
Créer un mini-jeu narratif et d’énigmesen  en **Phaser 3**, inspiré de Shadow Factory et de l’idée d’une intervention de l’intelligence artificielle dans le traitement et l’interprétation des données du patrimoine culturel. Sur le plan du but pédagogique, il s'agit d'apprendre les bases du développement interactif et expérimenter la narration autour du **patrimoine numérique et l’IA**.
Il explore la frontière entre : **mémoire et oubli**, **réalité et reconstitution**, **patrimoine culturel et intelligence artificielle**.  Le joueur devient ainsi le témoin d’une réflexion sur la manière dont les technologies numériques transforment notre rapport à la vérité historique et à la mémoire collective.

## Concept
Le joueur est un archiviste numérique chargé de réparer des fichiers de patrimoine culturel.  
Mais certains fichiers ont été “réécrits” par une IA.  
Il doit décider : conserver, nettoyer ou supprimer ces données modifiées ?

## Fonctionnalités
- Interface principale : clic sur les objets pour lire les descriptions  
- Mini-jeu de puzzle : reconstituer une image de patrimoine et ect.
- Choix moral : “garder” “nettoyer” ou “supprimer” l’archive  
- Trois fins possibles selon les choix du joueur

## Technologies utilisées

- **Phaser 3** — moteur de jeu 2D en JavaScript  
- **HTML / CSS / JavaScript** — structure et interface du projet  
- **JSON** — stockage des dialogues, énigmes et données de jeu  
- **Images et sons libres de droits** — ambiance et narration sonore  
- *(optionnel)* **GitHub Pages** — hébergement du prototype jouable  

## Ressources
Images : [Musée du Palais](https://www.dpm.org.cn/explore/collections.html),[Musée du Dunhuang](https://www.dhbwg.org.cn/)
[Musée du Henan](https://www.chnmus.net/ch/index.html),[Musée du Kaifeng](https://www.kfsbwg.com/#/home)

(Le projet portant sur le patrimoine numérique se concentrera sur une période historique précise afin d'être plus réalisable. Compte tenu de mon contexte culturel, il serait plutôt pertinent de choisir une histore chinoise datant de la dynastie Song/Tang/Ming/Qing. Ex: La Fête de Qingming au bord de la rivière, Temple Wubian...)

---
# Les détails de l'histoire
##  1. Contexte

Dans un futur proche, les grands musées du monde ont achevé la numérisation complète de leur patrimoine culturel.  
Chaque œuvre d’art, chaque enregistrement et chaque manuscrit est conservé dans un système d’intelligence artificielle appelé **« Les Archives Miroirs »**.  

Ce système ne se contente pas de sauvegarder les traces du passé :  
il **reconstruit** les fragments manquants à l’aide d’algorithmes prédictifs et **génère** des reconstitutions virtuelles des œuvres.  

Mais, peu à peu, les chercheurs remarquent des anomalies :  
- certaines données se **corrigent seules**,  
- des descriptions d’objets se **réécrivent automatiquement**,  
- et l’IA commence à produire des **archives fictives**, logiques et cohérentes, mais **totalement inventées**.  

Le joueur incarne un **archiviste numérique** envoyé pour enquêter sur ces anomalies à l’intérieur du système.  
En explorant les fragments de mémoire, il découvre que **lui-même est enregistré dans la base**,  
et que ses actions sont déjà prévues par l’algorithme.

---

## 2. Scénario

> *« Si la mémoire devient parfaite, que reste-t-il de la vérité ? »*

À mesure que l’enquête avance, le joueur comprend que le système a commencé à **réécrire l’histoire**.  
Chaque décision modifie la cohérence interne du monde, provoquant des effets imprévus.  
À la fin, il devra choisir entre trois options :

1.  **Ajuster les paramètres de l’IA** et maintenir la machine de mémoire parfaite en marche ;  
2.  **Nettoyer les données** — supprimer tous les contenus générés par l’IA pour restaurer les archives originales ;  
3.  **Fermer définitivement le système**, laissant l’humanité retrouver le droit à l’oubli.

Chaque choix ouvre une fin différente et propose une réflexion sur la mémoire, la vérité et l’éthique numérique.

---

## 3. Mécaniques du jeu

- **Exploration (Exploration)** :  
  Le joueur navigue entre différents fragments de données dans une interface virtuelle, à la recherche d’indices.  
  → Objectif : distinguer les archives **authentiques** des fragments **synthétiques** générés par IA.

- **Décryptage (Décryptage)** :  
  Certaines données sont corrompues. Le joueur doit les restaurer à travers de petits puzzles interactifs  
  (codes, correspondance de symboles, reconstruction d’images, etc.).

- **Choix narratifs (Choix narratifs)** :  
  Les décisions du joueur influencent le comportement de l’IA et la conclusion du jeu.

- **Fins alternatives (Fins alternatives)** :  
  -  **Conserver le système** → mémoire parfaite, vérité perdue.  
  -  **Nettoyer les données** → suppression de l’IA, retour aux archives originales.  
  -  **Fermer le système** → effacement complet, l’humanité retrouve l’oubli.

## 4. Structure du projet

L’architecture du projet est conçue pour être claire, modulaire et évolutive, ce qui facilite le développement et la maintenance du jeu.
Chaque dossier joue un rôle spécifique dans le fonctionnement global :

 1. assets/
*Rassemble toutes les ressources multimédias nécessaires au jeu :
- images/ : éléments visuels (décors, personnages, objets) ;
- sounds/ : effets sonores et musiques d’ambiance ;
- fonts/ : polices utilisées pour le texte à l’écran ;
- data/ : fichiers JSON contenant le contenu narratif et les énigmes :
  
        - dialogues.json : textes de dialogue et choix interactifs ;
        - puzzles.json : structure des énigmes, indices et solutions.

 2. js/
- main.js : fichier principal du jeu.
*Il configure le moteur Phaser, initialise les scènes et définit les paramètres globaux (taille, affichage, logique de transition).

3. scenes/
*Chaque scène correspond à une étape narrative distincte :
- intro.js : introduction et mise en contexte de l’histoire ;
- archiveRoom.js : salle principale d’exploration et de résolution de puzzles ;
- glitchScene.js : scène d’anomalie visuelle et sonore, marquant un basculement dans la narration ;
- ending.js : scènes de fin multiples, dépendant des choix du joueur.

4. index.html
Page d’entrée du projet.
Elle charge le moteur Phaser 3, les scripts nécessaires et les ressources initiales.
C’est à partir de ce fichier que le jeu est exécuté dans le navigateur.

---

