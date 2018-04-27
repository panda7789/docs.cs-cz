### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Vytváření rozhraní Entity Framework edmx s Visual Studio 2013 může selhat s chybou MSB4062 pomocí EntityDeploySplit nebo EntityClean úloh

|   |   |
|---|---|
|Podrobnosti|Nástroje MSBuild 12.0 (zahrnutá v sadě Visual Studio 2013) změnit umístění souborů nástroje MSBuild, způsobuje starší soubory cíle Entity Framework není platný. Výsledkem je, že <code>EntityDeploySplit</code> a <code>EntityClean</code> selhání úloh, protože se nepodařilo najít <code>Microsoft.Data.Entity.Build.Tasks.dll</code>. Upozorňujeme, že toto rozdělení se kvůli změně sady nástrojů (MSBuild/VS) není z důvodu změny rozhraní .NET Framework. Pouze dojde při upgradu nástrojů pro vývojáře, není při upgradu jenom rozhraní .NET Framework.|
|Návrh|Entity Framework cíle soubory se vyřešilo pro práci s novinkou MSBuild rozložení v rozhraní .NET Framework 4.6. Upgrade na tuto verzi rozhraní Framework, bude tento problém vyřešit. Alternativně [to](http://stackoverflow.com/a/24249247/131944) alternativní řešení lze opravit cíle soubory přímo.|
|Rozsah|Hlavní|
|Version|4.5.1|
|Typ|Změna orientace|

