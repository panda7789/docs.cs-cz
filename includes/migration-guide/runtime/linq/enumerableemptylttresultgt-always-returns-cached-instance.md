### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Enumerable.Empty&lt;TResult&gt; vždy vrátí v mezipaměti instance

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> vždy vrátí instanci interní mezipaměti <xref:System.Collections.Generic.IEnumerable%601>. Dříve <xref:System.Linq.Enumerable.Empty%60%601> by mezipaměti prázdná <xref:System.Collections.Generic.IEnumerable%601> během rozhraní API byla volána, to znamená, že v některé podmínky, ve kterém <xref:System.Linq.Enumerable.Empty%60%601> byla volána rychle a současně, různé instance daného typu může být vrácen pro různé volání ROZHRANÍ API.|
|Doporučení|Protože předchozí chování je Nedeterministický, kód je nepravděpodobné, že by na něm závisí. Ale v případě nepravděpodobné, že se porovnávají prázdný výčty a má být v některých případech nerovnost, by měl být vytvořen explicitní prázdná pole (<code>new T[0]</code>) namísto použití <xref:System.Linq.Enumerable.Empty%60%601>.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|

