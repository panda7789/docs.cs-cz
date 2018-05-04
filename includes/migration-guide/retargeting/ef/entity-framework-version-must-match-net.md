### <a name="entity-framework-version-must-match-the-net-framework-version"></a>Verze Entity Framework musí odpovídat verzi rozhraní .NET Framework

|   |   |
|---|---|
|Podrobnosti|Verze rozhraní .NET framework by si měly odpovídat verzi rozhraní entity framework. Rozhraní Entity Framework 5 se doporučuje pro rozhraní .NET Framework 4.5. Existují některé známé problémy s EF 4.x v rozhraní .NET Framework 4.5 projektu kolem <xref:System.ComponentModel.DataAnnotations>. V rozhraní .NET 4.5 tyto se přesunuly na jiném sestavení tak, že jsou problémy s určení, které poznámky k použití.|
|Návrh|Upgrade na rozhraní Entity Framework 5 pro rozhraní .NET Framework 4.5|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|Změna orientace|

