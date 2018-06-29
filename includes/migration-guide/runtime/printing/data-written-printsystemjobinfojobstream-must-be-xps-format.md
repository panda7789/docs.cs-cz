### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>Data zapsaná do PrintSystemJobInfo.JobStream musí být ve formátu XPS

|   |   |
|---|---|
|Podrobnosti|<xref:System.Printing.PrintSystemJobInfo.JobStream> Vlastnost zpřístupní datový proud tiskové úlohy. Uživatel může odesílat data o hrubém základní tisk součástí operačního systému napsáním s tímto datovým proudem. Od verze rozhraní .NET Framework 4.5 na Windows 8 a novějších verzích operačního systému, dat zapsaných na tento datový proud musí být ve formátu XPS jako datový proud balíčku.|
|Návrh|K vypsání tiskové obsah, můžete provést jeden z následujících akcí:<ul><li>Použití <xref:System.Windows.Xps.XpsDocumentWriter> třída výstup tiskové obsah. Toto je Doporučená alternativa.</li><li>Ujistěte se, že data odeslaná do datového proudu vrácený <xref:System.Printing.PrintSystemJobInfo.JobStream> vlastnost je ve formátu XPS jako datový proud balíčku.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|

