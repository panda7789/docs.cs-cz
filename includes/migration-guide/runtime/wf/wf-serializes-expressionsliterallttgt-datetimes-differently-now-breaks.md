### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF serializuje Expressions.Literal&lt;T&gt; času jinak teď (dělí vlastní analyzátory XAML)

|   |   |
|---|---|
|Podrobnosti|Přidruženého <xref:System.Windows.Markup.ValueSerializer> objekt převede <xref:System.DateTime?displayProperty=name> nebo <xref:System.DateTimeOffset?displayProperty=name> jehož druhý objekt a <xref:System.DateTime.Millisecond?displayProperty=name> součásti jsou nulová a (pro <xref:System.DateTime?displayProperty=name> hodnotu) jejichž <xref:System.DateTime.Kind> vlastnost není vlastnost elementu Syntaxe místo řetězec. Tato změna umožňuje <xref:System.DateTime?displayProperty=name> a <xref:System.DateTimeOffset?displayProperty=name> hodnoty, které mají být zpětné odbavení. Vlastní analyzátory XAML, které předpokládají, že vstup XAML je v syntaxi atributu, nebudou pracovat správně.|
|Návrh|Tato změna umožňuje <xref:System.DateTime?displayProperty=name> a <xref:System.DateTimeOffset?displayProperty=name> hodnoty, které mají být zpětné odbavení. Vlastní analyzátory XAML, které předpokládají, že vstup XAML je v syntaxi atributu, nebudou pracovat správně.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|

