### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF serializuje Expressions.Literal&lt;T&gt; DateTimes odlišně, teď (přeruší vlastní analyzátory XAML)

|   |   |
|---|---|
|Podrobnosti|Přidružené <xref:System.Windows.Markup.ValueSerializer> převede objekt <xref:System.DateTime?displayProperty=name> nebo <xref:System.DateTimeOffset?displayProperty=name> jehož druhý objekt a <xref:System.DateTime.Millisecond?displayProperty=name> komponenty jsou nenulové a (pro <xref:System.DateTime?displayProperty=name> hodnotu) jehož <xref:System.DateTime.Kind> vlastnost není property – element Syntaxe namísto řetězce. Tato změna umožňuje <xref:System.DateTime?displayProperty=name> a <xref:System.DateTimeOffset?displayProperty=name> hodnoty round-trip. Vlastní analyzátory XAML, které předpokládají, že vstup XAML je v syntaxi atributu, nebudou pracovat správně.|
|Návrh|Tato změna umožňuje <xref:System.DateTime?displayProperty=name> a <xref:System.DateTimeOffset?displayProperty=name> hodnoty round-trip. Vlastní analyzátory XAML, které předpokládají, že vstup XAML je v syntaxi atributu, nebudou pracovat správně.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|

