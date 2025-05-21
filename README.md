# ChangeSlotAutoEquip

ChangeSlotAutoEquip est un petit plugin Spigot destiné à la version **1.16.4**. Il permet d'équiper ou de retirer automatiquement l'armure et le bouclier d'un joueur lorsqu'il change de slot dans sa barre rapide. Le projet est développé en Java et se compile via **Maven**.

## Fonctionnement

Le plugin s'active uniquement pour les joueurs possédant le tag `ChangingSlotAutoEquip` sur leur scoreboard.

- **Changement vers un slot vide** : si le joueur sélectionne un slot vide alors que le slot précédent contenait un objet, toute l'armure portée (casque, plastron, jambières, bottes) ainsi que l'objet de la main secondaire sont retirés et stockés dans l'inventaire, respectivement dans les slots 9 à 13. Si ces emplacements sont déjà occupés, les objets sont simplement ajoutés à l'inventaire.
- **Changement vers une arme (épée ou hache)** : si le joueur sélectionne un slot contenant une épée ou une hache, les pièces d'armure éventuellement stockées dans les slots 9 à 13 sont rééquipées sur le joueur, et retirées de l'inventaire.

Ces comportements sont gérés dans `AutoEquipEvent.java` via l'événement `PlayerItemHeldEvent`.

## Fichiers de configuration

### `config.yml`

Ce fichier est fourni avec le plugin mais n'est actuellement pas utilisé dans le code. Il contient néanmoins les options suivantes :

- `enable` *(booléen)* : active ou désactive globalement le plugin.
- `projectile-rides-arrow` *(booléen)* : option héritée d'un autre projet, sans effet ici.
- `extra` *(section)* :
  - `spawn_eggs` *(booléen)*
  - `eggs` *(booléen)*
  - `snowballs` *(booléen)*
  - `boats` *(booléen)*
- `automount` *(section)* :
  - `enable` *(booléen)*
  - `entities.horses.enable` *(booléen)*
  - `entities.horses.auto_tame` *(booléen)*
  - `entities.horses.auto_saddle` *(booléen)*
  - `entities.boats` *(booléen)*
- `player-launch` *(booléen)*

### `plugin.yml`

```
name: ChangeSlotAutoEquip
author: DarkBow_
version: 1.0
main: fr.darkbow_.changeslotautoequip.ChangeSlotAutoEquip
```

Aucune commande ou permission n'est déclarée dans ce fichier.

## Commandes

Le plugin ne définit pas de commande particulière. Il fonctionne automatiquement pour les joueurs disposant du tag `ChangingSlotAutoEquip`.

## Compilation / Installation

Le projet utilise **Maven**. Pour compiler le plugin :

```bash
mvn package
```

Le fichier JAR sera généré dans le dossier `target/` sous le nom `ChangeSlotAutoEquip-1.0.jar`. Copiez ce fichier dans le dossier `plugins/` de votre serveur Spigot puis redémarrez-le.

## Fichiers importants

- `src/main/java/fr/darkbow_/changeslotautoequip/ChangeSlotAutoEquip.java` : classe principale du plugin, enregistre l'événement.
- `src/main/java/fr/darkbow_/changeslotautoequip/AutoEquipEvent.java` : gère l'équipement automatique lors du changement de slot.
- `src/main/resources/config.yml` : configuration (actuellement inutilisée).
- `src/main/resources/plugin.yml` : déclaration du plugin pour Spigot.
- `target/` : répertoire où Maven place le JAR compilé.

## Utilisation rapide

1. Compilez le plugin avec `mvn package`.
2. Déposez `ChangeSlotAutoEquip-1.0.jar` dans le dossier `plugins/` de votre serveur Spigot 1.16.4.
3. Lancez le serveur puis attribuez le tag `ChangingSlotAutoEquip` aux joueurs concernés (par exemple via une commande de scoreboard).
4. Lorsque ces joueurs passent d'un slot vide à une arme (ou inversement), leur équipement sera automatiquement rangé ou remis.

## Licence et contributions

Aucune licence n'est fournie dans ce dépôt et aucun fichier de contribution spécifique n'est présent. Vous pouvez donc adapter ce plugin selon vos besoins. N'hésitez pas à proposer des améliorations par *pull request* ou *fork*.

