### <a name="xslt-forward-compat-now-works"></a>Předat dál compat XSLT teď funguje.

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4 bylo dopřednou kompatibilitu XSLT 1.0 následující problémy:<ul><li>Načítání šablony stylů se nezdařilo, pokud byla její verze nastavena jako 2.0 a analyzátor zjistil nerozpoznanou konstrukci XSLT 1.0.</li><li><code>xsl:sort</code> Konstrukce nepodařilo řazení dat v případě verze list stylu byla nastavena na 1.1.</li></ul>V rozhraní .NET Framework 4.5 tyto opravy a XSLT 1.0 dopřednou kompatibilitu režim funguje správně.|
|Návrh|Většina aplikací by měl neovlivní, ale data se má seřadit jinak v některých případech teď, když je dodržena Sort. Pokud <code>xsl:sort</code> se používá v 1.1 šablony stylů, potvrďte, že aplikace nebyly v závislosti na pořadí seřazená data. Pokud aplikace spoléhají na 4.0 řazení chování, odeberte <code>xsl:sort</code> z této šablony.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|

