### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>Obousměrná vazba dat na vlastnost s neveřejným setter není podporován.

|   |   |
|---|---|
|Podrobnosti|Pokus o vázání dat na vlastnost bez veřejné metody setter nebyl nikdy podporovaný scénář. Od rozhraní .NET Framework 4.5.1, tento scénář se vyvolá <xref:System.InvalidOperationException?displayProperty=name>. Poznámka: Tato nová výjimka bude vyvolána pouze pro aplikace, které specificky cílí na rozhraní .NET Framework 4.5.1. Pokud aplikace cílí na rozhraní .NET Framework 4.5, povolí se volání. Pokud aplikace sdělení nebudete cílit na konkrétní verzi rozhraní .NET Framework, vazba bude považovat za jako jednosměrná.|
|Návrh|Aplikace se musí aktualizovat buď pomocí jednosměrné vazby, nebo veřejně zpřístupnit setter vlastnosti. Můžete také cílí na rozhraní .NET Framework 4.5 způsobí, že aplikace staré chování.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType></li></ul>|

