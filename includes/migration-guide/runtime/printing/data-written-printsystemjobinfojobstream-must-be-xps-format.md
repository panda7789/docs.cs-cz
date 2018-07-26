### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>Data zapsaná do PrintSystemJobInfo.JobStream musí být ve formátu XPS

|   |   |
|---|---|
|Podrobnosti|<xref:System.Printing.PrintSystemJobInfo.JobStream> Zpřístupňuje vlastnost datového proudu tiskové úlohy. Uživatel může odesílat nezpracovaná data na základní součásti tisku operačního systému pomocí zápisu s tímto datovým proudem. Od verze rozhraní .NET Framework 4.5 na Windows 8 a novější verze operačního systému Windows, zapsaná data do tohoto datového proudu musí být ve formátu XPS jako datový proud balíčku.|
|Návrh|Výstup vytisknout obsah, můžete provést jeden z následujících akcí:<ul><li>Použití <xref:System.Windows.Xps.XpsDocumentWriter> třídy do výstupního vytisknout obsah. Toto je Doporučená alternativa.</li><li>Ujistěte se, že data přenášená do datový proud vrácený <xref:System.Printing.PrintSystemJobInfo.JobStream> vlastnost je ve formátu XPS jako datový proud balíčku.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|

