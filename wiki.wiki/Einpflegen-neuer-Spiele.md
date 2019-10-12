Um dem ClientUI neue Spiele hinzuzufügen, müssen diese in die dafür vorgesehene Liste eingetragen werden.

![Spiel Listen im ClientUI](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_15.png)

## Singleplayer Spiel anlegen
Neue Singleplayer Spiele müssen in der “Singleplayer Games“ Liste eingetragen werden. Dazu ist der Name des Spiels und die Startszene des Spiels anzugeben.

## Multiplayer Spiele anlegen
Neue Multiplayer Spiele müssen in der “Multiplayer Games“ Liste eingetragen werden. Dazu ist, wie auch bei Singleplayer Spielen der Name des Spiels und die Startszene anzugeben. Zusätzlich ist jedoch auch die LobbyFactory und das GameObject mit den Einstellungen anzugeben.

### LobbyFactory
Eine LobbyFactory ist eine statische Methode, welche eine neue Lobby erstellt und die Einstellungen vornimmt.

```cs
public static ILobby Deathmatch(LobbiesModule module, Dictionary<string, string> properties, IPeer creator)
{
   // Setzte Lobby auf [...]
   return lobby;
}
```

Diese Methode wird dann im Master Server dem Lobbies-Modul hinzugefügt.

```cs
module.AddFactory(new LobbyFactoryAnonymous("Deathmatch", module, LobbyFactories.Deathmatch));
```

Nähers zu unserer Umsetzung in folgenden [Code-Files](https://github.com/K0bin/SWT-P_SS_19_Learn/tree/master/LearnGame/Assets/Scripts/MasterServer/LobbyFactories).

### Game Options
Bei den Game Options muss ein GameObject angegeben werden, welches ein Skript enthält, dass das IGameOptions Interface implementiert.

```cs
public class QuestionShooterOptions : MonoBehaviour, IGameOptions
{
// [...]
}
```

Das GameObject muss sich im ClientUI an folgender Position befinden:

![GameOptions im ClientUI](https://github.com/K0bin/SWT-P_SS_19_Learn/blob/master/BilderWiki/AuthLobbyChat/AuthLobbyChat_16.png)

Nähers zu unserer Umsetzung in folgenden [Code-Files](https://github.com/K0bin/SWT-P_SS_19_Learn/tree/master/LearnGame/Assets/Scripts/Client/UI/Lobby/Options).