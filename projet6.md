# testprojet6

## Optimisations et changements apportés

1. Optimisation du bouton d'entrée du jeu : sa position a été déplacée du coin inférieur gauche vers le centre de la page afin d’améliorer l’expérience utilisateur.

2. Après une analyse approfondie du code, il est apparu que les variables currentSlot, startX et startY avaient des significations confuses.
La variable slot était utilisée simultanément comme position logique, coordonnée d’affichage et référence pour l’échange, ce qui constituait l’une des principales sources de bugs.
Discussion avec l’IA :
https://chatgpt.com/share/693ecb01-7834-8008-9a66-eeb615f1097d

3. Décision finale : abandon du mécanisme d’échange par clic, passage à un système de glisser-déposer et séparation des zones de pièces et de la zone fixe afin de simplifier la logique.
Plusieurs versions de test sont disponibles : testprojet6t1.html
Discussion avec l’IA :
https://chatgpt.com/share/693edb86-a3e8-8008-b18e-9b7c610e9bea

## Réflexion sur le processus
Évolution de la logique：Clic pour échanger → Glisser-déposer → Séparation des zones

1. Logique de clic
Décalage constant entre les bordures et les pièces
Difficulté à identifier la pièce cible lors d’un échange
Code complexe et bugs persistants
Ne correspondait pas à l’intuition première des joueurs

2. Logique de glisser-déposer
Enregistrement de la position de départ
Tentative d’échange avec la pièce la plus proche
Problèmes persistants de décalage
Difficulté à déterminer correctement l’échange
Tentatives de simplification (placement manuel uniquement) générant de nouveaux bugs

Analyse de la logique de glisser-déposer:
Découper les pièces et enregistrer les coordonnées correctes.
Mélanger aléatoirement les pièces et enregistrer les positions actuelles et cibles.
À la fin du glissement :si la cible est vide → placer la pièce ; si la cible est occupée → échanger les pièces.

3. Séparation des zones
Problèmes initiaux:
Certaines pièces dépassaient la zone de visualisation
Décalage entre la pièce glissée et la pièce sélectionnée
Certaines bordures fixes ne pouvaient pas recevoir de pièces

Solutions mises en place:
Limitation stricte de la zone du pool de pièces
Correction du décalage lors de la sélection et du glissement
Correction des bordures fixes pour permettre le placement
Diagramme de la démarche et du débogage

## Réflexion générale
- La complexité du code dépassait mes capacités personnelles, rendant la résolution des bugs particulièrement difficile malgré plusieurs tentatives.
- Le manque de méthodologie systématique pour le débogage et la localisation des problèmes a entraîné de nombreux essais infructueux.
- Ce projet a mis en évidence l’importance d’une meilleure conception en amont et d’outils de débogage plus rigoureux.
- À l’avenir, il est préférable de commencer par des projets simples et d’augmenter progressivement la complexité afin d’éviter de se retrouver bloqué dans un code trop complexe.

## Diagramme
```mermaid
Diagramme de l’expérience joueur
    A[Archive minors] --> B(Introduction);
    B --> C(Salle :  l'œuvre Qingming]);
    C --> D(ACCÈS AU PUZZLE qingming);
    C --> E(Accès aux métadonnées de la scène);

    D --> F(Réorganiser les fragments de l'image pour compléter le puzzle);
    E --> G(Sélection des phrases erronées);

    F --> H{Puzzle déverrouillé ?};
    H -- P -> Non --> K(Échec/Retour);
    H -- P -> Oui (Énigme résolue) --> I(Q);

    G --> J{Toutes les erreurs trouvées ?};
    J -- T -> Non --> K;
    J -- T -> Oui --> L(Succès et validation);

    K --> M{Réessayer};
    M --> C;

    style A fill:#CCCCFF,stroke:#333
    style B fill:#CCCCFF,stroke:#333
    style C fill:#CCCCFF,stroke:#333
    style D fill:#CCCCFF,stroke:#333
    style E fill:#CCCCFF,stroke:#333
    style F fill:#CCCCFF,stroke:#333
    style G fill:#CCCCFF,stroke:#333
    style H fill:#CCCCFF,stroke:#333,stroke-dasharray: 5 5
    style I fill:#CCFFCC,stroke:#333
    style J fill:#CCCCFF,stroke:#333,stroke-dasharray: 5 5
    style K fill:#FFCCCC,stroke:#333
    style L fill:#CCFFCC,stroke:#333
    style M fill:#FFFFCC,stroke:#333



```mermaid 
Diagramme de la logique interne du jeu
    A[Lancement du jeu] --> B[Scène Intro]
    B --> C[Salle des archives]

    C --> D[Sélection de l'œuvre Qingming]
    D --> E[Accès au Puzzle]

    E --> F[Chargement de l'image principale]
    F --> G[Découpage en 15 fragments]

    G --> H[Mélange aléatoire des fragments]
    H --> I[Affichage du pool de pièces]
    H --> J[Affichage des emplacements fixes]

    I --> K[Interaction joueur : glisser-déposer]

    K --> L{Emplacement cible vide ?}
    L -->|Oui| M[Placer la pièce]
    L -->|Non| N[Refuser le placement]

    M --> O[Vérification de la solution]
    O --> P{Puzzle résolu ?}

    P -->|Non| K
    P -->|Oui| Q[Puzzle validé]

    Q --> R[Accès à la scène Métadonnées]
    R --> S[Sélection des phrases erronées]

    S --> T{Toutes les erreurs trouvées ?}
    T -->|Non| S
    T -->|Oui| U[Succès et validation]
```

```mermaid 
Diagramme du processus de conception et de débogage
    A[Début du projet Puzzle Qingming] --> B[Idée initiale : échange par clic]
    B --> B1[Implémentation du clic pour échanger]
    B1 --> B2[Problèmes détectés]

    B2 --> B21[Décalage entre cadres et pièces]
    B2 --> B22[Difficulté à identifier la pièce à échanger]
    B2 --> B23[Logique complexe et bugs persistants]

    B23 --> C[Changement de stratégie]

    C --> D[Essai : échange par glisser-déposer]
    D --> D1[Enregistrement position de départ]
    D --> D2[Échange avec la pièce la plus proche]

    D2 --> D3[Problèmes persistants]
    D3 --> D31[Décalage toujours présent]
    D3 --> D32[Échange difficile à déterminer]

    D3 --> E[Tentative de simplification]
    E --> E1[Suppression de l'échange automatique]
    E1 --> E2[Placement manuel uniquement]
    E2 --> E3[Nouveaux bugs apparaissent]

    E3 --> F[Phase de réflexion]

    F --> G[Nouvelle analyse de la logique]
    G --> G1[Découper les pièces]
    G --> G2[Mélanger l'ordre aléatoirement]
    G --> G3[Comparer position actuelle et position cible]

    G3 --> H[Décision finale]
    H --> I[Séparation du pool de pièces et de la zone fixe]
    I --> J[Simplification de la logique]

    J --> K[Résolution des principaux problèmes]
```
