## Erstellen von Lobbies
Nutzer können Lobbies erstellen:

![Fenster zum Erstellen von Lobbies](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_06.png)

Das UI für diese Funktion befindet sich im ClientUI:

![Erstellen von Lobbies im ClientUI](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_13.png)

## Suchen von Lobbies
Nutzer können Lobbies suchen und beitreten:

![Fenster zum Beitreten von Lobbies](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_07.png)

Das UI für diese Funktion befindet sich im ClientUI:

![Beitreten von Lobbies im ClientUI](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_12.png)

## Die Lobby selbst
In der Lobby bieten sich dem Nutzer, abhängig von dessen Rolle unterschiedliche Möglichkeiten.

![Fenster der Lobby](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_08.png)

Die Einstellungen(oben links) können nur vom Master (Host) der Lobby bearbeiten werden. Hier wird das gespielte Spiel ausgewählt. Außerdem beinhaltet jedes Spiel unterschiedliche Einstellungsmöglichkeiten. So können beispielsweise für das QuestionShooter Spiel der gespielte Kartensatz und die Anzahl der Phasen ausgewählt werden.

Wie man neue Multiplayer Spiele inklusive Einstellungen einpflegen kann, kann [hier](https://github.com/K0bin/SWT-P_SS_19_Learn/wiki/Einpflegen-neuer-Spiele#multiplayer-spiele-anlegen) nachgelesen werden.

Der Chat (unten links) bietet allen Spielern die Möglichkeit miteinander zu schreiben. Hierbei ist zu erwähnen, dass Spieler, welche einer Lobby mit einem laufenden Spiel beitreten, hier ebenfalls mit den sich im Spiel befindlichen Spielern schreiben können.

Die Auflistung der Spieler(rechts) zeigt ebenfalls an, ob alle Spieler bereit sind. Erst dann kann der Master das Spiel starten.

Das UI für diese Funktion befindet sich im ClientUI:

![Lobby im ClientUI](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_14.png)

Die Funktionen der Lobby werden seitens des Master Server Frameworks von dem Lobbies-Moduls angeboten. Dieses Modul verwendet wiederum das Matchmaker-Modul und das Rooms-Modul, um Spielsitzungen zu erstellen. Des weiteren wird ebenfalls das Chat-Modul verwendet, um den Chat zu realisieren. Somit vereint das Lobbies-Modul das Matchmaking, die Erstellung von Spiel-Servern und das Chatten zusammen mit den Funktionen der Lobby an sich. Man hat also nur noch Kontakt mit diesem einen übergeordneten Modul.

## Chat im Spiel

Der Lobby Chat und der Chat im Spiel sind identisch, bieten beide die selben Funktionen und verwenden auch beide das Lobbies-Modul. 

![Chat in der Lobby](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_09.png)