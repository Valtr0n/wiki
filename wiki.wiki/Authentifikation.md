## Was verwenden wir?
Wir bieten dem Nutzer die Möglichkeit, sich zu registrieren, sich einzuloggen oder als Gast zu spielen.

![Authentifikations Fenster](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_02.png)

Das UI für diese Funktion befindet sich im ClientUI:

![Authentifikation im ClientUI](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_10.png)

## Speicherung
Die zugrundelegende Funktion der Authentifikation stammt aus dem Auth-Moduls des Master Server Frameworks. Die LogIn Daten der Spieler werden seitens des Master Servers in eine LiteDB namens auth gespeichert.