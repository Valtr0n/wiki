## Was ist Codeflow

CodeFlow ist ein Spiel, welches dem Spieler die Grundlagen des Programmierens beibringen soll. Hierzu soll der Spieler mithilfe von einem visuellen Scripting Werkzeug kleine Aufgaben lösen. 

## Vorbilder

Ähnliche Scripting Systeme finden sich in neuen Game Engines wie Unreal Engine 4, Godot und vielen anderen. In diesen Engines sind sie als einfache Alternativen zu klassischen Skriptsprachen gedacht und sollen Designern ermöglichen, einfache Interaktivität einzubauen, ohne auf einen Entwickler angewiesen zu sein. Der Unterschied zu unserem Spiel liegt hauptsächlich darin, dass solche Plattformen keine Echtzeitausführung und visuelle Darstellung der Funktionsweise anbieten.
Codeflow im Gegensatz soll, ähnlich wie ein Debugger, grafisch zur Laufzeit darstellen, was passiert.

## Funktionsweise

Ein Befehlt wird dargestellt durch einen Block, der sowohl Eingänge, als auch Ausgänge hat.
Der Spieler zieht dann Linien zwischen diesen, um sowohl den Fluss von Daten, als auch die Ausführung zu steuern.

In jedem Level sind die Eingangsdaten festgelegt und es wird ein gewisses Ergebnis erwartet. Zusätzlich ist die Auswahl der Blöcke beschränkt, um den Spieler dazu zubringen, gewisse Taktiken zu entwickeln.

## Aufgabenstellungen

Eine mögliche Aufgabenstellung wäre es, eine Zahl hoch Zehn zu nehmen. Hierfür würde man als Parameter eine Variable bekommen und müsste diese entsprechen multiplizieren.
Das Ergebniss wird daraufhin von dem Spiel mit einem Erwartungswert verglichen.
Diese Aufgaben werden mehrfach mit verschiedenen Werten wiederholt um ein Hardcoding zu verhindern:
5^10, 2^10, 10^10


