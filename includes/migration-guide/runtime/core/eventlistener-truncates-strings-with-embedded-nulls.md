### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>EventListener zkrátí řetězce s embedded hodnoty Null

|   |   |
|---|---|
|Podrobnosti|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> zkrátí řetězce s embedded hodnoty Null. Znaky Null nejsou podporovány <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> třídy. Změna ovlivní pouze aplikace, které používají <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> číst <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data v procesu a které používají znaky null jako oddělovače.|
|Návrh|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data je třeba aktualizovat, pokud je to možné, nechcete použít vložené znaky null.|
|Rozsah|Edge|
|Version|4.5.1|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|

