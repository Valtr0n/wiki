# CodeFlow Frontend

Das CodeFlow Frontend befindet sich im Order LearnGame/CodeFlow/Frontend.

Die wichtigsten Klassen sind:

## [BlockController](http://K0bin.github.io/SWT-P_SS_19_Learn/api/LearnGame.CodeFlow.Frontend.BlockController.html)

Der `BlockController` hält eine Referenz zu einem Backend `Tile` Objekt.
Nachdem alle Blöcke erstellt wurden, kümmern sich diese darum, die Inputs und Outputs zu erstellen.
Dabei muss man unterscheiden zwischen normalen Daten Parametern und Execution Parametern (`CodeFlowType.CodeFlow`).
Das erstellen der Inputs/Outputs passiert in zwei Durchläufen abhängig von der Art des Parameters:
* Datenparameter sind im Backend **rückwärts** verlinkt. Das heißt, ein Parameter im Block zeigt auf den Punkt, wo er seine Daten her bekommt. Daher werden hier zu erst die Output Parameter erstellt und danach die Inputs. Bei letzterem werden dann auch direkt Linien instanziiert.
* Execution Parameter sind im Backend **vorwärts** verlinkt. Das heißt, ein Parameter im Block zeigt auf den Punkt, welcher als nächstes ausgeführt wird. Aus diesem Grund werden für Execution Parameter die Inputs vor den Outputs erstellt. Auch hier werden im Anschluss Linien instanziiert.

## [OutputHandleDraggable](http://K0bin.github.io/SWT-P_SS_19_Learn/api/LearnGame.CodeFlow.Frontend.OutputHandleDraggable.html)

`OutputHandleDraggable` stellt einen Ausgangspunkt da. Aus diesem Grund hat es eine Referenz zur Backend `Param` Instanz, die dieses Handle repräsentiert. Der Handle kann gezogen werden, um eine neue Linie zu erstellen. Für Execution Parameter kann nur eine Linie existierten, während Datenparameter an mehrere Inputs angeschlossen werden können. Nach dem Erstellen der Linie wird das Drag&Drop Event unmittelbar an diese übergeben und von dieser gehandhabt.
`OutputHandleDraggable` hält Referenzen zu den verbundenen Linien.

## [InputHandleDraggable](http://K0bin.github.io/SWT-P_SS_19_Learn/api/LearnGame.CodeFlow.Frontend.InputHandleDraggable.html)

`InputHandleDraggable` ist das Gegenstück zum `OutputHandleDraggable`. Es stellt ebenfalls eine Backend `Param` dar, dient aber als Endpunkt einer Linie. Wenn eine Linie verbunden ist, kann diese vom Handle abgezogen werden. Auch `InputHandleDraggable` startet nur den Drag&Drop Vorgang und übergibt die Events dann an die verbundene Linie.
Anders als `OutputHandleDraggable` kann ein `InputHandleDraggable` immer nur mit einer Linie verbunden sein.
 
## [Line](http://K0bin.github.io/SWT-P_SS_19_Learn/api/LearnGame.CodeFlow.Frontend.Line.html)

Die Linie ist ein reines Frontend Konstrukt. Im Backend sind In- und Out- `Params` direkt verbunden. Daher hält die Linie anders als die anderen beiden Objekte keine Referenz zu einem Backend Objekt. Sie hält hingegen Referenzen zum `OutputHandleDraggable`, an dem sie anfängt und dem `InputHandleDraggable` an dem sie endet. Ist das `EndHandle` null, ist die Linie im Drag&Drop-Ziehmodus. Wird dann der Drag&Drop Vorgang beendet, macht die Linie einen Raycast und sucht nach einem geeigneten `InputHandleDraggable`, mit dem die Linie sich verbindet. Wird kein Handle gefunden, wird der `TilePicker` gezeigt.
Die wichtigste Aufgabe der Linie ist allerdings das bloße Rendern. Hierfür werden die Endpunkte in jedem Frame aktualisiert.

## [GameManager](http://K0bin.github.io/SWT-P_SS_19_Learn/api/LearnGame.CodeFlow.Frontend.GameManager.html)
Der `GameManager` kümmert sich um die zentrale Steuerung des CodeFlow Frontends. Er lädt das Level, erstellt die Blöcke und weist diesen das Backend `Tile` zu.
Hier außerdem wird das Spiel gestartet und es gibt Feedback, ob die Lösung richtig oder falsch ist. Darüber hinaus hat der `GameManager` auch die Debugger Callbacks aus dem Backend. Diese sind allerdings im Moment nur Stubs.

Es ist auch geplant, mehrere Funktionen zu unterstützen, die dann auf einem eigenen Spielfeld dargestellt werden und per Block aufgerufen werden. Hier würde der `GameManager` den Spielfeldwechsel übernehmen. Dies ist allerdings nicht implementiert.
