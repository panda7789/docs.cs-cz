### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Volání System.Windows.Input.PenContext.Disable na systémy s dotykovým ovládáním může vyvolat ArgumentException –

|   |   |
|---|---|
|Podrobnosti|Za určitých okolností volání na interní <strong>System.Windows.Intput.PenContext.Disable</strong> metoda na systémy s dotykovým ovládáním může vyvolat neošetřenou <code>T:System.ArgumentException</code> kvůli vícenásobný přístup.|
|Návrh|Tento problém byl vyřešen v 4.7 rozhraní .NET Framework. Pokud chcete zabránit výjimku, upgradujte na verzi rozhraní .NET Framework od verze 4.7 rozhraní .NET Framework.|
|Rozsah|Edge|
|Version|4.6.1|
|Typ|Změna orientace|

