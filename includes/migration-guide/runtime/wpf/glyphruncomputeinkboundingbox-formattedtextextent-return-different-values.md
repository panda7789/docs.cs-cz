### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a>GlyphRun.ComputeInkBoundingBox() a FormattedText.Extent vracet různé hodnoty od verze rozhraní .NET Framework 4.5

|   |   |
|---|---|
|Podrobnosti|Byla provedena vylepšení <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> a <xref:System.Windows.Media.FormattedText.Extent> v rozhraní .NET Framework 4.5 umožní řešit problémy, kde byly do polí příliš malá pro obsažené glyfů v některých případech v rozhraní .NET Framework 4.0. V důsledku toho budou některé ohraničující polí větší od verze rozhraní .NET Framework 4.5, což vede k jemně lišit v rozložení uživatelského rozhraní.|
|Návrh|Upozorňujeme, že některé glyfy ohraničující pole velikosti zvýšil. Tyto změny se obvykle zlepšení prezentace a testování přístupů pole, ale pokud se požaduje starší chování (předběžné .NET 4.5), ho můžete vyjádřit výslovný souhlas do přidáním následující položku do souboru app.config:<pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|

