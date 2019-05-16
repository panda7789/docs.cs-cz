---
title: Dodatky k formátu csproj pro .NET Core
description: Další informace o rozdílech mezi stávající a soubory csproj .NET Core
ms.date: 04/08/2019
ms.openlocfilehash: 9c1f084af68010632cbe595858b2f242d37af598
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631806"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Dodatky k formátu csproj pro .NET Core

Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunu z *project.json* k *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild). Další informace o syntaxi souboru obecné projektu a odkaz, naleznete v tématu [souboru projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentaci.

## <a name="implicit-package-references"></a>Odkazy na implicitní balíček

Metabalíčky jsou implicitně odkazovat podle cílové architekturu podle `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost souboru projektu. `<TargetFrameworks>` se ignoruje, pokud `<TargetFramework>` je zadaný, nezávisle na pořadí. Další informace najdete v tématu [balíčky, metabalíčky a architektury](../packages.md). 

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

Protože `Microsoft.NETCore.App` nebo `NETStandard.Library` metabalíčky jsou implicitně odkazovat, naše doporučené osvědčené postupy jsou následující:

* Při cílení na .NET Core nebo .NET Standard, nikdy nemůžete mít explicitní odkaz na `Microsoft.NETCore.App` nebo `NETStandard.Library` metabalíčky prostřednictvím `<PackageReference>` položky v souboru projektu.
* Pokud potřebujete konkrétní verzi modulu runtime při cílení na .NET Core, měli byste použít `<RuntimeFrameworkVersion>` vlastnost v projektu (například `1.0.4`) namísto odkazování Microsoft.aspnetcore.all.
  * K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) a potřebujete oprav konkrétní verze 1.0.0 LTS běhu.
* Pokud potřebujete konkrétní verzi `NETStandard.Library` Microsoft.aspnetcore.all při cílení na .NET Standard, můžete použít `<NetStandardImplicitPackageVersion>` vlastnost a nastavte verzi budete potřebovat.
* Není explicitně přidat nebo aktualizovat odkazy na buď `Microsoft.NETCore.App` nebo `NETStandard.Library` Microsoft.aspnetcore.all v projektech .NET Framework. Pokud všechny verze `NETStandard.Library` je potřeba při použití balíčku NuGet pro .NET Standard na základě, NuGet automaticky instaluje tuto verzi.

## <a name="implicit-version-for-some-package-references"></a>Implicitní verze pro některé odkazy na balíček

Většina použití [ `<PackageReference>` ](#packagereference) vyžadují nastavení `Version` atribut k určení verze balíčku NuGet, který se má použít. Pokud používáte .NET Core 2.1 nebo 2.2 a odkazující [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) nebo [metabalíček](/aspnet/core/fundamentals/metapackage), ale atribut je zbytečné. .NET Core SDK můžete automaticky vybrat verzi tyto balíčky, které by měla sloužit.

### <a name="recommendation"></a>Doporučení

Při odkazování `Microsoft.AspNetCore.App` nebo `Microsoft.AspNetCore.All` balíčky, nezadávejte jejich verze. Pokud není zadána verze, sada SDK může vytvořit upozornění NETSDK1071. Chcete-li opravit toto upozornění odeberte verzi balíčku jako v následujícím příkladu:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> Známý problém: .NET Core 2.1 SDK podporuje tuto syntaxi jen v případě, že projekt používá také Microsoft.NET.Sdk.Web. Tím je vyřešeno v .NET Core 2.2 SDK.

Tyto odkazy do ASP.NET Core metabalíčky mají mírně odlišné chování než nejvíce normální balíčky NuGet. [Nasazení závisí na architektuře](../deploying/index.md#framework-dependent-deployments-fdd) aplikací, které automaticky používají tyto metabalíčky využít sdílené architektuře ASP.NET Core. Při použití metabalíčky, **žádné** nasazení se aplikace používají prostředky z balíčků odkazovaných ASP.NET Core NuGet – sdílené architektuře ASP.NET Core obsahuje tyto prostředky. Prostředky v rámci sdílené jsou optimalizované pro cílovou platformu pro zlepšení času spuštění aplikace. Další informace o sdílené architektuře, najdete v části [vytváření distribučních balíčků .NET Core](../build/distribution-packaging.md).

Pokud verze *je* zadán, je považován za *minimální* sdílené architektuře ASP.NET Core pro nasazení závisí na architektuře a jako verzi *přesné* verze pro samostatná nasazení. To může mít následující důsledky:

* Pokud verze modulu ASP.NET Core nainstalována na serveru je nižší než verze zadaná v PackageReference, proces .NET Core se nespustí. Aktualizace Microsoft.aspnetcore.all jsou dostupné na NuGet.org, často předtím, než byly provedeny aktualizace k dispozici v hostitelských prostředích, jako je Azure. Aktualizace verze na PackageReference pro ASP.NET Core může způsobit selhání nasazené aplikace.
* Pokud je aplikace nasazená jako [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd), aplikace nemusí obsahovat nejnovější aktualizace zabezpečení pro .NET Core. Pokud není zadána verze, sady SDK do samostatná nasazení automaticky zahrnout nejnovější verzi aplikace ASP.NET Core.

## <a name="default-compilation-includes-in-net-core-projects"></a>Obsahuje výchozí kompilace v projektech .NET Core

S přechodem na *csproj* formátu v nejnovější verze sady SDK, přešli jsme výchozí zahrnuje a nezahrnuje pro položky kompilace a vložené prostředky, které vlastnosti soubory sady SDK. To znamená, že už nemusíte určit tyto položky v souboru projektu.

Hlavním důvodem pro to je přehlednost v souboru projektu. Výchozí hodnoty, které jsou k dispozici v sadě SDK by měly pokrývat nejběžnější případy použití, takže není nutné opakovat v každém projektu, který vytvoříte. To vede k menší soubory projektu, které jsou mnohem snazší porozumět, stejně jako upravit ručně, v případě potřeby.

V následující tabulce jsou uvedeny které elementy a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuté i vyloučené v sadě SDK:

| Prvek           | Zahrnout glob                              | Vyloučit glob                                                  | Odebrat glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Kompilace           | \*\*/\*.cs (nebo jiných jazykových rozšíření) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | Není k dispozici                      |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | Není k dispozici                      |
| Žádný              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*.cs; \* \* / \*resx   |

> [!NOTE]
> **Vyloučit glob** vždy vyloučí `./bin` a `./obj` složek, které jsou znázorněny `$(BaseOutputPath)` a `$(BaseIntermediateOutputPath)` vlastnosti nástroje MSBuild, v uvedeném pořadí. Jako celek, vyloučí všechny jsou reprezentovány `$(DefaultItemExcludes)`.

Pokud máte globy ve vašem projektu a zkusíte sestavit pomocí nejnovější SDK, zobrazí se vám chybová zpráva:

> Duplicitní položky kompilace byly zahrnuty. Sady .NET SDK obsahuje ve výchozím nastavení kompilace položky z adresáře projektu. Můžete tyto položky odebrat ze svého souboru projektu, nebo nastavte vlastnost 'EnableDefaultCompileItems' na hodnotu false' Pokud chcete explicitně zahrnout je do souboru projektu.

Aby bylo možné tuto chybu vyřešit, buď odstraněním explicitní `Compile` položky, které odpovídají těm, které jsou uvedené v předchozí tabulce, nebo můžete nastavit `<EnableDefaultCompileItems>` vlastnost `false`, tímto způsobem:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Nastavení této vlastnosti na `false` dojde k zakázání implicitního zahrnutí návrat k chování předchozí sady SDK, které jste museli zadat výchozí globy ve vašem projektu.

Tato změna neprovede žádné změny v hlavním obsahuje jiné mechanismy. Ale pokud chcete zadat, například některé soubory se publikovat s vaší aplikací, můžete stále použít známé mechanismy ve *csproj* pro daný (například `<Content>` element).

`<EnableDefaultCompileItems>` pouze zakáže `Compile` globy, ale nemá vliv na ostatní globy, jako jsou implicitní `None` glob, která se také vztahuje na \*.cs položky. Proto **Průzkumníka řešení** bude dál zobrazovat \*.cs položky jako součást projektu, jako `None` položky. Podobným způsobem můžete nastavit `<EnableDefaultNoneItems>` na hodnotu false, chcete-li zakázat implicitní `None` glob takto:

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Chcete-li zakázat **všechny implicitní globy**, můžete nastavit `<EnableDefaultItems>` vlastnost `false` jako v následujícím příkladu:

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Zobrazení celého projektu, jak ho uvidí MSBuild

Zatímco tyto změny csproj výrazně zjednodušit soubory projektu, můžete chtít zobrazit plně rozšířené projektu jako MSBuild ji vidí, jakmile jsou zahrnuty v sadě SDK a cíle. Předběžné zpracování projektu s [ `/pp` přepnout](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) příkaz, který ukazuje, které soubory se importují, jejich zdroje a svoje příspěvky k sestavení bez ve skutečnosti sestavení projektu:

`dotnet msbuild -pp:fullproject.xml`

Pokud projekt obsahuje více cílových platforem, by měl výsledky příkazu, zaměřuje na pouze jeden z nich tak, že zadáte jako vlastnost MSBuild:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Přidání

### <a name="sdk-attribute"></a>Atribut SDK

Kořen `<Project>` elementu *.csproj* soubor obsahuje nový atribut volá `Sdk`. `Sdk` Určuje, které sada SDK se používá v projektu. Sady SDK, jako [rozvržení dokumentu](cli-msbuild-architecture.md) popisuje, je sada MSBuild [úlohy](/visualstudio/msbuild/msbuild-tasks) a [cíle](/visualstudio/msbuild/msbuild-targets) , které můžete vytvářet kód .NET Core. Při použití .NET Core 3.0 Preview dodáváme tři hlavní sady SDK s nástroji .NET Core a další dvě sady SDK:

1. .NET Core SDK s ID `Microsoft.NET.Sdk`
2. .NET Core web SDK s ID `Microsoft.NET.Sdk.Web`
3. Knihovny tříd Razor .NET Core SDK s ID nástroje `Microsoft.NET.Sdk.Razor`
4. Službu v .NET Core pracovního procesu s ID `Microsoft.NET.Sdk.Worker` (.NET Core 3.0 Preview)
5. .NET Core WinForms a WPF s ID `Microsoft.NET.Sdk.WindowsDesktop` (.NET Core 3.0 Preview)

Je potřeba mít `Sdk` nastavený atribut na jednu z těchto ID na `<Project>` prvku abyste mohli použít nástroje pro .NET Core a vytváření kódu.

### <a name="packagereference"></a>PackageReference

A `<PackageReference>` určuje prvek položky [závislostí NuGet v projektu](/nuget/consume-packages/package-references-in-project-files). `Include` Atribut určuje ID balíčku.

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Version

Požadované `Version` atribut určuje verzi balíčku k obnovení. Atribut respektuje pravidla [správy verzí NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards) schéma. Výchozí chování je shoda přesnou verzi. Například zadání `Version="1.2.3"` je ekvivalentní zápisu NuGet `[1.2.3]` pro přesné 1.2.3 verzi balíčku.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets a PrivateAssets

`IncludeAssets` atribut určuje, jaké prostředky, které patří do určeného balíčku `<PackageReference>` by měl používat. Ve výchozím nastavení jsou zahrnuty všechny prostředky balíčku.

`ExcludeAssets` atribut určuje, jaké prostředky, které patří do určeného balíčku `<PackageReference>` by neměla využívat.

`PrivateAssets` atribut určuje, jaké prostředky, které patří do určeného balíčku `<PackageReference>` by měl používat, ale ne směrovat do příští projekt. `Analyzers`, `Build` a `ContentFiles` prostředky jsou ve výchozím nastavení privátní, když tento atribut není k dispozici.

> [!NOTE]
> `PrivateAssets` je ekvivalentní *project.json*/*xproj* `SuppressParent` elementu.

Tyto atributy mohou obsahovat jednu nebo více následující položky oddělené středníkem `;` znaku, pokud je uveden více než jeden:

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
A `<DotNetCliToolReference>` prvek položky určuje nástroj rozhraní příkazového řádku, který uživatel chce obnovit v kontextu projektu. Je náhradou za `tools` uzel v *project.json*.

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a>Version

`Version` Určuje verzi balíčku, který se obnovit. Atribut respektuje pravidla [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) schéma. Výchozí chování je shoda přesnou verzi. Například zadání `Version="1.2.3"` je ekvivalentní zápisu NuGet `[1.2.3]` pro přesné 1.2.3 verzi balíčku.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

`<RuntimeIdentifiers>` Property – element umožňuje určit seznam oddělený středníkem [Runtime identifikátorů (RID)](../rid-catalog.md) pro projekt.
Identifikátory RID povolit publikování samostatná nasazení.

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier

`<RuntimeIdentifier>` Property – element umožňuje určit pouze jeden [identifikátor modulu Runtime (RID)](../rid-catalog.md) pro projekt. Identifikátor RID umožňuje publikování samostatná nasazení.

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

Použití `<RuntimeIdentifiers>` (množném čísle) místo toho pokud je potřeba publikovat pro více modulů – runtime. `<RuntimeIdentifier>` rychlejší sestavování a můžete zadat, pokud je nutné použít pouze jeden modul runtime.

### <a name="packagetargetfallback"></a>PackageTargetFallback

`<PackageTargetFallback>` Property – element umožňuje určit sadu kompatibilní cíle se použije při obnovování balíčků. Je navržen tak, aby balíčky, které používají dotnet [TxM (Moniker cílového x)](/nuget/schema/target-frameworks) pracovat s balíčky, které není deklarovat dotnet TxM. Pokud váš projekt používá dotnet TxM, pak všechny balíčky, které závisí na musí také mít dotnet TxM, pokud přidáte `<PackageTargetFallback>` do vašeho projektu, aby bylo možné povolit bez dotnet platformy se kvůli kompatibilitě s dotnet.

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

S přechodem na MSBuild, přesunuli jsme vstupní metadata, která se používá při balení balíček NuGet *project.json* k *.csproj* soubory. Vstupy jsou vlastnosti nástroje MSBuild, takže budou muset přejít v rámci `<PropertyGroup>` skupiny. Tady je seznam vlastností, které se používají jako vstupy do procesu zabalení, při použití `dotnet pack` příkazu nebo `Pack` MSBuild cíl, který je součástí sady SDK.

### <a name="ispackable"></a>IsPackable

Logická hodnota určující, zda lze zabalit projekt. Výchozí hodnota je `true`.

### <a name="packageversion"></a>PackageVersion

Určuje verzi, bude výsledný balíček. Přijímá všechny formy řetězec verze NuGet. Výchozí hodnota je hodnota `$(Version)`, to znamená, vlastnosti `Version` v projektu.

### <a name="packageid"></a>PackageId

Určuje název pro výsledný balíček. Pokud není zadán, `pack` operace budou ve výchozím nastavení použití `AssemblyName` nebo název adresáře jako název balíčku.

### <a name="title"></a>Název

Lidské popisný název balíčku, obvykle používaných v uživatelském rozhraní na webech nuget.org a Správce balíčků v sadě Visual Studio. Pokud se nezadá, ID balíčku, který se používá místo toho.

### <a name="authors"></a>Autoři

Středníkem oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org. Tyto jsou zobrazeny v galerii NuGet na nuget.org a slouží k křížový odkaz balíčky stejné autory.

### <a name="packagedescription"></a>PackageDescription

Dlouhý popis balíčku zobrazí v uživatelském rozhraní.

### <a name="description"></a>Popis

Dlouhý popis pro sestavení. Pokud `PackageDescription` není zadán, pak tato vlastnost slouží také jako popis balíčku.

### <a name="copyright"></a>Copyright

Podrobnosti o autorských právech pro balíček.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance

Logická hodnota určující, zda klient musí požádat spotřebitele o přijetí licence balíčku před instalací balíčku. Výchozí hodnota je `false`.

### <a name="packagelicenseexpression"></a>PackageLicenseExpression

[SPDX licence identifikátor](https://spdx.org/licenses/) nebo výraz. Například, `Apache-2.0`.

Tady je úplný seznam [SPDX licence identifikátory](https://spdx.org/licenses/). NuGet.org přijímá pouze OSI nebo licenci FSF schválení licence při použití výrazu typu.

Syntaxe výrazů licence je popsaný dole v [ABNF](https://tools.ietf.org/html/rfc5234).

```cli
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> Pouze jeden z `PackageLicenseExpression`, `PackageLicenseFile` a `PackageLicenseUrl` lze zadat najednou.

### <a name="packagelicensefile"></a>PackageLicenseFile

Cesta k souboru licencí v rámci balíčku, pokud používáte licenci, která ještě není přiřazený identifikátor SPDX, nebo vlastní licenci (jinak `PackageLicenseExpression` je upřednostňované)

Nahradí `PackageLicenseUrl`, nelze kombinovat s `PackageLicenseExpression` a vyžaduje Visual Studio 15.9.4 2.1.502 nebo 2.2.101, sady .NET SDK nebo novější.

Budete muset zajistit, že soubor s licencí je zabalena tak, že explicitně přidáte k projektu, příklady použití:

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a>PackageLicenseUrl

Adresu URL licence, která se vztahuje na balíček. (_zastaralé od verze Visual Studio 15.9.4, sady .NET SDK 2.1.502 a 2.2.101_)

### <a name="packageiconurl"></a>PackageIconUrl

Adresa URL pro bitovou kopii 64 x 64 s průhledným pozadím použít jako ikona pro balíček zobrazená v uživatelském rozhraní.

### <a name="packagereleasenotes"></a>PackageReleaseNotes

Zpráva k vydání verze pro balíček.

### <a name="packagetags"></a>PackageTags

Středníkem oddělený seznam značek, který určuje balíček.

### <a name="packageoutputpath"></a>PackageOutputPath

Určuje výstupní cesta, ve kterém se zahodí komprimovaný balíček. Výchozí hodnota je `$(OutputPath)`.

### <a name="includesymbols"></a>IncludeSymbols
Tato logická hodnota označuje, zda by měl balíček tehdy, když je zabalit projekt vytvořit balíček dalších symbolů. Formát balíčku symbolů se řídí `SymbolPackageFormat` vlastnost.

### <a name="symbolpackageformat"></a>SymbolPackageFormat
Určuje formát balíček symbolů. Pokud "symbols.nupkg" symboly starší verze balíčku se vytvoří s *. symbols.nupkg* rozšíření, který obsahuje soubory PDB, knihovny DLL a ostatních výstupních souborů. Pokud "snupkg" balíček symbolů snupkg bude vytvořen obsahující souborům portable pdb. Výchozí hodnota je "symbols.nupkg".

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
