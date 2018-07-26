### <a name="xml-schema-validation-is-stricter"></a>Je ověřování schématu XML přísnější

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5 je ověřování schématu XML přísnější. Jestliže použijete xsd:anyURI k vyhodnocení URI jako protokolu e-mailu a v URI jsou mezery, vyhodnocení selže. V předchozích verzích rozhraní .NET Framework ověření proběhlo úspěšně. Změna ovlivní pouze aplikace, které se zaměřují na rozhraní .NET Framework 4.5.|
|Návrh|V případě potřeby volnější ověřování rozhraní .NET Framework 4.0 ověřování aplikace může cílit verzi 4.0 rozhraní .NET Framework. Pokud mění se cílení na .NET Framework 4.5, však musí ujistit se, že nejsou neplatné identifikátory URI (s mezerami) stanovená jako hodnoty atributů s datovým typem anyURI provedena revize kódu.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Mění se cílení|

