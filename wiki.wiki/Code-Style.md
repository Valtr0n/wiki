# Benennung
Unser Code orierntert sich in erster Linie an C# Konventionen.
* Methoden: UpperCamelCase
* private Felder: _lowerCamelCase
* public Felder: UpperCamelCase
* Konstanten: UpperCamelCase
* Klassen, Structs, Enums: UpperCamelCase
* Enum-Einträge: UpperCamelCase
* lokale Variablen & Parameter: lowerCamelCase
* private statische Variablen: lowerCamelCase
* public statische Variablen: lowerCamelCase

`public` und `internal` Felder sollten vermieden werden. Stattdessen sollten `public` Properties eingesetzt werden.

Felder und Properties vom Typ Bool sollten mit `is`, `are`, `can` oder `should` beginnen.

# Unity spezifisches
Felder, die im Unity Editor angezeigt werden, sollten `private` sein und das explizite `[SerializeField]` Attribut verwenden.

In Multiplayer Umgebungen sollten Methoden mit Seiteneffekten, wenn möglich, das `[Server]` oder `[Client]` Attribut bekommen. Dies sollte für die Lesbarkeit auch dann gemacht werden, wenn die Methode ohnehin nicht nur von Server/Client Methoden aufgerufen werden kann. Die Ausnahme hierfür sind von Unity selbst aufgerufene Methoden wie `OnStart`. Hierfür bietet Unity die Attribute `[ServerCallback]` und `[ClientCallback]`. Damit vermeidet man, dass das Log mit nutzlosen Meldungen darüber, dass z.B. auf dem Client eine Servermethode aufgerufen wird, gefüllt wird.
Mehr dazu in [Verwendung von UNet](https://github.com/K0bin/SWT-P_SS_19_Learn/wiki/Verwendung-von-UNet).

In LearnGame.Common, gibt es Extension Methods, die das nützliche Hilfsmethoden für Unity interne Klassen bieten.