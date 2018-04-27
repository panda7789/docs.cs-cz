### <a name="typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>Type.IsAssignableFrom vrátí chybný výsledek pro obecné proměnné s omezení

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5 <xref:System.Type.IsAssignableFrom(System.Type)> nesprávně vrátí <code>false</code> ve všech případech pro některé obecné typy s omezeními.|
|Návrh|Tento problém byl opraven v servisní aktualizace. Aktualizujte prosím rozhraní .NET Framework 4.5, nebo upgradujte na verzi rozhraní .NET Framework 4.5.1 nebo novější, pokud chcete tento problém vyřešit. Alternativně Vyhněte se používání IsAssignableFrom s obecné typy, které mají omezení obecných parametrů. Rozhraní API reflexe slouží jako řešení.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Type.IsAssignableFrom(System.Type)?displayProperty=nameWithType></li></ul>|
|Analyzátory|<ul><li>CD0089</li></ul>|

