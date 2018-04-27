### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException v kódu z ImageSourceConverter.ConvertFrom zpracování výjimek

|   |   |
|---|---|
|Podrobnosti|Chyba v kód pro zpracování výjimek <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> kvůli nesprávné <xref:System.NullReferenceException?displayProperty=name> vyvolání namísto zamýšlené výjimky (<xref:System.IO.DirectoryNotFoundException?displayProperty=name> nebo <xref:System.IO.FileNotFoundException?displayProperty=name>). Tato změna opraví chybu tak, aby metoda nyní vyvolá výjimku správné. Pomocí výchozí cílení na rozhraní .NET Framework 4.6.2 všechny aplikace a níže budou nadále throw <xref:System.NullReferenceException?displayProperty=name> pro kompatibilitu, vývojáři cílení na rozhraní .NET Framework 4.7 a vyšší měli vidět správné výjimky.|
|Návrh|Vývojáři, kteří chtějí vrátit k získávání <xref:System.NullReferenceException?displayProperty=name> při cílení na rozhraní .NET Framework 4.7 nebo novější můžete přidat či sloučení následujícího souboru App.config jejich aplikace:<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|

