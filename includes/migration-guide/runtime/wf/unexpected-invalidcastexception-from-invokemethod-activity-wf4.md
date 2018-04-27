### <a name="unexpected-invalidcastexception-from-invokemethod-activity-in-wf4"></a>Neočekávané InvalidCastException z aktivity InvokeMethod v WF4

|   |   |
|---|---|
|Podrobnosti|Použití <xref:System.Activities.Statements.InvokeMethod> , můžete vyvolat cíle metodu s s možnou hodnotou NULL parametru <xref:System.InvalidCastException?displayProperty=name>.|
|Návrh|Toto chování se vrátila v rozhraní .NET Framework 4.5 obsluhy verze. Aktualizujte prosím rozhraní .NET Framework 4.5 (nebo upgradujte na verzi rozhraní .NET Framework 4.5.1 nebo novější) vyřešit problém.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Activities.Statements.InvokeMethod.Parameters?displayProperty=nameWithType></li></ul>|
|Analyzátory|<ul><li>CD0088</li></ul>|

