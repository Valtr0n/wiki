Um die Multiplayer Funktion umzusetzen haben wir das [Barebones Master Server Framework](https://github.com/alvyxaz/barebones-masterserver) verwendet. Im Folgenden wird die grundsätzliche Funktionsweise kurz erklärt und anschließend gezeigt, wird das Framework in unserem Projekt verwendet wird.

Die komplette Dokumentation des  Master Server Frameworks befindet sich [hier](https://github.com/alvyxaz/barebones-masterserver/wiki).

## Grundsätzliche Funktionsweise
![Überblick über den Aufbau des Master Server Frameworks](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_01.png)

Das Framework besteht aus drei Servern:

### Master Server
Der namensgebende Master Server beinhaltet unter Anderem die folgenden Funktionen:
- Authentifizierung der Nutzer
- Verwalten von Lobbys, in denen sich zu Spielen getroffen wird
- Verwalten der angemeldeten Game Server
- Verwalten von Chaträumen und das Übertragen der Nachrichten

### Spawner Server
Der Spawner Server ist zuständig für das Erzeugen von Game Servern. Wollen Spieler also ein Spiel starten, sucht der Master Server nach einem geeigneten Spawner Server und gibt den Auftrag, einen Game Server zu erzeugen.

### Game Server
Der Game Server handelt die eigentliche Kommunikation des Spiels ab. 

Zusammenfassend kann man sagen, dass der Master Server die Instanz ist, welches das Konstrukt zusammenhält. Die verbindenden Funktionen führen zu einer geringen Netzlast. Der Game Server hingegen muss mit einer hoher Netzlast umgehen, da dort die Kommunikation des Spiels stattfindet. Das Serverkonstrukt ist somit für die Anzahl der Spieler skalierbar.