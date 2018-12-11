### <a name="xslt-forward-compat-now-works"></a>Dopředné kompatibility XSLT teď funguje.

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4 dopředné kompatibility XSLT 1.0 vyskytly následující problémy:<ul><li>Načítání šablony stylů se nezdařilo, pokud byla její verze nastavena jako 2.0 a analyzátor zjistil nerozpoznanou konstrukci XSLT 1.0.</li><li><code>xsl:sort</code> Konstrukce nepodařilo řazení dat, pokud byla verze šablony stylu nastavena na hodnotu 1.1.</li></ul>V rozhraní .NET Framework 4.5 byly tyto problémy vyřešeny a režim dopředné kompatibility XSLT 1.0 funguje správně.|
|Doporučení|Většina aplikací by to neovlivní, ale data budou seřazeny jinak než v některých případech teď, když je dodržena XSL: sort. Pokud <code>xsl:sort</code> je používán 1.1 šablony stylů, potvrďte, že aplikace nebyla v závislosti na pořadí seřazená data. Pokud aplikace závisí na 4.0 chování řazení, odeberte <code>xsl:sort</code> ze šablony stylů.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|

