### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Chybí Přezdívka cílový Framework za následek 4.0 chování

|   |   |
|---|---|
|Podrobnosti|Aplikace bez <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> použít na úrovni bude sestavení automaticky spustit pomocí sémantika (adaptivní) rozhraní .NET Framework 4.0. K zajištění vysoké kvality, se doporučuje, aby se všechny binární soubory explicitně opatřená <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> označující verzi rozhraní .NET Framework, které byly vytvořené s nástroji. Všimněte si, že použití Přezdívka framework cíl v souboru projektu způsobí MSBuild pro automatické použití <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name>.|
|Návrh|A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> by měl být zadaný, buď prostřednictvím přidání atributu přímo k sestavení nebo zadáním cílové rozhraní v [souboru projektu nebo pomocí sady Visual Studio projektu grafickým uživatelským rozhraním vlastnosti](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio- managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx).|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|modul runtime|

