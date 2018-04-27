### <a name="listsort-algorithm-changed"></a>List.Sort – algoritmus změnit

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=name>na algoritmus řazení došlo ke změně (jako při introspective řazení místo rychlého řazení). <xref:System.Collections.Generic.List%601?displayProperty=name>pro řazení nebyla nikdy stabilní, ale tato změna může způsobit, že různé scénáře seřadit nestabilním způsoby. Jednoduše to znamená, že může seřadit ekvivalentní položky v různém pořadí při následných voláních rozhraní API.|
|Návrh|Protože staré algoritmus řazení také nestabilním (i když v několika různými způsoby), měla by existovat žádný kód, který závisí na ekvivalentní položky vždy řazení v určitém pořadí. Pokud existují instance kódu v závislosti na který a šťastná s původním chování, tento kód by měl být aktualizováno na pomocí porovnávače, která nepodmíněně seřadíte položky do požadovaného pořadí.|
|Rozsah|Transparentní|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|

