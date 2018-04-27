### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET již nepodporuje kvalifikace částečné obor názvů pro rozhraní API System.Windows

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET 4.5.2, projektech VB.NET nelze zadat System.Windows rozhraní API s částečně kvalifikovaný obory názvů. Například odkazující na <code>Windows.Forms.DialogResult</code> se nezdaří. Místo toho musí kódu odkazovat na plně kvalifikovaný název (<xref:System.Windows.Forms.DialogResult>) nebo importovat konkrétní obor názvů a odkazovat pouze na <xref:System.Windows.Forms.DialogResult?displayProperty=name>.|
|Návrh|Kód by měl aktualizovat odkazovat na <code>System.Windows</code> rozhraní API s jednoduché názvy (a import relevantní oboru názvů) nebo s plně kvalifikované názvy.|
|Rozsah|Vedlejší|
|Version|4.5.2|
|Typ|Změna orientace|

