### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource.WriteEvent impls musí projít WriteEvent stejné parametry, které obdržel (plus ID)

|   |   |
|---|---|
|Podrobnosti|Modul runtime teď vynucuje kontrakt, který určuje následující: Třída odvozená z <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> trasování událostí pro Windows, který definuje události metoda musí volat základní třídy <code>EventSource.WriteEvent</code> metoda s ID události následuje stejné argumenty, které metoda události trasování událostí pro Windows byl předán.|
|Návrh|<xref:System.IndexOutOfRangeException?displayProperty=name> Je vyvolána výjimka, pokud <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> čte <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data v procesu pro daný zdroj události, která porušuje tento kontrakt.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|modul runtime|

