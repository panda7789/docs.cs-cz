### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Enumerable.Empty&lt;TResult&gt; vždy vrátí do mezipaměti instance

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET 4.5, <xref:System.Linq.Enumerable.Empty%60%601> vždy vrátí hodnotu uloženou v mezipaměti interní instance <xref:System.Collections.Generic.IEnumerable%601>. Dříve <xref:System.Linq.Enumerable.Empty%60%601> by mezipaměti prázdnou <xref:System.Collections.Generic.IEnumerable%601> během rozhraní API byla volána, znamená to, že v některé podmínky, ve kterém <xref:System.Linq.Enumerable.Empty%60%601> byla volána rychle a souběžně, jiné instance typu nemohl být vrácen pro různé volání ROZHRANÍ API.|
|Návrh|Protože předchozí chování je Nedeterministický, kód je nepravděpodobné, že jsou na ní závislé. Ale v případě nepravděpodobné, že prázdný enumerables se porovnají a očekává se někdy nerovné, by měl být vytvořen explicitní prázdné pole (<code>new T[0]</code>) namísto použití <xref:System.Linq.Enumerable.Empty%60%601>.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|

