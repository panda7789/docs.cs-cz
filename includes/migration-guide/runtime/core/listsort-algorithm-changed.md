### <a name="listsort-algorithm-changed"></a>List.Sort algoritmus změnit

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=name>algoritmus řazení došlo ke změně (třeba následující introspektivní řazení namísto rychlé řazení). <xref:System.Collections.Generic.List%601?displayProperty=name>pro řazení nebylo nikdy stabilní, ale tato změna může způsobit, že různé scénáře způsoby nestabilní řazení. Jednoduše to znamená, že ekvivalentní položky může řadit v různém pořadí v následných volání rozhraní API.|
|Návrh|Protože původní algoritmus řazení se také nestabilní (i když několika různými způsoby), by měl být žádný kód, který závisí na ekvivalentní položky vždy v určitém pořadí řazení. Pokud existuje instance kódu v závislosti na, který a štěstí s původní chování, tento kód by měl být aktualizován, aby pomocí porovnávače, která bude řadit nedeterministicky položky do požadovaného pořadí.|
|Rozsah|Transparentní|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|

