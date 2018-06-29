### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>Trasování událostí pro Windows EventListeners není zachycen události z poskytovatelů s explicitní klíčová slova (např. zprostředkovatele TPL)

|   |   |
|---|---|
|Podrobnosti|Trasování událostí pro Windows EventListeners s maskou prázdné – klíčové slovo není správně zachycen události z poskytovatelů s explicitní klíčová slova. V rozhraní .NET Framework 4.5 zprostředkovatele TPL začal poskytnutí klíčových slov explicitní a aktivuje tento problém. V rozhraní .NET Framework 4.6 byly aktualizovány EventListeners již má tento problém.|
|Návrh|Chcete-li tento problém obejít, nahraďte volání <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> pomocí volání EnableEvents přetížení, které explicitně určuje &quot;klíčová slova&quot; maska použít: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Případně se tento problém byl opraven v rozhraní .NET Framework 4.6 a může být kontaktována upgrade na tuto verzi rozhraní .NET Framework.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

