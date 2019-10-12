# Die SpielSzene

Die Szene in welcher sich das Spiel befindet findet man unter folgendem Pfad:
### LearnGame/Assets/Scenes/GameLevels

In dieser Szene befinden natürlich alle GameObjekts, welche für eine Multiplayer-Szene notwendig sind. Dazu mehr hier: [Szenen hinzufügen](https://github.com/K0bin/SWT-P_SS_19_Learn/wiki/Einpflegen-neuer-Spiele).

## Folgende GameObjects (im folgenden nur noch Objects) bilden das Spiel:

### KingSpwan:
Sinn dieses Objects ist es die Spawnpunkte (Boss und Spieler) für die Fragen-Phase des Bosses zu halten.

### SpawnPoints:
Enthält die Objects für die Spawnpunkte der Spieler.

### Boss:
Das ist der verrückte Professor in der Szene. An diesem Prefab hängt das Boss Script (Boss.cs), welches grob gesagt das Verhalten des Bosses steuert. Im Detail findet man dazu mehr in der Code Dokumentation. Des weiteren befinden sich die Partikel, Sound und "Fragen-Bomben" an diesem Object. Diese "Fragen-Bomben" sind Prefabs und heißen: "Aswer A", "Aswer B", "Aswer C".

### "Aswer A-C" 
Diese Prefabs werden über das AnswerBomb Script gesteuert (AnswerBomb.cs). 
Sie werden zudem auch im "Graveyard" verwendet.

### Grid bzw. BasicMap_Hill
Das Grid Object hält das BasicMap_Hill Prefab, welches das Spielfeld als TileMap darstellt. Es wird vom TileManager Script gesteuert(TileManager.cs).

### Graveyard
Dieses Object hält Spawnpunkte für die einzelnen Spieler (GP_1-4). Jedem Spieler wird einer dieser Zugeteilt. Sobald ein Spieler kein "Leben" mehr hat wird dieser an seinen GP_1-4 gespawned. An diesem Punkt angelangt muss der Spieler Fragen beantworten, in dem er die "Fragen-Bomben" entsprechend der Fragen beschießt. 

### QuestionManager 
Dieses Prefab kümmert sich:
* mit hilfe des CardLoader Scripts (CardLoader.cs) um das Laden der Daten aus einer Firebase Datenbank. 
* mit dem QuestionManager Script (QuestionManager.cs) umd die Fragenlogik in der Fragen-Phase des Bosses
* mit dem RewardManager Script um die Reward Logik.
* mit dem GraveyardManager Script um die Logik für Spieler auf dem Garveyard.
* mit dem RewardSaver Script werden die Rewards in der Firebase-DB gespeichert.

### BossArrow
Ein simples Objekt werlches dem Spieler mit hilfe des BossArrow Scripts einen Pfeil in Richtung des Bosses zeigt, falls dieser sich zu weit von diesem entfernt. 

### ServerFramerateLimiter
Dieses Object begrenzt die Framerate des Servers auf 60fps.


> # **Die Code Dokumentation für die genannten Scripts [Code-Doku](https://k0bin.github.io/SWT-P_SS_19_Learn/api/index.html)**
