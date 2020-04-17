---
title: Dodatky k formátu csproj pro .NET Core
description: Informace o rozdílech mezi existujícími a .NET Core csproj soubory
ms.date: 04/08/2019
ms.openlocfilehash: fadc6de43f522129970e48bc72914cf187fe3f82
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607703"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Dodatky k formátu csproj pro .NET Core

Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přechodu z *project.json* na *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild). Další informace o obecné syntaxi souboru projektu a odkaz naleznete v dokumentaci [k souboru projektu MSBuild.](/visualstudio/msbuild/msbuild-project-file-schema-reference)

## <a name="implicit-package-references"></a>Implicitní odkazy na balíky

Metabalíčky jsou implicitně odkazovány na základě cílové `<TargetFramework>` architektury `<TargetFrameworks>` zadané v nebo vlastnost souboru projektu. `<TargetFrameworks>`je ignorována, pokud `<TargetFramework>` je zadána, nezávisle na pořadí. Další informace naleznete [v tématu Balíčky, metabalíčky a architektury](../packages.md).

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

Vzhledem k tomu, `Microsoft.NETCore.App` nebo `NETStandard.Library` metapackages jsou implicitně odkazuje, následující jsou naše doporučené doporučené postupy:

- Při cílení na rozhraní .NET Core nebo .NET `Microsoft.NETCore.App` `NETStandard.Library` Standard nikdy `<PackageReference>` nemají explicitní odkaz na nebo metapackages prostřednictvím položky v souboru projektu.
- Pokud potřebujete konkrétní verzi runtime při cílení .NET Core, `<RuntimeFrameworkVersion>` měli byste použít vlastnost `1.0.4`v projektu (například) namísto odkazování na metabalíček.
  - K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#publish-self-contained) a potřebujete například konkrétní verzi opravy runtime 1.0.0 LTS.
- Pokud potřebujete konkrétní verzi `NETStandard.Library` metabalíčku při cílení na standard .NET, můžete použít `<NetStandardImplicitPackageVersion>` vlastnost a nastavit verzi, kterou potřebujete.
- Nepřidávejte explicitně ani neaktualizujte `Microsoft.NETCore.App` `NETStandard.Library` odkazy na metabalíček nebo metabalíček v projektech rozhraní .NET Framework. Pokud je `NETStandard.Library` při použití balíčku NuGet založeného na standardu .NET standard potřeba libovolná verze programu NuGet, nuget tuto verzi automaticky nainstaluje.

## <a name="implicit-version-for-some-package-references"></a>Implicitní verze pro některé odkazy na balíčky

