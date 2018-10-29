---
title: Dodatky k formátu csproj pro .NET Core
description: Další informace o rozdílech mezi stávající a soubory csproj .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.openlocfilehash: 3de168b8cebeb435a45861138aea26580663c135
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50203953"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Dodatky k formátu csproj pro .NET Core

Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunu z *project.json* k *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild). Další informace o syntaxi souboru obecné projektu a odkaz, naleznete v tématu [souboru projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentaci.  

## <a name="implicit-package-references"></a>Odkazy na implicitní balíček
Metabalíčky jsou implicitně odkazovat podle cílové architekturu podle `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost souboru projektu. `<TargetFrameworks>` se ignoruje, pokud `<TargetFramework>` je zadaný, nezávisle na pořadí.

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a>Doporučení
Protože `Microsoft.NETCore.App` nebo `NetStandard.Library` metabalíčky jsou implicitně odkazovat, naše doporučené osvědčené postupy jsou následující:

* Při cílení na .NET Core nebo .NET Standard, nikdy nemůžete mít explicitní odkaz na `Microsoft.NETCore.App` nebo `NetStandard.Library` metabalíčky prostřednictvím `<PackageReference>` položky v souboru projektu.
* Pokud potřebujete konkrétní verzi modulu runtime při cílení na .NET Core, měli byste použít `<RuntimeFrameworkVersion>` vlastnost v projektu (například `1.0.4`) namísto odkazování Microsoft.aspnetcore.all.
    * K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) a potřebujete oprav konkrétní verze 1.0.0 LTS běhu.
* Pokud potřebujete konkrétní verzi `NetStandard.Library` Microsoft.aspnetcore.all při cílení na .NET Standard, můžete použít `<NetStandardImplicitPackageVersion>` vlastnost a nastavte verzi budete potřebovat.
* Není explicitně přidat nebo aktualizovat odkazy na buď `Microsoft.NETCore.App` nebo `NetStandard.Library` Microsoft.aspnetcore.all v projektech .NET Framework. Pokud všechny verze `NetStandard.Library` je potřeba při použití balíčku NuGet pro .NET Standard na základě, NuGet automaticky instaluje tuto verzi.

## <a name="default-compilation-includes-in-net-core-projects"></a>Obsahuje výchozí kompilace v projektech .NET Core
S přechodem na *csproj* formátu v nejnovější verze sady SDK, přešli jsme výchozí zahrnuje a nezahrnuje pro položky kompilace a vložené prostředky, které vlastnosti soubory sady SDK. To znamená, že už nemusíte určit tyto položky v souboru projektu. 

Hlavním důvodem pro to je přehlednost v souboru projektu. Výchozí hodnoty, které jsou k dispozici v sadě SDK by měly pokrývat nejběžnější případy použití, takže není nutné opakovat v každém projektu, který vytvoříte. To vede k menší soubory projektu, které jsou mnohem snazší porozumět, stejně jako upravit ručně, v případě potřeby. 

V následující tabulce jsou uvedeny které elementy a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuté i vyloučené v sadě SDK: 

| Prvek           | Zahrnout glob                              | Vyloučit glob                                                  | Odebrat glob                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Kompilace           | \*\*/\*.cs (nebo jiných jazykových rozšíření) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | Není k dispozici                        |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | Není k dispozici                        |
| Žádné              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | - \*\*/\*.cs; \*\*/\*.resx |

Pokud máte globy ve vašem projektu a zkusíte sestavit pomocí nejnovější SDK, zobrazí se vám chybová zpráva:

> Duplicitní položky kompilace byly zahrnuty. Sady .NET SDK obsahuje ve výchozím nastavení kompilace položky z adresáře projektu. Můžete tyto položky odebrat ze svého souboru projektu, nebo nastavte vlastnost 'EnableDefaultCompileItems' na hodnotu false' Pokud chcete explicitně zahrnout je do souboru projektu. 

Aby bylo možné tuto chybu vyřešit, buď odstraněním explicitní `Compile` položky, které odpovídají těm, které jsou uvedené v předchozí tabulce, nebo můžete nastavit `<EnableDefaultCompileItems>` vlastnost `false`, tímto způsobem:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
Nastavení této vlastnosti na `false` přepíše implicitního zahrnutí a chování se vrátí zpět na předchozí sady SDK, které jste museli zadat výchozí globy ve vašem projektu. 

Tato změna neprovede žádné změny v hlavním obsahuje jiné mechanismy. Ale pokud chcete zadat, například některé soubory se publikovat s vaší aplikací, můžete stále použít známé mechanismy ve *csproj* pro daný (například `<Content>` element).

`<EnableDefaultCompileItems>` pouze zakáže `Compile` globy, ale nemá vliv na ostatní globy, jako jsou implicitní `None` glob, která se také vztahuje na \*.cs položky. Proto **Průzkumníka řešení** bude dál zobrazovat \*.cs položky jako součást projektu, jako `None` položky. Podobným způsobem, můžete použít `<EnableDefaultNoneItems>` zakázat implicitní `None` glob.

Chcete-li zakázat **všechny implicitní globy**, můžete nastavit `<EnableDefaultItems>` vlastnost `false` jako v následujícím příkladu:
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a>Doporučení
S csproj doporučujeme, abyste výchozí globy odeberte z projektu a přidat jenom cesty k souborům s globy pro tyto artefakty, které vaše aplikace/knihovna potřebuje pro různé scénáře (například modul runtime a zabalení NuGet).

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Zobrazení celého projektu, jak ho uvidí MSBuild

Zatímco tyto změny csproj výrazně zjednodušit soubory projektu, můžete chtít zobrazit plně rozšířené projektu jako MSBuild ji vidí, jakmile jsou zahrnuty v sadě SDK a cíle. Předběžné zpracování projektu s [ `/pp` přepnout](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) příkaz, který ukazuje, které soubory se importují, jejich zdroje a svoje příspěvky k sestavení bez ve skutečnosti sestavení projektu:

`dotnet msbuild -pp:fullproject.xml`

Pokud projekt obsahuje více cílových platforem, by měl výsledky příkazu, zaměřuje na pouze jeden z nich tak, že zadáte jako vlastnost MSBuild:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Přidání

### <a name="sdk-attribute"></a>Atribut SDK 
`<Project>` Elementu *.csproj* soubor obsahuje nový atribut volá `Sdk`. `Sdk` Určuje, které sada SDK se používá v projektu. Sady SDK, jako [rozvržení dokumentu](cli-msbuild-architecture.md) popisuje, je sada MSBuild [úlohy](/visualstudio/msbuild/msbuild-tasks) a [cíle](/visualstudio/msbuild/msbuild-targets) , které můžete vytvářet kód .NET Core. Dodáváme tři hlavní sady SDK s nástroji .NET Core:

1. .NET Core SDK s ID `Microsoft.NET.Sdk`
2. .NET Core web SDK s ID `Microsoft.NET.Sdk.Web`
3. Knihovny tříd Razor .NET Core SDK s ID nástroje `Microsoft.NET.Sdk.Razor`

Je potřeba mít `Sdk` nastavený atribut na jednu z těchto ID na `<Project>` prvku abyste mohli použít nástroje pro .NET Core a vytváření kódu. 

### <a name="packagereference"></a>PackageReference
Položka, která určuje závislostí NuGet v projektu. `Include` Atribut určuje ID balíčku. 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Version
`Version` Určuje verzi balíčku, který se obnovit. Atribut respektuje pravidla [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma. Výchozí chování je shoda přesnou verzi. Například zadání `Version="1.2.3"` je ekvivalentní zápisu NuGet `[1.2.3]` pro přesné 1.2.3 verzi balíčku.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets a PrivateAssets
`IncludeAssets` atribut určuje, jaké prostředky, které patří do určeného balíčku `<PackageReference>` by měl používat. 

`ExcludeAssets` atribut určuje, jaké prostředky, které patří do určeného balíčku `<PackageReference>` by neměla využívat.

`PrivateAssets` atribut určuje, jaké prostředky, které patří do určeného balíčku `<PackageReference>` by měl používat, ale ne směrovat do příští projekt. 

> [!NOTE]
> `PrivateAssets` je ekvivalentní *project.json*/*xproj* `SuppressParent` elementu.

Tyto atributy mohou obsahovat jednu nebo více z následujících položek:

* `Compile` – je možné kompilovat proti obsah složky lib.
* `Runtime` – obsah složky modulu runtime jsou distribuovány.
* `ContentFiles` – obsah *contentfiles* složky se používají.
* `Build` – vlastnosti a cíle ve složce sestavení se používají.
* `Native` – obsah z nativní prostředky se zkopíruje do výstupní složky pro modul runtime.
* `Analyzers` – Analyzátory se používají.

Alternativně může obsahovat atribut:

* `None` – žádné prostředky se používají.
* `All` – všechny prostředky se používají.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference
`<DotNetCliToolReference>` prvek položky určuje nástroj rozhraní příkazového řádku, který uživatel chce obnovit v kontextu projektu. Je náhradou za `tools` uzel v *project.json*. 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a>Version
`Version` Určuje verzi balíčku, který se obnovit. Atribut respektuje pravidla [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma. Výchozí chování je shoda přesnou verzi. Například zadání `Version="1.2.3"` je ekvivalentní zápisu NuGet `[1.2.3]` pro přesné 1.2.3 verzi balíčku.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers
`<RuntimeIdentifiers>` Element umožňuje určit seznam oddělený středníkem [Runtime identifikátorů (RID)](../rid-catalog.md) pro projekt. Identifikátory RID povolit publikování samostatná nasazení. 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier
`<RuntimeIdentifier>` Element umožňuje určit pouze jeden [identifikátor modulu Runtime (RID)](../rid-catalog.md) pro projekt. Identifikátory RID povolit publikování samostatná nasazení. 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a>PackageTargetFallback 
`<PackageTargetFallback>` Element slouží k určení sady cílů kompatibilní se použije při obnovování balíčků. Je navržen tak, aby balíčky, které používají dotnet [TxM (Moniker cílového x)](/nuget/schema/target-frameworks) pracovat s balíčky, které není deklarovat dotnet TxM. Pokud váš projekt používá dotnet TxM, pak všechny balíčky, které závisí na musí také mít dotnet TxM, pokud přidáte `<PackageTargetFallback>` do vašeho projektu, aby bylo možné povolit bez dotnet platformy se kvůli kompatibilitě s dotnet. 

Následující příklad uvádí náhrad pro všechny cíle v projektu: 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

Následující příklad určuje náhrad pouze `netcoreapp2.1` cíl:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a>Vlastnosti metadat NuGet
S přechodem na MSbuild, přesunuli jsme vstupní metadata, která se používá při balení balíček NuGet *project.json* k *.csproj* soubory. Vstupy jsou vlastnosti nástroje MSBuild, takže budou muset přejít v rámci `<PropertyGroup>` skupiny. Tady je seznam vlastností, které se používají jako vstupy do procesu zabalení, při použití `dotnet pack` příkazu nebo `Pack` MSBuild cíl, který je součástí sady SDK. 

### <a name="ispackable"></a>IsPackable
Logická hodnota určující, zda lze zabalit projekt. Výchozí hodnota je `true`. 

### <a name="packageversion"></a>PackageVersion
Určuje verzi, bude výsledný balíček. Přijímá všechny formy řetězec verze NuGet. Výchozí hodnota je hodnota `$(Version)`, to znamená, vlastnosti `Version` v projektu. 

### <a name="packageid"></a>ID balíčku
Určuje název pro výsledný balíček. Pokud není zadán, `pack` operace budou ve výchozím nastavení použití `AssemblyName` nebo název adresáře jako název balíčku. 

### <a name="title"></a>Název
Lidské popisný název balíčku, obvykle používaných v uživatelském rozhraní na webech nuget.org a Správce balíčků v sadě Visual Studio. Pokud se nezadá, ID balíčku, který se používá místo toho.

### <a name="authors"></a>Autoři
Středníkem oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org. Tyto jsou zobrazeny v galerii NuGet na nuget.org a slouží k křížový odkaz balíčky stejné autory.

### <a name="description"></a>Popis
Dlouhý popis balíčku zobrazí v uživatelském rozhraní.

### <a name="copyright"></a>Copyright
Podrobnosti o autorských právech pro balíček.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance
Logická hodnota určující, zda klient musí požádat spotřebitele o přijetí licence balíčku před instalací balíčku. Výchozí hodnota je `false`.

### <a name="packagelicenseurl"></a>PackageLicenseUrl
Adresu URL licence, která se vztahuje na balíček.

### <a name="packageprojecturl"></a>PackageProjectUrl
Adresa URL domovské stránky balíčku, často zobrazuje v uživatelském rozhraní nuget.org.

### <a name="packageiconurl"></a>PackageIconUrl
Adresa URL pro bitovou kopii 64 x 64 s průhledným pozadím použít jako ikona pro balíček zobrazená v uživatelském rozhraní.

### <a name="packagereleasenotes"></a>PackageReleaseNotes
Zpráva k vydání verze pro balíček.

### <a name="packagetags"></a>PackageTags
Středníkem oddělený seznam značek, který určuje balíček.

### <a name="packageoutputpath"></a>PackageOutputPath
Určuje výstupní cesta, ve kterém se zahodí komprimovaný balíček. Výchozí hodnota je `$(OutputPath)`. 

### <a name="includesymbols"></a>IncludeSymbols
Tato logická hodnota označuje, zda by měl balíček tehdy, když je zabalit projekt vytvořit balíček dalších symbolů. Tento balíček bude mít *. symbols.nupkg* rozšíření a bude kopírovat soubory PDB spolu s knihovny DLL a ostatních výstupních souborů.

### <a name="includesource"></a>IncludeSource
Tato logická hodnota značí, zda proces pack by měl vytvářet zdrojového balíčku. Zdrojový balíček obsahuje knihovny zdrojový kód a soubory PDB. Zdrojové soubory jsou umístěny na `src/ProjectName` adresáře ve výsledném souboru balíčku. 

### <a name="istool"></a>IsTool
Určuje, zda jsou všechny výstupní soubory zkopírovány do *nástroje* složky namísto *lib* složky. Všimněte si, že se liší od `DotNetCliTool` který je určený nastavením `PackageType` v *.csproj* souboru.

### <a name="repositoryurl"></a>RepositoryUrl
Určuje adresu URL úložiště, kde se nachází zdrojový kód pro balíček a/nebo z kterého se má být sestaven. 

### <a name="repositorytype"></a>RepositoryType
Určuje typ úložiště. Výchozí hodnota je "git". 

### <a name="nopackageanalysis"></a>NoPackageAnalysis
Určuje, že balíček by neměl balíčku spustit jeho analýzu po sestavení.

### <a name="minclientversion"></a>MinClientVersion
Určuje minimální verzi klienta NuGet, který můžete nainstalovat tento balíček, vynucuje nuget.exe a Správce balíčků sady Visual Studio.

### <a name="includebuildoutput"></a>IncludeBuildOutput
Tato logické hodnoty Určuje, zda sestavení výstupu sestavení by měl být zabaleny do *.nupkg* souboru nebo ne.

### <a name="includecontentinpack"></a>IncludeContentInPack
Tato logická hodnota určuje, zda všechny položky, které mají typ `Content` výsledný balíček bude obsahovat automaticky. Výchozí hodnota je `true`. 

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder
Určuje složku, kam chcete umístit výstup sestavení. Výstup sestavení (a ostatních výstupních souborů) jsou zkopírovány do složky jejich příslušných rozhraní framework.

### <a name="contenttargetfolders"></a>ContentTargetFolders
Tato vlastnost určuje výchozí umístění, kde by měl přejděte všechny soubory obsahu, pokud `PackagePath` není zadaný pro ně. Výchozí hodnota je "obsah; contentFiles".

### <a name="nuspecfile"></a>NuspecFile
Relativní nebo absolutní cesta k *souboru .nuspec* souboru se používají pro balení. 

> [!NOTE]
> Pokud *souboru .nuspec* soubor zadán, použije se **výhradně** pro balení informace a informace v projektech se nepoužívá. 

### <a name="nuspecbasepath"></a>NuspecBasePath
Základní cesta pro *souboru .nuspec* souboru.

### <a name="nuspecproperties"></a>NuspecProperties
Středníkem oddělený seznam klíč = dvojice hodnot.

## <a name="assemblyinfo-properties"></a>Vlastnosti souboru AssemblyInfo
[Atributy sestavení](../../framework/app-domains/set-assembly-attributes.md) , která se obvykle používají ve *AssemblyInfo* souboru jsou teď automaticky generovány z vlastností.

### <a name="properties-per-attribute"></a>Každý atribut vlastnosti

Každý atribut má vlastnosti, které řídí jeho obsah a druhou pro zakázání jeho generaci, jak je znázorněno v následující tabulce:

| Atribut                                                      | Vlastnost               | Vlastnost pro zákaz                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

Poznámky:

* `AssemblyVersion` a `FileVersion` výchozí je převést hodnotu `$(Version)` bez přípony. Například pokud `$(Version)` je `1.2.3-beta.4`, pak bude hodnota `1.2.3`.
* `InformationalVersion` Výchozí hodnota je hodnota `$(Version)`.
* `InformationalVersion` má `$(SourceRevisionId)` připojí, pokud vlastnost je k dispozici. Je možné ho zakázat, pomocí `IncludeSourceRevisionInInformationalVersion`.
* `Copyright` a `Description` vlastnosti jsou také používány pro NuGet metadat.
* `Configuration` je sdílený v procesu sestavení a nastavené přes `--configuration` parametr `dotnet` příkazy.

### <a name="generateassemblyinfo"></a>GenerateAssemblyInfo 
Logická hodnota, která povolí nebo zakáže všechny generování souboru AssemblyInfo. Výchozí hodnota je `true`. 

### <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile 
Cestu k souboru informací o vygenerované sestavení. Ve výchozím nastavení v souboru `$(IntermediateOutputPath)` adresáře (obj).
