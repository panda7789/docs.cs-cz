### <a name="xml-schema-validation-is-stricter"></a>Ověření schématu XML je přísnější

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5 je více striktní ověřování schématu XML. Jestliže použijete xsd:anyURI k vyhodnocení URI jako protokolu e-mailu a v URI jsou mezery, vyhodnocení selže. V předchozích verzích rozhraní .NET Framework ověření proběhlo úspěšně. Změna ovlivní pouze aplikace cílených rozhraní .NET Framework 4.5.|
|Návrh|V případě potřeby Čím větší ověřování rozhraní .NET Framework 4.0 ověřování aplikace, můžete vybrat verzi rozhraní .NET Framework 4.0. Při přesměrování na rozhraní .NET Framework 4.5, ale revize kódu je potřeba zajistit, že nejsou neplatné identifikátory URI (včetně mezer) očekávané jako hodnoty atributů s datovým typem anyURI.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Změna orientace|

