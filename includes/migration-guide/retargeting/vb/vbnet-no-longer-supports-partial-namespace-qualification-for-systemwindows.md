### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET už nepodporuje kvalifikace částečné obor názvů System.Windows rozhraní API

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5.2, VB.NET projekty nelze zadat System.Windows rozhraní API s částečně kvalifikované obory názvů. Například odkazující na <code>Windows.Forms.DialogResult</code> se nezdaří. Místo toho kód musí odkazovat na plně kvalifikovaný název (<xref:System.Windows.Forms.DialogResult>) nebo importovat konkrétní obor názvů a odkazovat pouze na <xref:System.Windows.Forms.DialogResult?displayProperty=name>.|
|Návrh|Kód by měl aktualizovat o <code>System.Windows</code> rozhraní API pomocí jednoduchých názvy (a import oboru názvů relevantní) nebo s plně kvalifikované názvy.|
|Rozsah|Vedlejší|
|Version|4.5.2|
|Typ|Mění se cílení|

