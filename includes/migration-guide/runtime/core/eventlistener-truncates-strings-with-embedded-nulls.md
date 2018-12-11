### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>Naslouchacího procesu událostí zkrátí řetězce s vložené znaky Null

|   |   |
|---|---|
|Podrobnosti|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> zkrátí řetězce s vložené znaky null. Znaky s hodnotou Null nejsou podporovány <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> třídy. Tato změna ovlivní pouze aplikace, které používají <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> číst <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data v procesu a jako oddělovače použít znaky s hodnotou null.|
|Doporučení|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data se musí aktualizovat, pokud je to možné, používat vložené znaky null.|
|Rozsah|Edge|
|Version|4.5.1|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|

