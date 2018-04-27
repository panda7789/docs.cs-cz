### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>Obousměrné datové vazby na vlastnost s neveřejným setter není podporován.

|   |   |
|---|---|
|Podrobnosti|Probíhá pokus o vazbě dat na vlastnost bez veřejnou metodu setter nikdy nebyla podporovaném scénáři. Od verze rozhraní .NET Framework 4.5.1, vyvolá výjimku tento scénář <xref:System.InvalidOperationException?displayProperty=name>. Všimněte si, že tento nový pouze k výjimce pro aplikace, která se specificky zaměřují rozhraní .NET Framework 4.5.1. Pokud aplikace cílí rozhraní .NET Framework 4.5, budou mít povolený volání. Pokud aplikace není zaměřen na konkrétní verzi rozhraní .NET Framework, bude vazba jednal jako jednosměrný.|
|Návrh|Aplikace se musí aktualizovat na buď pomocí jednosměrné vazby, nebo veřejně vystavit pro vlastnost setter. Alternativně cílení na rozhraní .NET Framework 4.5 způsobí, že aplikace staré chování.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType></li></ul>|

