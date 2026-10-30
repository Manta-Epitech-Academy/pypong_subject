# PyPong

Créez votre propre jeu Pong simplifié en Python avec TIC-80 !

Contenu d'atelier au format **convention 2.0**, prêt à être importé dans une instance CTFd par la plateforme [CTFd_coding_platform](https://github.com/kevin-cazal/CTFd_coding_platform).

## Ce que contient ce dépôt

| Fichier | Rôle |
|---|---|
| `subject.yaml` | la fiche d'identité du sujet : nom, ordre de lecture, runtime, défauts |
| `intro.md` | document de l'atelier (page d'entrée) |
| `pypong.md` | document de l'atelier |
| `quiz_answers.yaml.gpg` | les réponses, chiffrées (voir plus bas) |
| `decrypt.sh` / `encrypt.sh` | déchiffrer avant un import, rechiffrer après une modification |

Le texte est du Markdown normal, lisible tel quel sur GitHub. Tout ce dont la plateforme a besoin est porté par des commentaires HTML `<!-- ws: ... -->`, invisibles à la lecture. La structure de l'atelier est lue dans les titres : il n'y a pas de sommaire à tenir à jour.

## Comment cet atelier est réglé

- **Mode** : `instructor_led`
- **Validation** : `checkpoint`
- **Points par étape** : 10 XP par minute estimée, en multiples de 5, fixés étape par étape (1390 XP au total, pour une durée estimée d'environ 2 h 20). Les points CTFd sont les XP Jump, un pour un. On les change ici, puis on resynchronise : jamais à la main dans l'admin CTFd.

| Étape | Validation | XP |
|---|---|---|
| Prendre en main l'environnement | quiz | 100 |
| Affichage du pad et de l'écran de jeu | quiz | 100 |
| Faire bouger le pad | code animateur | 200 |
| Quiz : Les touches du joueur | quiz | 20 |
| Créer la balle rebondissante | quiz | 150 |
| Faire rebondir la balle | code animateur | 200 |
| Quiz : Le sens du rebond | quiz | 20 |
| Checkpoint | code animateur | 50 |
| Gérer le respawn et la collision avec le pad | code animateur | 250 |
| Ajouter une interface | code animateur | 300 |

Dans une étape validée par quiz, seule la valeur de l'étape compte : les `points` des questions qu'elle contient sont ignorés.
- **Runtime** : TIC-80 (`tic80` épinglé en `8ad976f`) — [tic80-web-editor_runtime](https://github.com/kevin-cazal/tic80-web-editor_runtime)

## Les réponses

`quiz_answers.yaml` n'est **pas** en clair dans ce dépôt public. La version chiffrée (`quiz_answers.yaml.gpg`, AES256 symétrique) est versionnée, le clair est ignoré par git.

```sh
GPG_PASSPHRASE=... ./decrypt.sh   # avant un import
GPG_PASSPHRASE=... ./encrypt.sh   # après avoir modifié les réponses
```

## Mettre cet atelier en ligne

```sh
git clone https://github.com/kevin-cazal/CTFd_coding_platform
cd CTFd_coding_platform
docker compose up -d                      # CTFd sur :8080
python3 tools/sync_subject.py <ce-depot> \
    --url http://localhost:8080 --admin-user admin --admin-pass ...
```

Relancer la commande met le contenu à jour : les étapes sont réconciliées par leur `id`, les réussites des participants sont conservées.

## Écrire ou modifier du contenu

La convention complète est dans [`docs/CONTENT_CONVENTION.md`](https://github.com/kevin-cazal/CTFd_coding_platform/blob/main/docs/CONTENT_CONVENTION.md), la version courte dans [`docs/CONTRIBUER.md`](https://github.com/kevin-cazal/CTFd_coding_platform/blob/main/docs/CONTRIBUER.md).

Deux règles de fond : le contenu s'écrit **en français**, en phrases simples, pour des lycéens de 15 à 18 ans — et **on ne donne jamais la réponse**, ni dans le texte ni dans les indices.
