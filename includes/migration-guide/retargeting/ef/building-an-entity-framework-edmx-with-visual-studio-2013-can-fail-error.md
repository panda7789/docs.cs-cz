### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Sestavování Entity Framework edmx pomocí sady Visual Studio 2013 může selhat s chybou MSB4062, pokud používáte úkoly EntityDeploySplit nebo EntityClean

|   |   |
|---|---|
|Podrobnosti|Nástroj MSBuild 12.0 nástroje (zahrnutý v sadě Visual Studio 2013) změnit umístění souborů nástroje MSBuild, způsobí starší soubory cíle Entity Framework je neplatná. Důsledkem toho pak bude <code>EntityDeploySplit</code> a <code>EntityClean</code> úloha nebude úspěšná, protože se nepodařilo najít <code>Microsoft.Data.Entity.Build.Tasks.dll</code>. Upozorňujeme, že toto přerušení z důvodu změny sady nástrojů (MSBuild/VS), není kvůli změně rozhraní .NET Framework. Tato hodnota se vrátí pouze při upgradu nástroje pro vývojáře, ne v případě upgrade pouze rozhraní .NET Framework.|
|Návrh|Entity Framework cíle soubory odstraněny pro práci s novinkou systému rozložení MSBuild v rozhraní .NET Framework 4.6. Upgrade na tuto verzi rozhraní Framework bude tento problém vyřešit. Alternativně [to](http://stackoverflow.com/a/24249247/131944) řešení je možné opravovat soubory cíle přímo.|
|Rozsah|Hlavní|
|Version|4.5.1|
|Typ|Mění se cílení|

