### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>Seznam&lt;T&gt;. ForEach výjimku můžete vyvolat při úpravě položky seznamu

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET 4.5 <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> vyvolá výjimku enumerátor <xref:System.InvalidOperationException?displayProperty=name> výjimka, pokud je upraven element v kolekci volání. Dříve to nebude výjimku ale může vést k časování.|
|Návrh|V ideálním případě je třeba stanovit kód není upravit seznamy při vytváření výčtu jejich elementů, protože se jedná nikdy bezpečný provoz. Chcete-li vrátit k předchozí chování, ale aplikace mohou být zaměřeny na rozhraní .NET 4.0.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|

