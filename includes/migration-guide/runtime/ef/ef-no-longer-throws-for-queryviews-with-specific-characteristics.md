### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF již nevyvolá pro QueryViews s konkrétními vlastnostmi

|   |   |
|---|---|
|Podrobnosti|Entity Framework již nevyvolá <xref:System.StackOverflowException?displayProperty=name> výjimka při aplikace provede dotaz, který zahrnuje zobrazení QueryView s 0..1 navigační vlastnost, která se pokusí přidat související entity jako součást dotazu. Například voláním <code>.Include(e =&gt; e.RelatedNavProp)</code>.|
|Doporučení|Tato změna ovlivní pouze kód, který používá QueryViews s 1-0..1 relací při spuštění dotazů toto volání. Zahrnout. Zvyšuje spolehlivost a musejí být transparentní pro téměř všechny aplikace. Ale pokud dojde k neočekávanému chování, můžete zakázat ho tak, že přidáte následující položky <code>&lt;appSettings&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.5.2|
|Typ|Modul runtime|

