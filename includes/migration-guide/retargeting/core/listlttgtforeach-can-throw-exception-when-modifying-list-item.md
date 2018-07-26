### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>Seznam&lt;T&gt;. ForEach může vyvolat výjimku při úpravě položky seznamu

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5 <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> čítač vyvolá výjimku <xref:System.InvalidOperationException?displayProperty=name> výjimku, pokud byl prvek v kolekci volání změněn. Dříve to vyvolání výjimky, by ale může vést ke konfliktům časování.|
|Návrh|V ideálním případě by kód stanovit nemohou měnit seznamy při vytváření výčtu jejich elementy, protože to je nikdy bezpečný provoz. Chcete-li vrátit k předchozí chování, ale aplikace mohou být zaměřeny na rozhraní .NET Framework 4.0.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|