Většina použití [`<PackageReference>`](#packagereference) vyžadují `Version` nastavení atributu k určení verze balíčku NuGet, který má být použit. Při použití rozhraní .NET Core 2.1 nebo 2.2 a odkazování [na Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) nebo [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), ale atribut je zbytečné. Sada .NET Core SDK může automaticky vybrat verzi těchto balíčků, které by měly být použity.

### <a name="recommendation"></a>Doporučení

Při odkazování `Microsoft.AspNetCore.App` `Microsoft.AspNetCore.All` na nebo balíčky, nezadávejte jejich verzi. Pokud je zadána verze, sada SDK může způsobit upozornění NETSDK1071. Chcete-li toto upozornění opravit, odeberte verzi balíčku jako v následujícím příkladu:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> Známý problém: Sada .NET Core 2.1 SDK tuto syntaxi pouze podporovala, když projekt také používá microsoft.NET.Sdk.Web. To je vyřešen v .NET Core 2.2 SDK.

Tyto odkazy na ASP.NET Metapackages Core mají mírně odlišné chování od většiny běžných nuget ových balíčků. [Nasazení aplikací,](../deploying/index.md#publish-runtime-dependent) které používají tyto metabalíčky, jsou závislá na rámci sítě automaticky využívat ASP.NET sdíleného rozhraní Core. Při použití metapackages **žádné** prostředky z odkazované ASP.NET balíčky Core NuGet jsou nasazeny s aplikací – ASP.NET základní sdílené rozhraní obsahuje tyto prostředky. Prostředky ve sdíleném rámci jsou optimalizovány pro cílovou platformu pro zlepšení doby spuštění aplikace. Další informace o sdíleném rozhraní naleznete v [tématu .NET Core distribution packaging](../distribution-packaging.md).

Pokud *je* zadána verze, je považována za *minimální* verzi sdíleného rozhraní ASP.NET Core pro nasazení závislá na rámci a jako *přesná* verze pro samostatná nasazení. To může mít následující důsledky:

- Pokud je verze ASP.NET Core nainstalovaná na serveru menší než verze zadaná v packagereference, proces .NET Core se nespustí. Aktualizace metabalíčku jsou často k dispozici na NuGet.org před aktualizace byly zpřístupněny v hostitelských prostředích, jako je Azure. Aktualizace verze na PackageReference to ASP.NET Core může způsobit selhání nasazené aplikace.
- Pokud je aplikace nasazena jako [samostatné nasazení](../deploying/index.md#publish-self-contained), nemusí aplikace obsahovat nejnovější aktualizace zabezpečení pro .NET Core. Pokud není zadána verze, sada SDK může automaticky zahrnout nejnovější verzi ASP.NET jádra do samostatného nasazení.

## <a name="default-compilation-includes-in-net-core-projects"></a>Výchozí kompilace zahrnuje v projektech .NET Core

S přechodem do formátu *csproj* v nejnovějších verzích sady SDK jsme přesunuli výchozí zahrnutí a vyloučení pro kompilaci položek a vložených prostředků do souborů vlastností sady SDK. To znamená, že již není nutné zadávat tyto položky v souboru projektu.

Hlavním důvodem je snížení nepořádku v souboru projektu. Výchozí hodnoty, které jsou k dispozici v sadě SDK by měla zahrnovat většinu běžných případů použití, takže není nutné opakovat v každém projektu, který vytvoříte. To vede k menším souborům projektu, které jsou mnohem srozumitelnější a v případě potřeby ručně upravovány.

V následující tabulce je uvedeno, který prvek a které globs jsou [zahrnuty](https://en.wikipedia.org/wiki/Glob_(programming)) i vyloučeny do sady SDK:

| Prvek           | Zahrnout glob                              | Vyloučit glob                                                  | Odstranit glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Kompilaci           | \*\*/\*.cs (nebo jiná jazyková rozšíření) | \*\*/\*.user;  \*\*/\*. \*proj;  \* \* /.sln; \*  \* \* / \*.vssscc  | –                      |
| Vložený prostředek  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*. \*proj; \* \* /.sln; \* \* \* / \*.vssscc     | –                      |
| Žádná              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*. \*proj; \* \* /.sln; \* \* \* / \*.vssscc     | \*\*/\*.cs; \* \* /.resx \*   |

> [!NOTE]
> **Vyloučit glob** vždy `./bin` vylučuje `./obj` a složky, `$(BaseOutputPath)` které `$(BaseIntermediateOutputPath)` jsou reprezentovány vlastnostmi MSBuild. Jako celek jsou všechna vyloučení `$(DefaultItemExcludes)`reprezentována .

Pokud máte globs v projektu a pokusíte se jej vytvořit pomocí nejnovější sady SDK, zobrazí se následující chyba:

> Byly zahrnuty duplicitní položky kompilace. Sada .NET SDK ve výchozím nastavení obsahuje položky kompilace z adresáře projektu. Tyto položky můžete odebrat ze souboru projektu nebo nastavit vlastnost EnableDefaultCompileItems na hodnotu false, pokud je chcete explicitně zahrnout do souboru projektu.

Chcete-li tuto chybu obejít, můžete `Compile` buď odebrat explicitní položky, které odpovídají položkám uvedeným v předchozí tabulce, nebo můžete vlastnost nastavit `<EnableDefaultCompileItems>` na `false`, například takto:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Nastavení této `false` vlastnosti zakáže implicitní zahrnutí, návrat k chování předchozích sad SDK, kde jste museli zadat výchozí globs v projektu.

Tato změna nemění hlavní mechaniky jiných zahrnuje. Pokud však chcete například zadat některé soubory, které chcete publikovat s vaší aplikací, můžete pro to stále používat `<Content>` známé mechanismy v *csproj* (například prvek).

`<EnableDefaultCompileItems>`pouze zakáže `Compile` globs, ale nemá vliv na `None` jiné globs, \*jako je implicitní glob, který se vztahuje i na .cs položky. Z tohoto důvodu bude **Průzkumník řešení** pokračovat v zobrazení \*položek `None` .cs jako součást projektu, zahrnutých jako položky. Podobným způsobem můžete nastavit `<EnableDefaultNoneItems>` na hodnotu false, chcete-li zakázat implicitní `None` glob, takto:

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Chcete-li zakázat **všechny implicitní globs**, můžete nastavit `<EnableDefaultItems>` vlastnost jako `false` v následujícím příkladu:

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Jak zobrazit celý projekt tak, jak jej vidí MSBuild

Zatímco tyto změny csproj výrazně zjednodušit soubory projektu, můžete chtít vidět plně rozšířený projekt jako MSBuild vidí, jakmile SDK a jeho cíle jsou zahrnuty. Předběžně zpracujte projekt [`dotnet msbuild`](dotnet-msbuild.md) [ `/pp` pomocí přepínače](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) příkazu, který zobrazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky k sestavení, aniž by bylo skutečně budováno projektu:

`dotnet msbuild -pp:fullproject.xml`

Pokud projekt má více cílových architektur, výsledky příkazu by měly být zaměřeny pouze na jeden z nich zadáním jako msbuild vlastnost:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Dodatky

### <a name="sdk-attribute"></a>Atribut Sdk

Kořenový `<Project>` prvek souboru *.csproj* má `Sdk`nový atribut s názvem . `Sdk`určuje, která sada SDK bude projektem používán. Sada SDK, jak popisuje [dokument vrstvení,](cli-msbuild-architecture.md) je sada [úloh](/visualstudio/msbuild/msbuild-tasks) a [cílů](/visualstudio/msbuild/msbuild-targets) MSBuild, které mohou vytvářet základní kód .NET. Pro službu .NET Core jsou k dispozici následující sady SDK:

1. Sada .NET Core SDK s ID`Microsoft.NET.Sdk`
2. Sada .NET Core web SDK s ID`Microsoft.NET.Sdk.Web`
3. Knihovna třídy .NET Core Razor SDK s ID`Microsoft.NET.Sdk.Razor`
4. Služba .NET Core Worker Service `Microsoft.NET.Sdk.Worker` s ID (od .NET Core 3.0)
5. Rozhraní .NET Core WinForms a WPF `Microsoft.NET.Sdk.WindowsDesktop` s ID (od .NET Core 3.0)

Musíte mít `Sdk` atribut nastaven na jeden z těchto `<Project>` ID na prvek, aby bylo možné použít nástroje .NET Core a vytvořit kód.

### <a name="packagereference"></a>Odkaz na balíček

Prvek `<PackageReference>` položky určuje [závislost NuGet v projektu](/nuget/consume-packages/package-references-in-project-files). Atribut `Include` určuje ID balíčku.

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Version

Požadovaný `Version` atribut určuje verzi balíčku, který má být obnoven. Atribut respektuje pravidla [nuget verze rozsahu](/nuget/concepts/package-versioning#version-ranges) schématu. Výchozí chování je minimální verze, včetně shoda. Například zadání `Version="1.2.3"` je ekvivalentní NuGet `[1.2.3, )` zápisu a znamená, že vyřešený balíček bude mít verzi 1.2.3, pokud je k dispozici nebo větší jinak.

#### <a name="includeassets-excludeassets-and-privateassets"></a>Zahrnout majetek, vyloučit majetek a privateassets

`IncludeAssets`atribut určuje, které prostředky patřící `<PackageReference>` do balíčku určeného by měly být spotřebovány. Ve výchozím nastavení jsou zahrnuty všechny datové zdroje balíčku.

`ExcludeAssets`atribut určuje, které prostředky patřící `<PackageReference>` do balíčku určeného by neměly být spotřebovány.

`PrivateAssets`atribut určuje, které prostředky patřící `<PackageReference>` do balíčku určeného by měly být spotřebovány, ale ne tok do dalšího projektu. A `Analyzers` `Build` prostředky `ContentFiles` jsou ve výchozím nastavení soukromé, pokud tento atribut není k dispozici.

> [!NOTE]
> `PrivateAssets`je ekvivalentní prvku *project.json*/*xproj.* `SuppressParent`

Tyto atributy mohou obsahovat jednu nebo více následujících položek oddělených středníkem, `;` pokud je uvedeno více než jeden:

- `Compile`– obsah složky *lib* jsou k dispozici pro kompilaci.
- `Runtime`– obsah *složky runtime* jsou distribuovány.
- `ContentFiles`– obsah složky *contentfiles* se používá.
- `Build`– používají se rekvizity/cíle ve složce *sestavení.*
- `Native`– obsah z nativních datových zdrojů se zkopíruje do *výstupní* složky pro běh.
- `Analyzers`– analyzátory.

Alternativně atribut může obsahovat:

- `None`– žádný z aktiv není použit.
- `All`– používají se všechna aktiva.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference

Prvek `<DotNetCliToolReference>` položky určuje nástroj rozhraní se klis, který chce uživatel obnovit v kontextu projektu. Je to náhrada `tools` za uzel v *project.json*.

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

Všimněte `DotNetCliToolReference` si, že je [nyní zastaralé](https://github.com/dotnet/announcements/issues/107) ve prospěch [.NET Core místní nástroje](https://aka.ms/local-tools).

#### <a name="version"></a>Version

`Version`určuje verzi balíčku, který chcete obnovit. Atribut respektuje pravidla [nuget verze schématu.](/nuget/create-packages/dependency-versions#version-ranges) Výchozí chování je minimální verze, včetně shoda. Například zadání `Version="1.2.3"` je ekvivalentní NuGet `[1.2.3, )` zápisu a znamená, že vyřešený balíček bude mít verzi 1.2.3, pokud je k dispozici nebo větší jinak.

### <a name="runtimeidentifiers"></a>Identifikátory runtime

Element `<RuntimeIdentifiers>` vlastnosti umožňuje zadat seznam [identifikátorů runtime (RID)](../rid-catalog.md) pro projekt oddělený středníkem.
Ridy umožňují publikování samostatných nasazení.

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>Identifikátor runtime

Element `<RuntimeIdentifier>` vlastnosti umožňuje zadat pouze jeden [identifikátor runtime (RID)](../rid-catalog.md) pro projekt. Rid umožňuje publikování samostatné nasazení.

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

Místo `<RuntimeIdentifiers>` toho použijte (množné číslo), pokud potřebujete publikovat pro více runtimes. `<RuntimeIdentifier>`může poskytovat rychlejší sestavení, pokud je vyžadován pouze jeden runtime.

### <a name="packagetargetfallback"></a>BalíčekTargetFallback

Element `<PackageTargetFallback>` vlastnosti umožňuje zadat sadu kompatibilních cílů, které mají být použity při obnovení balíčků. Je navržen tak, aby balíčky, které používají dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) pracovat s balíčky, které nedeklarují dotnet TxM. Pokud váš projekt používá dotnet TxM, pak všechny balíčky, na kterých závisí, musí `<PackageTargetFallback>` mít také dotnet TxM, pokud nepřidáte do projektu, aby byly platformy bez dotnetu kompatibilní s dotnet.

Následující příklad poskytuje záložní informace o všech cílech v projektu:

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

Následující příklad určuje záložní pouze pro `netcoreapp2.1` cíl:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a>Vytváření událostí

Způsob, jakým jsou v souboru projektu zadány události před sestavením a po sestavení, se změnil. Vlastnosti PreBuildEvent a PostBuildEvent se ve formátu projektu ve stylu sady SDK nedoporučují, protože makra jako $(ProjectDir) nejsou vyřešena. Například následující kód již není podporován:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

V projektech ve stylu sady SDK `PreBuild` použijte `PostBuild` cíl `BeforeTargets` MSBuild `AfterTargets` s `PostBuild`názvem nebo a nastavte vlastnost pro `PreBuild` nebo vlastnost pro . Pro předchozí příklad použijte následující kód:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>Pro cíle MSBuild můžete použít libovolný název, ale ide `PostBuild` sady Visual Studio rozpozná a cílí, `PreBuild` takže doporučujeme tyto názvy používat, abyste mohli upravovat příkazy v ide sady Visual Studio.

## <a name="nuget-metadata-properties"></a>Vlastnosti metadat NuGet

S přechodem na MSBuild jsme přesunuli vstupní metadata, která se používá při balení balíčku NuGet z *project.json* na *soubory .csproj.* Vstupy jsou MSBuild vlastnosti, takže `<PropertyGroup>` musí jít do skupiny. Následuje seznam vlastností, které se používají jako vstupy do `dotnet pack` procesu `Pack` balení při použití příkazu nebo cíle MSBuild, který je součástí sady SDK:

### <a name="ispackable"></a>Jestelná

Logická hodnota, která určuje, zda může být projekt zabalen. Výchozí hodnota je `true`.

### <a name="packageversion"></a>PackageVersion

Určuje verzi, kterou bude mít výsledný balíček. Přijímá všechny formy řetězce verze NuGet. Výchozí hodnota je `$(Version)`hodnota , to `Version` znamená vlastnost v projektu.

### <a name="packageid"></a>Id balení

Určuje název výsledného balíčku. Pokud není zadán, `pack` bude operace `AssemblyName` ve výchozím nastavení používat název nebo jako název balíčku.

### <a name="title"></a>Nadpis

Lidský název balíčku, obvykle používaný v ui se zobrazí jako na nuget.org a Správce balíčků v sadě Visual Studio. Pokud není zadán, použije se místo toho ID balíčku.

### <a name="authors"></a>Autoři

Středník-oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org. Ty jsou zobrazeny v Galerii NuGet na nuget.org a slouží ke křížovým odkazům balíčky stejnými autory.

### <a name="packagedescription"></a>Popis balíčku

Dlouhý popis balíčku pro zobrazení ui.

### <a name="description"></a>Popis

Dlouhý popis sestavení. Pokud `PackageDescription` není zadán, pak tato vlastnost se také používá jako popis balíčku.

### <a name="copyright"></a>Copyright

Podrobnosti o autorských právech k balíčku.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance

Logická hodnota, která určuje, zda musí klient vyzvat spotřebitele k přijetí licence balíčku před instalací balíčku. Výchozí formát je `false`.

### <a name="developmentdependency"></a>DevelopmentDependency

Logická hodnota, která určuje, zda je balíček označen jako závislost pouze pro vývoj, což zabraňuje zahrnutí balíčku jako závislosti do jiných balíčků. S PackageReference (NuGet 4.8+) tento příznak také znamená, že prostředky v době kompilace jsou vyloučeny z kompilace. Další informace naleznete v [tématu DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).

### <a name="packagelicenseexpression"></a>PackageLicenseExpression

Identifikátor nebo výraz [licence SPDX.](https://spdx.org/licenses/) Například, `Apache-2.0`.

Zde je úplný seznam [identifikátorů licencí SPDX](https://spdx.org/licenses/). NuGet.org přijímá pouze licence schválené OSI nebo FSF při použití výrazu typu licence.

Přesná syntaxe licenčních výrazů je popsána níže v [ABNF](https://tools.ietf.org/html/rfc5234).

```abnf
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
> Pouze jeden `PackageLicenseExpression` `PackageLicenseFile` z `PackageLicenseUrl` , a lze zadat současně.

### <a name="packagelicensefile"></a>Soubor PackageLicenseFile

Cesta k licenčnímu souboru v rámci balíčku, pokud používáte licenci, které nebyl přiřazen identifikátor `PackageLicenseExpression` SPDX, nebo se jedná o vlastní licenci (v opačném případě je upřednostňována)

Nahrazuje `PackageLicenseUrl`, nelze kombinovat s `PackageLicenseExpression`aplikacemi a vyžaduje sady Visual Studio verze 15.9.4 a .NET SDK 2.1.502 nebo 2.2.101 nebo novější.

Budete muset zajistit, že licenční soubor je zabalen přidáním explicitně do projektu, například použití:

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a>Adresa PackageLicenseUrl

Adresa URL licence, která se vztahuje na balíček. (_zastaralé od Visual Studio 15.9.4, .NET SDK 2.1.502 a 2.2.101_)

### <a name="packageiconurl"></a>Adresa PackageIconUrl

Adresa URL obrázku 64 x 64 s průhledným pozadím, která se má použít jako ikona balíčku v zobrazení uživatelského prostředí.

### <a name="packagereleasenotes"></a>Poznámky k vydání balíčku

Poznámky k uvolnění balíčku.

### <a name="packagetags"></a>Tagy balíčků

Středník-oddělený seznam značek, který označuje balíček.

### <a name="packageoutputpath"></a>PackageOutputPath

Určuje výstupní cestu, ve které bude vynechán balíček. Výchozí je `$(OutputPath)`.

### <a name="includesymbols"></a>Zahrnout symboly
Tato logická hodnota označuje, zda balíček by měl vytvořit další symboly balíček při projektu je zabalen. Formát balíčku symbolů je řízen `SymbolPackageFormat` vlastností.

### <a name="symbolpackageformat"></a>SymbolPackageFormat
Určuje formát balíčku symbolů. Pokud "symbols.nupkg", balíček starších symbolů bude vytvořen s příponou *.symbols.nupkg* obsahující pdbs, dll a další výstupní soubory. Pokud "snupkg", bude vytvořen balíček symbolů snupkg obsahující přenosné PD. Výchozí hodnota je "symbols.nupkg".

### <a name="includesource"></a>IncludeSource

Tato logická hodnota označuje, zda by měl proces balení vytvořit zdrojový balíček. Zdrojový balíček obsahuje zdrojový kód knihovny, stejně jako soubory PDB. Zdrojové soubory jsou `src/ProjectName` umístěny pod adresářem ve výsledném souboru balíčku.

### <a name="istool"></a>Istool

Určuje, zda budou všechny výstupní soubory zkopírovány do složky *nástrojů* namísto složky *lib.* To se liší `DotNetCliTool`od , který `PackageType` je určen nastavením v souboru *.csproj.*

### <a name="repositoryurl"></a>Adresa úložiště

Určuje adresu URL úložiště, kde se nachází zdrojový kód pro balíček nebo ze kterého je právě setožován.

### <a name="repositorytype"></a>Typ úložiště

Určuje typ úložiště. Výchozí hodnota je "git".

### <a name="repositorybranch"></a>Pobočka úložiště
Určuje název zdrojové větve v úložišti. Když je projekt zabalen v balíčku NuGet, je přidán do metadat balíčku.

### <a name="repositorycommit"></a>Potvrzení úložiště
Volitelné potvrzení úložiště nebo sada změn k označení zdroje, proti kterému byl balíček vytvořen. `RepositoryUrl`musí být také určeny pro tuto vlastnost, které mají být zahrnuty. Když je projekt zabalen v balíčku NuGet, toto potvrzení nebo sada změn je přidán do metadat balíčku.

### <a name="nopackageanalysis"></a>NoPackageAnalysis

Určuje, že balíček by neměl spustit analýzu balíčku po sestavení balíčku.

### <a name="minclientversion"></a>MinClientVersion

Určuje minimální verzi klienta NuGet, který může nainstalovat tento balíček vynucený nuget.exe a Správce balíčků sady Visual Studio.

### <a name="includebuildoutput"></a>IncludeBuildOutput

Tato logická hodnota určuje, zda mají být výstupní sestavení zabalena do souboru *.nupkg* nebo ne.

### <a name="includecontentinpack"></a>IncludeContentInPack

Tato logická hodnota určuje, zda budou `Content` všechny položky, které mají typ, automaticky zahrnuty do výsledného balíčku. Výchozí formát je `true`.

### <a name="buildoutputtargetfolder"></a>Složka BuildOutputTargetFolder

Určuje složku, kam mají být umístěna výstupní sestavení. Výstupní sestavení (a další výstupní soubory) jsou zkopírovány do příslušných složek architektury.

### <a name="contenttargetfolders"></a>ContentTargetFolders

Tato vlastnost určuje výchozí umístění, kam by měly být všechny soubory obsahu zadány, pokud `PackagePath` pro ně nejsou zadány. Výchozí hodnota je "content;contentFiles".

### <a name="nuspecfile"></a>Soubor NuspecFile

Relativní nebo absolutní cesta k souboru *.nuspec,* který se používá pro balení.

> [!NOTE]
> Pokud je zadán soubor *.nuspec,* používá se **výhradně** pro informace o balení a žádné informace v projektech se nepoužívá.

### <a name="nuspecbasepath"></a>Aplikace NuspecBasePath

Základní cesta pro soubor *Nuspec.*

### <a name="nuspecproperties"></a>NuspecProperties

Středník oddělený seznam key=value pairs.

## <a name="assemblyinfo-properties"></a>AssemblyInfo, vlastnosti

[Atributy sestavení,](../../standard/assembly/set-attributes.md) které byly obvykle přítomny v souboru *AssemblyInfo,* jsou nyní automaticky generovány z vlastností.

### <a name="properties-per-attribute"></a>Vlastnosti podle atributu

Jak je znázorněno v následující tabulce, každý atribut má vlastnost, která řídí jeho obsah a jiný, který zakáže jeho generování:

| Atribut                                                      | Vlastnost               | Vlastnost zakázat                             |
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

- `AssemblyVersion`a `FileVersion` výchozí je vzít `$(Version)` hodnotu bez přípony. Například pokud `$(Version)` `1.2.3-beta.4`je , pak `1.2.3`hodnota bude .
- `InformationalVersion`výchozí hodnota aplikace `$(Version)`.
- `InformationalVersion``$(SourceRevisionId)` pokud je vlastnost přítomna. To může být `IncludeSourceRevisionInInformationalVersion`zakázáno pomocí .
- `Copyright`a `Description` vlastnosti se také používají pro metadata NuGet.
- `Configuration`je sdílena se všemi procesy sestavení a nastavena `--configuration` pomocí parametru `dotnet` příkazů.

### <a name="generateassemblyinfo"></a>Generovat informace o sestavení

Logická hodnota, která povoluje nebo zakazuje všechny generování AssemblyInfo. Výchozí hodnota je `true`.

### <a name="generatedassemblyinfofile"></a>Generovanou žádost ParlamentníHo Hromada

Cesta generovaného souboru informací o sestavení. Výchozí soubor v `$(IntermediateOutputPath)` adresáři (obj).
