# Verwendung von UNet

Um ein GameObject mit UNet zu verwenden, muss dieses den Component `Network Identity` haben. Wird dies vergessen, entstehen kryptische Fehler bei RPC/Cmd Aufrufen.

Darüber hinaus muss das Skript, in welchem UNet verwendet wird, von `NetworkBehaviour` erben.

# Generelles

Wenn möglich sollte der Server so gut wie alle Entscheidungen treffen. Die Ausnahme hierfür ist vor allem das Movement des lokalen Spielers. Dieses wird lokal ausgeführt, weil man dabei ansonsten eine starke Latenz merken würde, was dem Spielgefühl massiv schaden würde. Daher ist das Player Objekt das einzige, bei dem im `NetworkIdentity` Component der Haken bei `Local Player Authority` gesetzt ist. Dies bedeutet, dass anders als bei den anderen Objekten, der Client über dieses GameObjekt bestimmt.

# Mechanismen zur Synchronisation

## `[SyncVar]`

`[SyncVar]` bei einem Feld synchronisiert den Wert eines Value Typen (z.B. Primitive Typen wie int, float, etc. oder structs)

Dabei bietet es sich an, das dazugehörige Feld in ein Property zu packen und den Setter zusätzlich mit einem `[Server]` Attribut zu versehen. Das führt dazu, dass Unity eine Warnung wirft, wenn der Client versucht, den Wert zu überschreiben, aber keine Authority darüber hat. Tut man das nicht, wird der Wert nach dem Schreibvorgang lautlos wieder zurückgesetzt und man wundert sich unter Umständen, warum es nicht funktioniert hat.

## `[ClientRpc]`

Das `[ClientRpc]` Attribut an einer Methode führt dazu, dass der Server alle Clients anweist, diese Methode auszuführen. Die Methode muss mit dem Prefix `Rpc` beginnen. Es ist allerdings wichtig zu beachten, das dies erheblich aufwändiger ist, als ein normaler Methodenaufruf. Man sollte von daher auf keinen Fall in jedem `Update` einen Rpc-Aufruf machen. Ist dies notwendig, sollte `FixedUpdate` verwendet werden, da dies eine fixe Aufrufrate hat.

## `[TargetRpc]`

Das `[TargetRpc]` Attribut führt dazu, dass der Server nur **einen** Client anweist, die Methode auszuführen. Die dazugehörige Methode muss mit dem Prefix `Target` beginnen.

## `[Command]`

Das `[Command]` Attribut führt dazu, dass der Client den Server Client anweist, die Methode auszuführen. 
Es kann nur in Methoden des lokalen Spieler Objekts ausgeführt werden. Die dazugehörige Methode muss mit dem Prefix `Cmd` beginnen.

## `[Server]` und `[Client]`

Die Attribute `[Server]` und `[Client]` an einer Methode führen dazu, dass die Methode nur auf dem Server oder Client ausgeführt werden kann. Diese Attribute sind allerdings nicht für Unity interne Callbacks wie `Start` oder `Update` zu verwenden, da das zu Log Spam führt.
 
## `[ServerCallback]` und `[ClientCallback]`

`[ServerCallback]` und `[ClientCallback]` sind die Gegenstücke zu `[Server]` und `[Client]` für Unity interne Callbacks wie `Start` oder `Update`. Sie führen dazu, dass die Methoden nur auf Server oder Client aufgerufen werden.

## Spawn und Destroy

Das Erstellen und Zerstören von GameObjects muss über den NetworkManager passieren, damit es korrekt synchronisiert wird. Vor dem Erstellen muss das Prefab des GameObjects allerdings unbedingt der Spawn Liste hinzugefügt werden!

# Macken

Bei der Entwicklung hat die Verwendung von `SetActive()` bei GameObjects mit `NetworkBehaviour` zu massiven Problemen geführt. Die Unity Dokumentation sagt nichts dazu, ob `SetActive` synchronisiert wird. In der Praxis hat es dazugeführt, dass Rpc Aufrufe ohne Fehlermeldung einfach fehlgeschlagen sind.

Daher sollte `SetActive` bei GameObjects mit Networking vermieden werden.