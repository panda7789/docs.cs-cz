### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Volání System.Windows.Input.PenContext.Disable systémech s dotykovým ovládáním může vyvolat ArgumentException

|   |   |
|---|---|
|Podrobnosti|Za určitých okolností volání vnitřní <strong>System.Windows.Intput.PenContext.Disable</strong> může vyvolat metodu na systémy s dotykovým ovládáním neošetřenou <code>T:System.ArgumentException</code> kvůli vícenásobnému přístupu.|
|Návrh|Tento problém byl vyřešen v rozhraní .NET Framework 4.7. Pokud chcete zabránit výjimku, upgradujte na verzi rozhraní .NET Framework počínaje .NET Framework 4.7.|
|Rozsah|Edge|
|Version|4.6.1|
|Typ|Mění se cílení|

