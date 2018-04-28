---
title: Přidání do formátu csproj pro .NET Core
description: Další informace o rozdílech mezi existující a .NET Core csproj soubory
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: ed1a25337ac1594d4ca748d0c6f79bdcc038a1e8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Přidání do formátu csproj pro .NET Core

Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunutí ze *project.json* k *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild). Další informace o syntaxi souboru obecné projektu a referenční informace najdete v tématu [soubor projektu nástroje MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentaci.  

## <a name="implicit-package-references"></a>Implicitní balíček odkazuje
Metapackages odkazují implicitně podle framework(s) cíl zadaný v `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost souboru projektu. `<TargetFrameworks>` je ignorována, pokud `<TargetFramework>` je zadaný, nezávisle na pořadí.

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp1.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp1.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a>Doporučení
Vzhledem k tomu `Microsoft.NETCore.App` nebo `NetStandard.Library` metapackages implicitně odkazují, naše doporučené osvědčené postupy jsou následující:

* Pokud je cílem .NET Core nebo .NET Standard, nemusí explicitní odkaz na `Microsoft.NETCore.App` nebo `NetStandard.Library` metapackages prostřednictvím `<PackageReference>` položku v souboru projektu.
* Pokud budete potřebovat na konkrétní verzi modulu runtime, pokud je cílem .NET Core, měli byste použít `<RuntimeFrameworkVersion>` vlastnost ve vašem projektu (například `1.0.4`) namísto odkazující metapackage.
    * K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) a je třeba daná oprava verzi 1.0.0 modul runtime LTS, např.
* Pokud potřebujete konkrétní verzi nástroje `NetStandard.Library` metapackage, pokud je cílem .NET Standard, můžete použít `<NetStandardImplicitPackageVersion>` vlastnost a sadu verze potřebujete.
* Není explicitně přidat nebo aktualizovat odkazy na buď `Microsoft.NETCore.App` nebo `NetStandard.Library` metapackage v projektech pro rozhraní .NET Framework. Pokud všechny verze `NetStandard.Library` je potřeba, když pomocí balíčku NuGet .NET Standard na základě, NuGet automaticky instaluje tuto verzi.

## <a name="default-compilation-includes-in-net-core-projects"></a>Výchozí kompilace zahrnuje v projektech .NET Core
S přechodem na *csproj* formátu v nejnovější verze sady SDK sídla výchozí zahrnuje a vyloučí pro kompilaci položky a vložené prostředky k souborům vlastnosti SDK. To znamená, že už muset zadat tyto položky v souboru projektu. 

Hlavním důvodem tohoto postupu je přehlednost v souboru projektu. Výchozí hodnoty, které se nacházejí v sadě SDK by měly zahrnovat nejběžnější případy použití, takže není nutné je opakovat v každém projektu, který vytvoříte. To vede k menší soubory projektu, které je mnohem snazší pochopit a také upravit ručně, v případě potřeby. 

Následující tabulka uvádí, které elementy a které [globs](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuté i vyloučené v sadě SDK: 

| Prvek           | Zahrnout glob                              | Vyloučit glob                                                  | Odebrat glob                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Kompilace           | \*\*/\*.cs (nebo jiné jazyková rozšíření) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | Není k dispozici                        |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | Není k dispozici                        |
| Žádné              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | - \*\*/\*.cs; \*\*/\*.resx |

Pokud máte globs ve vašem projektu a pokusíte se sestavení pomocí nejnovější SDK, získáte následující chybě:

> Duplicitní položky kompilace byly zahrnuty. .NET SDK zahrnuje kompilace položky z adresáře projektu ve výchozím nastavení. Můžete tyto položky odebrat ze souboru projektu, nebo nastavte vlastnost 'EnableDefaultCompileItems' na hodnotu "false", pokud chcete výslovně nezahrnete v souboru projektu. 

Chcete-li získat vyřešit tuto chybu, můžete odebrat explicitní `Compile` položky, které odpovídají těm, které jsou uvedené v předchozí tabulce, nebo můžete nastavit `<EnableDefaultCompileItems>` vlastnost, která má `false`, podobné výjimky:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
Nastavení této vlastnosti na `false` přepíší implicitní zahrnutí a chování se vrátí zpět na předchozí sady SDK, které jste museli zadat výchozí globs ve vašem projektu. 

Tato změna nedojde ke změně hlavní zahrnuje jiné mechanismy. Ale pokud chcete určit, například některé soubory získat publikována s vaší aplikací, můžete pořád použít známé mechanismy v *csproj* pro tento (například `<Content>` element).

`<EnableDefaultCompileItems>` pouze zakáže `Compile` globs, ale nemá žádný vliv na ostatní globs, jako implicitní `None` glob, která se vztahuje také na \*.cs položky. Z tohoto důvodu **Průzkumníku řešení** bude pokračovat zobrazit \*.cs položky v rámci projektu, které jsou zahrnuty jako `None` položky. Podobným způsobem, můžete použít `<EnableDefaultNoneItems>` zakázat implicitní `None` glob.

Chcete-li zakázat **všechny implicitní globs**, můžete nastavit `<EnableDefaultItems>` vlastnost `false` jako v následujícím příkladu:
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a>Doporučení
S csproj doporučujeme odebrat globs výchozí z projektu a přidávat jenom cesty k souborům s globs pro tyto artefakty, které vaše aplikace nebo knihovna potřebuje pro různé scénáře (například za běhu a vytváření balíčků NuGet).

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Jak zjistit celý projekt jako MSBuild uvidí ho

Když tyto změny csproj výrazně zjednodušit soubory projektu, můžete chtít najdete v části plně rozšířené projektu jako MSBuild uvidí ho, jakmile jsou součástí sady SDK a jeho cíle. Předběžné zpracování projektu s [ `/pp` přepínač](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) příkaz, který ukazuje soubory, které jsou importovány, jejich zdroje a jejich příspěvky k sestavení bez ve skutečnosti sestavení projektu:

`dotnet msbuild /pp:fullproject.xml`

Pokud projekt má více cílové rozhraní, se musí výsledky příkazu zaměřit na pouze jeden z nich tak, že zadáte jako ve vlastnosti nástroje MSBuild:

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a>Přidání

### <a name="sdk-attribute"></a>Atribut SDK 
`<Project>` Element *.csproj* soubor má nový atribut názvem `Sdk`. `Sdk` Určuje, které SDK bude používán v projektu. Sadu SDK, jako [rozvrstvení dokumentu](cli-msbuild-architecture.md) popisuje, je sada MSBuild [úlohy](/visualstudio/msbuild/msbuild-tasks) a [cíle](/visualstudio/msbuild/msbuild-targets) , můžete vytvořit kódu .NET Core. Jsme dodávat dvě hlavní sady SDK nástroje .NET Core:

1. .NET Core SDK s ID `Microsoft.NET.Sdk`
2. .NET Core web SDK s ID `Microsoft.NET.Sdk.Web`

Je potřeba mít `Sdk` nastaven atribut na jednu z těchto ID na `<Project>` element Chcete-li použít nástroje .NET Core a sestavení kódu. 

### <a name="packagereference"></a>PackageReference
Položka, která určuje závislostí NuGet v projektu. `Include` Atribut určuje ID balíčku. 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Version
`Version` Určuje verzi balíčku, který má obnovit. Atribut respektuje pravidla [verze NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma. Výchozí chování je v případě shody přesnou verzi. Například zadání `Version="1.2.3"` je ekvivalentní NuGet zápis `[1.2.3]` pro přesnou 1.2.3 verze balíčku.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets a PrivateAssets
`IncludeAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by měl být využívány. 

`ExcludeAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by neměl být využívány.

`PrivateAssets` atribut určuje, jaké prostředky, které patří do balíčku určeného `<PackageReference>` by měl být využívány ale, že by neměl toku do další projektu. 

> [!NOTE]
> `PrivateAssets` je ekvivalentní *project.json*/*xproj* `SuppressParent` element.

Tyto atributy mohou obsahovat jednu nebo více z následujících položek:

* `Compile` – jsou k dispozici ke kompilaci proti obsah složky lib.
* `Runtime` – distribuují obsah složky modulu runtime.
* `ContentFiles` – obsah *contentfiles* složky se používá.
* `Build` – props/cíle ve složce sestavení se používají.
* `Native` – obsah z nativní prostředky se zkopírují do výstupní složky pro modul runtime.
* `Analyzers` – Analyzátory se používají.

Alternativně může obsahovat atribut:

* `None` – žádné prostředky se používají.
* `All` – všechny prostředky používají.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference
`<DotNetCliToolReference>` Item – prvek určuje nástroj příkazového řádku, který chce uživatel obnovit v kontextu projektu. Je to náhrada za `tools` uzlu v *project.json*. 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a>Version
`Version` Určuje verzi balíčku, který má obnovit. Atribut respektuje pravidla [verze NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma. Výchozí chování je v případě shody přesnou verzi. Například zadání `Version="1.2.3"` je ekvivalentní NuGet zápis `[1.2.3]` pro přesnou 1.2.3 verze balíčku.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers
`<RuntimeIdentifiers>` Vám umožňuje určit seznam oddělený středníkem [Runtime identifikátorů (RID)](../rid-catalog.md) pro projekt. Povolit identifikátorů RID publikování samostatná nasazení. 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier
`<RuntimeIdentifier>` Element umožňuje určit pouze jeden [identifikátor Runtime (RID)](../rid-catalog.md) pro projekt. Povolit identifikátorů RID publikování samostatná nasazení. 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a>PackageTargetFallback 
`<PackageTargetFallback>` Element umožňuje určit sadu kompatibilní cíle, který se má použít při obnovování balíčků. Je navržena k umožnění balíčků, které používají dotnet [TxM (cíl x přezdívka)](/nuget/schema/target-frameworks) pracovat s balíčky, které nejsou deklarovat dotnet TxM. Pokud váš projekt používá dotnet TxM, pak všechny balíčky, které závisí na musí také mít dotnet TxM, pokud přidáte `<PackageTargetFallback>` do projektu, aby bylo možné povolit platformy bez dotnet. aby bylo kompatibilní s dotnet. 

Následující příklad uvádí případech přejít pro všechny cíle ve vašem projektu: 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

Následující příklad určuje případech přejít jenom pro `netcoreapp1.0` cíl:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a>Vlastnosti metadat NuGet
S přechodem na nástroje MSbuild, byl přesunut vstupní metadata, která se používá při balení balíček NuGet z *project.json* k *.csproj* soubory. Vstupní hodnoty jsou vlastnosti nástroje MSBuild, takže budou muset přejít v rámci `<PropertyGroup>` skupiny. Následuje seznam vlastností, které se používají jako vstupy pro proces okolních při použití `dotnet pack` příkaz nebo `Pack` MSBuild cíle, který je součástí sady SDK. 

### <a name="ispackable"></a>IsPackable
Logická hodnota, která určuje, zda lze zabalit projektu. Výchozí hodnota je `true`. 

### <a name="packageversion"></a>PackageVersion
Určuje verzi, která bude mít výsledný balíčku. Přijme všechny formy řetězec verze NuGet. Výchozí hodnota je hodnota `$(Version)`, která je vlastnosti `Version` v projektu. 

### <a name="packageid"></a>ID balíčku
Určuje název pro výsledný balíček. Pokud není zadáno, `pack` operace bude použita výchozí pomocí `AssemblyName` nebo název adresáře jako název balíčku. 

### <a name="title"></a>Název
Lidské popisný název balíčku, obvykle používaných v zobrazení uživatelského rozhraní na nuget.org a Správce balíčků v sadě Visual Studio. Pokud není zadáno, bude místo něj použita ID balíčku.

### <a name="authors"></a>Autoři
Seznam balíčků autoři, odpovídající profil názvy v nuget.org oddělených středníkem. Tyto jsou zobrazeny v galerii NuGet v nuget.org a jsou používané pro křížovou balíčky autory stejné.

### <a name="description"></a>Popis
Dlouhý popis balíčku pro zobrazení uživatelského rozhraní.

### <a name="copyright"></a>Copyright
Údaje o autorských právech pro balíček.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance
Logická hodnota, která určuje, jestli klient musí zobrazovat výzvu k příjemce tak, aby přijímal licenční balíček před instalací balíčku. Výchozí hodnota je `false`.

### <a name="packagelicenseurl"></a>PackageLicenseUrl
Adresu URL licence, která se vztahuje na balíčku.

### <a name="packageprojecturl"></a>PackageProjectUrl
Zobrazí adresu URL pro domovskou stránku balíčku, často se zobrazí v uživatelském rozhraní a také nuget.org.

### <a name="packageiconurl"></a>PackageIconUrl
Adresu URL pro bitovou kopii 64 x 64 s průhledným pozadím chcete použít jako ikonu balíčku v zobrazení uživatelského rozhraní.

### <a name="packagereleasenotes"></a>PackageReleaseNotes
Poznámky k verzi pro balíček.

### <a name="packagetags"></a>PackageTags
Seznam značek oddělených středníkem, který označuje balíčku.

### <a name="packageoutputpath"></a>PackageOutputPath
Určuje výstupní cesta, ve kterém se zahodí sbalené balíčku. Výchozí hodnota je `$(OutputPath)`. 

### <a name="includesymbols"></a>IncludeSymbols
Tato logická hodnota určuje, zda by měl balíček tehdy, když je zabalit projektu vytvoření balíčku další symboly. Bude mít tento balíček *. symbols.nupkg* rozšíření a bude kopírovat soubory PDB společně s knihovnou DLL a ostatní výstupní soubory.

### <a name="includesource"></a>IncludeSource
Tato logická hodnota určuje, jestli proces pack by měl vytvořit zdroj balíčku. Zdrojový balíček obsahuje knihovny zdrojového kódu a také soubory PDB. Zdrojové soubory jsou umístěny v části `src/ProjectName` adresář ve výsledném souboru balíčku. 

### <a name="istool"></a>IsTool
Určuje, zda všechny výstupní soubory se zkopírují do *nástroje* složky místo *lib* složky. Všimněte si, že se to neliší od `DotNetCliTool` , která je určena podle nastavení `PackageType` v *.csproj* souboru.

### <a name="repositoryurl"></a>RepositoryUrl
Určuje adresu URL pro úložiště, kde se nachází zdrojový kód pro balíček nebo ze které je právě vytvořen. 

### <a name="repositorytype"></a>RepositoryType
Určuje typ úložiště. Výchozí hodnota je "git". 

### <a name="nopackageanalysis"></a>NoPackageAnalysis
Určuje, že sada by neměl spustit analysis balíčku po vytvoření balíčku.

### <a name="minclientversion"></a>MinClientVersion
Určuje minimální verzi klienta NuGet, který můžete nainstalovat tento balíček vynucováno nuget.exe a Správce balíčků Visual Studio.

### <a name="includebuildoutput"></a>IncludeBuildOutput
Tato logické hodnoty Určuje, zda by měl sestavení výstupu sestavení do mnoha funkcemi *.nupkg* souboru nebo ne.

### <a name="includecontentinpack"></a>IncludeContentInPack
Tato logická hodnota určuje, zda všechny položky, které mají typ `Content` budou zahrnuty do výsledného balíček automaticky. Výchozí hodnota je `true`. 

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder
Určuje složku, kam umístit výstupu sestavení. Výstup sestavení (a ostatní výstupní soubory) se zkopírují do jejich odpovídajících framework složky.

### <a name="contenttargetfolders"></a>ContentTargetFolders
Tato vlastnost určuje, kde se má zobrazit všechny soubory obsahu, pokud výchozí umístění `PackagePath` není zadaný pro ně. Výchozí hodnota je "obsah; contentFiles".

### <a name="nuspecfile"></a>NuspecFile
Relativní nebo absolutní cesta k *příponou .nuspec* soubor používá pro okolních. 

> [!NOTE]
> Pokud *příponou .nuspec* je zadán, použije se **výhradně** pro balení informace a všechny informace v projektech nepoužívá. 

### <a name="nuspecbasepath"></a>NuspecBasePath
Základní cesta pro *příponou .nuspec* souboru.

### <a name="nuspecproperties"></a>NuspecProperties
Středníky oddělený seznam klíč = hodnota páry.
