### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF už pro zobrazení Queryview vyvolá s konkrétními vlastnostmi

|   |   |
|---|---|
|Podrobnosti|Rozhraní Entity Framework už vyvolá <xref:System.StackOverflowException?displayProperty=name> výjimky, když aplikace provede dotaz, který zahrnuje zobrazení QueryView s 0..1 navigační vlastnost, která se pokusí zahrnout související entity jako součást dotazu. Například voláním <code>.Include(e =&gt; e.RelatedNavProp)</code>.|
|Návrh|Tato změna ovlivňuje pouze kód, který používá zobrazení Queryview s 1-0..1 vztahy při spuštění dotazuje toto volání. Zahrnout. Se zvyšuje spolehlivost a mělo by být transparentní na téměř všechny aplikace. Ale pokud vede k neočekávanému chování, můžete ji můžete vypnout přidáním následující položku na <code>&lt;appSettings&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.5.2|
|Typ|modul runtime|

