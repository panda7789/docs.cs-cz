### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource.WriteEvent impls musíte předat metodě WriteEvent stejné parametry, které obdržel (plus ID)

|   |   |
|---|---|
|Podrobnosti|Runtime modul vynucuje nyní kontrakt, který určuje následující: Třída odvozená z <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> , který definuje ETW metodě události musí volat základní třídy <code>EventSource.WriteEvent</code> metoda s ID události, za nímž následuje stejné argumenty, které byla metoda události trasování událostí pro Windows předán.|
|Návrh|<xref:System.IndexOutOfRangeException?displayProperty=name> Je vyvolána výjimka, pokud <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> přečte <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data v procesu pro zdroje událostí, která porušuje tento kontrakt.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Modul runtime|

