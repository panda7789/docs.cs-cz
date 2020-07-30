---
title: Přidání do formátu csproj pro .NET Core
description: Přečtěte si o rozdílech mezi existujícími a soubory .NET Core csproj.
ms.date: 04/08/2019
ms.openlocfilehash: a0cbead27e52af3114d9c44fd19c966e665a2850
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2020
ms.locfileid: "87427005"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Přidání do formátu csproj pro .NET Core

Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunutí z *project.jsna* do *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild). Další informace o obecných syntaxech souborů projektu a referenčních informacích naleznete v dokumentaci k [souboru projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .

## <a name="implicit-package-references"></a>Odkazy na implicitní balíčky

Na metabalíčky se implicitně odkazuje na základě cílových rozhraní, která jsou určená v `<TargetFramework>` vlastnosti nebo `<TargetFrameworks>` souboru projektu. `<TargetFrameworks>`se ignoruje `<TargetFramework>` , pokud je zadaný, nezávisle na pořadí.

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

Vzhledem `Microsoft.NETCore.App` `NETStandard.Library` k tomu, že jsou implicitně odkazovány na nebo metabalíčky, následující doporučené osvědčené postupy:

- Pokud cílíte na rozhraní .NET Core nebo .NET Standard, nikdy nepoužívejte explicitní odkaz na `Microsoft.NETCore.App` nebo `NETStandard.Library` metabalíčky prostřednictvím `<PackageReference>` položky v souboru projektu.
- Pokud potřebujete specifickou verzi modulu runtime při cílení na .NET Core, měli byste použít `<RuntimeFrameworkVersion>` vlastnost v projektu (například `1.0.4` ) namísto odkazování na Metapackage.
  - K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#publish-self-contained) a potřebujete konkrétní opravu verze 1.0.0 LTS runtime, například.
- Pokud potřebujete specifickou verzi `NETStandard.Library` Metapackage při cílení na .NET Standard, můžete použít `<NetStandardImplicitPackageVersion>` vlastnost a nastavit verzi, kterou potřebujete.
- Neprovádějte explicitní přidávání nebo aktualizaci odkazů na `Microsoft.NETCore.App` Metapackage nebo `NETStandard.Library` v projektech .NET Framework. Pokud `NETStandard.Library` je při použití balíčku NuGet založeného na .NET Standard potřebná nějaká verze, NuGet tuto verzi nainstaluje automaticky.

## <a name="implicit-version-for-some-package-references"></a>Implicitní verze pro některé odkazy na balíčky

Většina použití [`<PackageReference>`](#packagereference) parametru vyžaduje nastavení `Version` atributu k určení verze balíčku NuGet, která se má použít. Při použití .NET Core 2,1 nebo 2,2 a odkazování na [Microsoft. AspNetCore. app](/aspnet/core/fundamentals/metapackage-app) nebo [Microsoft. AspNetCore. All](/aspnet/core/fundamentals/metapackage)ale atribut není zbytečný. .NET Core SDK může automaticky vybrat verzi těchto balíčků, které by se měly použít.

### <a name="recommendation"></a>Doporučení

Při odkazování na `Microsoft.AspNetCore.App` balíčky nebo nezadávejte `Microsoft.AspNetCore.All` jejich verzi. Pokud je zadána verze, sada SDK může vytvořit upozornění NETSDK1071. Chcete-li toto upozornění vyřešit, odeberte verzi balíčku, jako v následujícím příkladu:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> Známý problém: sada .NET Core 2,1 SDK podporuje pouze tuto syntaxi pouze v případě, že projekt používá také Microsoft. NET. SDK. Web. To je vyřešeno v sadě .NET Core 2,2 SDK.

Tyto odkazy na ASP.NET Core metabalíčky mají mírně odlišné chování z většiny běžných balíčků NuGet. [Nasazení aplikací závislých na rozhraních](../deploying/index.md#publish-runtime-dependent) , která používají tyto metabalíčky, automaticky využívají ASP.NET Core sdílené rozhraní. Při použití metabalíčky se s aplikací nasadí **žádné** prostředky z odkazovaného ASP.NET Core balíčků NuGet – ASP.NET Core sdílené rozhraní obsahuje tyto prostředky. Prostředky ve sdíleném rozhraní jsou optimalizované pro cílovou platformu pro zlepšení času spuštění aplikace. Další informace o sdílených rozhraních naleznete v tématu [distribuční balíček .NET Core](../distribution-packaging.md).

*Je* -li zadána verze, je zpracována jako *minimální* verze ASP.NET Core sdílené architektury pro nasazení závislá na rozhraních a jako *Přesná* verze pro samostatně nasazená nasazení. To může mít následující důsledky:

- Pokud je verze ASP.NET Core nainstalovaná na serveru menší než verze zadaná na PackageReference, proces .NET Core se nepovede spustit. Aktualizace Metapackage jsou často k dispozici v NuGet.org před zpřístupněním aktualizací v hostitelských prostředích, jako je Azure. Aktualizace verze PackageReference na ASP.NET Core by mohla způsobit selhání nasazené aplikace.
- Pokud je aplikace nasazena jako [samostatné nasazení](../deploying/index.md#publish-self-contained), aplikace nemusí obsahovat nejnovější aktualizace zabezpečení .NET Core. Pokud není určena verze, může sada SDK automaticky zahrnovat nejnovější verzi ASP.NET Core v samostatném nasazení.

## <a name="default-compilation-includes-in-net-core-projects"></a>Výchozí kompilace zahrnuje v projektech .NET Core

S přesunem do formátu *csproj* v nejnovějších verzích sady SDK jsme přesunuli výchozí zahrnutí a vyloučení položek kompilace a integrovaných prostředků do souborů vlastností sady SDK. To znamená, že už nemusíte tyto položky v souboru projektu zadávat.

Hlavním důvodem pro to, aby to bylo, je omezit zbytečné soubory projektu. Výchozí hodnoty, které jsou obsaženy v sadě SDK, by měly pokrývat většinu běžných případů použití, takže je nemusíte opakovat v každém vytvořeném projektu. To vede k menšímu množství souborů projektu, které jsou v případě potřeby mnohem snazší a v případě potřeby upravitelné.

Následující tabulka ukazuje, který prvek a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuty a vyloučeny v sadě SDK:

| Prvek           | Zahrnout glob                              | Vyloučit glob                                                  | Odebrat glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Sestavení           | \*\*/\*cs (nebo jiné jazykové rozšíření) | \*\*/\*uživatelský  \*\*/\*.\* Souhrn  \*\*/\*. SLN  \*\*/\*. vssscc  | –                      |
| EmbeddedResource  | \*\*/\*. resx                              | \*\*/\*uživatelský \*\*/\*.\* Souhrn \*\*/\*. SLN \*\*/\*. vssscc     | –                      |
| Žádné              | \*\*/\*                                   | \*\*/\*uživatelský \*\*/\*.\* Souhrn \*\*/\*. SLN \*\*/\*. vssscc     | \*\*/\*cs \*\*/\*. RESX   |

> [!NOTE]
> **Exclude glob** vždy vyloučí `./bin` složky a `./obj` , které jsou reprezentovány `$(BaseOutputPath)` vlastnostmi a `$(BaseIntermediateOutputPath)` , v uvedeném pořadí. Všechna vyloučení jsou představována jako celek `$(DefaultItemExcludes)` .

Pokud jste v projektu globy a pokusíte se ho sestavit pomocí nejnovější sady SDK, zobrazí se následující chyba:

> Byly zahrnuty duplicitní položky kompilace. Sada .NET SDK obsahuje ve výchozím nastavení položky kompilace z adresáře projektu. Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultCompileItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.

Chcete-li se této chybě vyhnout, můžete buď odebrat explicitní `Compile` položky, které odpovídají těm, které jsou uvedeny v předchozí tabulce, nebo můžete nastavit `<EnableDefaultCompileItems>` vlastnost na následujícím `false` způsobem:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Nastavením této vlastnosti na `false` zakážete implicitní zahrnutí a vrátíte se do chování předchozích sad SDK, kde jste museli v projektu zadat výchozí globy.

Tato změna neupravuje hlavní mechanismy ostatních zahrnutí. Nicméně pokud chcete určit, například některé soubory, které mají být publikovány s vaší aplikací, můžete stále používat známé mechanismy v souboru *csproj* pro tento prvek (například `<Content>` element).

`<EnableDefaultCompileItems>`zakáže jenom `Compile` globy, ale neovlivní jiné globy, jako je implicitní `None` glob, které platí i pro \* položky. cs. Z tohoto důvodu **Průzkumník řešení** nadále zobrazovat \* položky cs jako součást projektu zahrnuté jako `None` položky. Podobným způsobem můžete nastavit `<EnableDefaultNoneItems>` na hodnotu false, chcete-li zakázat implicitní `None` glob, například:

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Chcete-li zakázat **všechny implicitní globy**, můžete nastavit `<EnableDefaultItems>` vlastnost na `false` jako v následujícím příkladu:

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Jak zobrazit celý projekt, když ho MSBuild uvidí

I když tyto změny csproj značně zjednodušují soubory projektu, je možné, že budete chtít zobrazit plně rozbalený projekt jako nástroj MSBuild, jakmile bude sada SDK a její cíle zahrnuté. Projekt předzpracování pomocí [ `/pp` přepínače](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](dotnet-msbuild.md) příkazu, který ukazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky na sestavení bez skutečného sestavení projektu:

`dotnet msbuild -pp:fullproject.xml`

Pokud má projekt více cílových rozhraní, výsledky příkazu by měly být zaměřené jenom na jeden z nich zadáním jako vlastnost MSBuild:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Rozšíření

### <a name="sdk-attribute"></a>Atribut sady SDK

Kořenový `<Project>` element souboru *. csproj* má nový atribut s názvem `Sdk` . `Sdk`Určuje sadu SDK, kterou bude projekt používat. Sada SDK, jak popisuje [dokument vrstvení](cli-msbuild-architecture.md) , je sada [úloh](/visualstudio/msbuild/msbuild-tasks) a [cílů](/visualstudio/msbuild/msbuild-targets) nástroje MSBuild, které mohou sestavovat kód .NET Core. Pro .NET Core jsou k dispozici následující sady SDK:

1. .NET Core SDK s ID`Microsoft.NET.Sdk`
2. Sada Web SDK .NET Core s ID`Microsoft.NET.Sdk.Web`
3. Sada SDK knihovny tříd .NET Core Razor s ID`Microsoft.NET.Sdk.Razor`
4. Služba pracovních procesů .NET Core s ID `Microsoft.NET.Sdk.Worker` (od .NET core 3,0)
5. WinForms rozhraní .NET Core a WPF s ID `Microsoft.NET.Sdk.WindowsDesktop` (od .NET core 3,0)

Aby bylo možné `Sdk` `<Project>` používat nástroje .NET Core a sestavovat kód, je nutné mít atribut nastaven na jedno z těchto identifikátorů v elementu.

### <a name="packagereference"></a>PackageReference

`<PackageReference>`Element Item Určuje [závislost NuGet v projektu](/nuget/consume-packages/package-references-in-project-files). `Include`Atribut určuje ID balíčku.

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Verze

Požadovaný `Version` atribut určuje verzi balíčku, který má být obnoven. Atribut respektuje pravidla schématu [rozsahu verzí NuGet](/nuget/concepts/package-versioning#version-ranges) . Výchozí chování je minimální verze (včetně shody). Zadání `Version="1.2.3"` je například ekvivalentní zápisu NuGet `[1.2.3, )` a znamená, že vyřešený balíček bude mít verzi 1.2.3, je-li k dispozici nebo více než jinak.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets a PrivateAssets

`IncludeAssets`atribut určuje, které prostředky patřící k balíčku určenému parametr `<PackageReference>` by měly být spotřebovány. Ve výchozím nastavení jsou zahrnuty všechny prostředky balíčku.

`ExcludeAssets`atribut určuje, které prostředky patřící do balíčku určeného `<PackageReference>` by neměly být spotřebovány.

`PrivateAssets`atribut určuje, které prostředky patřící do balíčku určeného `<PackageReference>` by měly být spotřebovány, ale nikoli do dalšího projektu. V `Analyzers` případě, že `Build` `ContentFiles` Tento atribut není k dispozici, jsou prostředky a majetky soukromé ve výchozím nastavení.

> [!NOTE]
> `PrivateAssets`je ekvivalentní *project.js* / elementu*xproj* `SuppressParent` .

Tyto atributy mohou obsahovat jednu nebo více z následujících položek oddělených středníkem, `;` Pokud je uvedena více než jedna:

- `Compile`– obsah složky *lib* je k dispozici pro zkompilování.
- `Runtime`– obsah *běhové* složky se distribuuje.
- `ContentFiles`– používá se obsah složky *contentFiles* .
- `Build`– jsou použity props/targets ve složce *sestavení* .
- `Native`– obsah z nativních assetů se zkopíruje do *výstupní* složky pro modul runtime.
- `Analyzers`– Analyzátory se používají.

Atribut může případně obsahovat:

- `None`– žádný z prostředků se nepoužívá.
- `All`– používají se všechny prostředky.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference

`<DotNetCliToolReference>`Element Item Určuje nástroj CLI, který uživatel chce obnovit v kontextu projektu. Je náhradou za `tools` uzel v *project.js*.

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

Všimněte si, že `DotNetCliToolReference` se [teď zastaralá](https://github.com/dotnet/announcements/issues/107) s upřednostněním [místních nástrojů .NET Core](./global-tools.md#install-a-local-tool).

#### <a name="version"></a>Verze

`Version`Určuje verzi balíčku, který se má obnovit. Atribut respektuje pravidla schématu [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) . Výchozí chování je minimální verze (včetně shody). Zadání `Version="1.2.3"` je například ekvivalentní zápisu NuGet `[1.2.3, )` a znamená, že vyřešený balíček bude mít verzi 1.2.3, je-li k dispozici nebo více než jinak.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

`<RuntimeIdentifiers>`Element Property umožňuje určit seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) , které jsou v projektu odděleny středníkem.
Identifikátorů RID umožňuje publikování samostatně obsažených nasazení.

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier

`<RuntimeIdentifier>`Element Property umožňuje zadat pouze jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt. Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

Použijte `<RuntimeIdentifiers>` (plural) místo toho, pokud potřebujete publikovat pro více modulů runtime. `<RuntimeIdentifier>`může poskytovat rychlejší sestavení, je-li vyžadován pouze jeden modul runtime.

### <a name="packagetargetfallback"></a>PackageTargetFallback

`<PackageTargetFallback>`Element Property umožňuje zadat sadu kompatibilních cílů, které se mají použít při obnovování balíčků. Je navržena tak, aby povolovala balíčky, které používají dotnet [TxM (Target x moniker)](/nuget/schema/target-frameworks) pro práci s balíčky, které nedeklarují dotnet TxM. Pokud váš projekt používá TxM dotnet, pak všechny balíčky, na kterých závisí, musí mít také hodnotu dotnet TxM, pokud do projektu nepřidáte, aby bylo možné, aby platformy, které `<PackageTargetFallback>` nejsou dotnet, byly kompatibilní s dotnet.

Následující příklad poskytuje záložní hodnoty pro všechny cíle v projektu:

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

Následující příklad určuje pouze zálohy pro `netcoreapp2.1` cíl:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a>Události sestavení

Způsob, jakým se změnily události před sestavením a po sestavení, jsou uvedeny v souboru projektu. Vlastnosti PreBuildEvent a PostBuildEvent nejsou doporučovány ve formátu projektu ve stylu sady SDK, protože makra jako $ (ProjectDir) nejsou vyřešena. Například následující kód již není podporován:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

V projektech se stylem sady SDK použijte cíl MSBuild s názvem `PreBuild` nebo `PostBuild` a nastavte `BeforeTargets` vlastnost pro `PreBuild` nebo `AfterTargets` vlastnost pro `PostBuild` . Pro předchozí příklad použijte následující kód:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>Můžete použít libovolný název cílů MSBuild, ale rozhraní IDE sady Visual Studio rozpoznává `PreBuild` a `PostBuild` cílí, takže doporučujeme použít tyto názvy, abyste mohli upravovat příkazy v integrovaném vývojovém prostředí sady Visual Studio.

## <a name="nuget-metadata-properties"></a>Vlastnosti metadat NuGet

Při přechodu na MSBuild jsme přesunuli vstupní metadata, která se používají při balení balíčku NuGet z *project.js* do souborů *. csproj* . Vstupy jsou vlastnosti nástroje MSBuild, takže musí jít v rámci `<PropertyGroup>` skupiny. Následuje seznam vlastností, které se používají jako vstupy do procesu balení při použití `dotnet pack` příkazu nebo `Pack` cíle MSBuild, který je součástí sady SDK:

### <a name="ispackable"></a>Ispackable nastavenou

Logická hodnota, která určuje, zda lze projekt zabalit. Výchozí hodnota je `true`.

### <a name="packageversion"></a>PackageVersion

Určuje verzi, kterou výsledný balíček bude mít. Akceptuje všechny formy řetězce verze NuGet. Výchozí hodnota je hodnota `$(Version)` , to znamená vlastnost `Version` v projektu.

### <a name="packageid"></a>PackageId

Určuje název výsledného balíčku. Pokud tento parametr nezadáte, použije se ve `pack` výchozím nastavení `AssemblyName` jako název balíčku název adresáře nebo.

### <a name="title"></a>Nadpis

Popisný název balíčku, který se obvykle používá v uživatelském rozhraní, se zobrazuje jako v nuget.org a správce balíčků v aplikaci Visual Studio. Pokud není zadaný, použije se místo toho ID balíčku.

### <a name="authors"></a>Autoři

Středníkem oddělený seznam autorů balíčků, které odpovídají názvům profilů v nuget.org. Ty se zobrazí v galerii NuGet na nuget.org a používají se pro balíčky křížového odkazu stejnými autory.

### <a name="packagedescription"></a>PackageDescription

Dlouhý popis balíčku pro zobrazení uživatelského rozhraní.

### <a name="description"></a>Popis

Dlouhý popis pro sestavení. Pokud `PackageDescription` parametr není zadán, tato vlastnost se používá také jako Popis balíčku.

### <a name="copyright"></a>Copyright

Podrobnosti o autorských právech pro balíček.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance

Logická hodnota, která určuje, zda klient musí požádat spotřebitele o přijetí licence k balíčku před instalací balíčku. Výchozí formát je `false`.

### <a name="developmentdependency"></a>DevelopmentDependency

Logická hodnota, která určuje, zda je balíček označen jako jen pro vývoj, což zabrání zahrnutí balíčku jako závislosti v jiných balíčcích. Pomocí PackageReference (NuGet 4,8 +) Tento příznak také znamená, že prostředky při kompilaci jsou vyloučeny z kompilace. Další informace najdete v tématu [Podpora DevelopmentDependency pro PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).

### <a name="packagelicenseexpression"></a>PackageLicenseExpression

Identifikátor nebo výraz [licence SPDX](https://spdx.org/licenses/) Například, `Apache-2.0`.

Tady je úplný seznam [identifikátorů licencí SPDX](https://spdx.org/licenses/). NuGet.org přijímá při použití výrazu typu licence pouze licence OSI nebo FSF schválené.

Přesná Syntaxe výrazů s licencí je popsána níže v tématu [ABNF](https://tools.ietf.org/html/rfc5234).

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
> `PackageLicenseExpression` `PackageLicenseFile` `PackageLicenseUrl` V jednom okamžiku může být určena pouze jedna z a.

### <a name="packagelicensefile"></a>PackageLicenseFile

Cesta k souboru s licencí v rámci balíčku Pokud používáte licenci, ke které se nepřiřadil identifikátor SPDX, nebo se jedná o vlastní licenci (jinak `PackageLicenseExpression` se upřednostňuje)

Nahrazuje `PackageLicenseUrl` , nejde kombinovat s a `PackageLicenseExpression` vyžaduje Visual Studio verze 15.9.4 a .NET SDK 2.1.502 nebo 2.2.101 nebo novější.

Je potřeba zajistit, aby byl soubor s licencí zabalený tak, že ho do projektu přidáte explicitně, jako příklad použití:

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a>PackageLicenseUrl

Adresa URL licence, která se vztahuje na balíček. (_nepoužívá se od verze Visual Studio 15.9.4, .NET SDK 2.1.502 a 2.2.101_)

### <a name="packageicon"></a>PackageIcon

Cesta k obrázku v balíčku, který se má použít jako ikona balíčku Přečtěte si další informace o [ `icon` metadatech](/nuget/reference/nuspec#icon). [PackageIconUrl je zastaralé](/nuget/reference/msbuild-targets#packageiconurl) namísto PackageIcon.

### <a name="packagereleasenotes"></a>PackageReleaseNotes

Poznámky k verzi balíčku

### <a name="packagetags"></a>PackageTags

Seznam značek oddělených středníkem, který určuje balíček.

### <a name="packageoutputpath"></a>PackageOutputPath

Určuje výstupní cestu, do které bude zahozen zabalený balíček. Výchozí je `$(OutputPath)`.

### <a name="includesymbols"></a>IncludeSymbols
Tato logická hodnota označuje, zda má balíček při zabalení projektu vytvořit další balíček symbolů. Formát balíčku symbolů je řízen `SymbolPackageFormat` vlastností.

### <a name="symbolpackageformat"></a>SymbolPackageFormat
Určuje formát balíčku symbolů. Pokud "Symbols. nupkg", bude balíček starších symbolů vytvořen s příponou *. Symbols. nupkg* , která obsahuje soubory PDB, knihovny DLL a další výstupní soubory. Pokud bude "snupkg", vytvoří se balíček symbolů snupkg obsahující přenosné soubory PDB. Výchozí hodnota je "Symbols. nupkg".

### <a name="includesource"></a>IncludeSource

Tato logická hodnota označuje, zda by měl proces balíčku vytvořit zdrojový balíček. Zdrojový balíček obsahuje zdrojový kód knihovny i soubory PDB. Zdrojové soubory jsou umístěny do `src/ProjectName` adresáře ve výsledném souboru balíčku.

### <a name="istool"></a>Nástroj

Určuje, zda jsou všechny výstupní soubory zkopírovány do složky *Tools* namísto složky *lib* . To se liší od a `DotNetCliTool` , která je určena nastavením `PackageType` v souboru *. csproj* .

### <a name="repositoryurl"></a>RepositoryUrl

Určuje adresu URL úložiště, ve kterém se nachází zdrojový kód balíčku, nebo ze kterého se vytváří.

### <a name="repositorytype"></a>RepositoryType

Určuje typ úložiště. Výchozí hodnota je "git".

### <a name="repositorybranch"></a>RepositoryBranch
Určuje název zdrojové větve v úložišti. Když je projekt zabalen do balíčku NuGet, přidá se do metadat balíčku.

### <a name="repositorycommit"></a>RepositoryCommit
Volitelné potvrzení změn úložiště nebo sada změn, které označují, na který zdroj byl balíček vytvořen. `RepositoryUrl`musí být také zadáno pro zahrnutí této vlastnosti. Když je projekt zabalen v balíčku NuGet, toto potvrzení nebo sada změn se přidá do metadat balíčku.

### <a name="nopackageanalysis"></a>NoPackageAnalysis

Určuje, že sada by neměla po sestavení balíčku spustit analýzu balíčku.

### <a name="minclientversion"></a>MinClientVersion

Určuje minimální verzi klienta NuGet, která může nainstalovat tento balíček vynutila nuget.exe a správcem balíčků sady Visual Studio.

### <a name="includebuildoutput"></a>IncludeBuildOutput

Tato logická hodnota určuje, zda mají být výstupní sestavení sestavení zabalena do souboru *. nupkg* nebo ne.

### <a name="includecontentinpack"></a>IncludeContentInPack

Tato logická hodnota určuje, zda `Content` budou do výsledného balíčku automaticky zahrnuty všechny položky, které mají typ. Výchozí formát je `true`.

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder

Určuje složku, kam se mají umístit výstupní sestavení. Výstupní sestavení (a další výstupní soubory) se zkopírují do příslušných složek rozhraní.

### <a name="contenttargetfolders"></a>ContentTargetFolders

Tato vlastnost určuje výchozí umístění, kde mají všechny soubory obsahu jít, pokud `PackagePath` nejsou pro ně zadány. Výchozí hodnota je Content; contentFiles.

### <a name="nuspecfile"></a>NuspecFile

Relativní nebo absolutní cesta k souboru *. nuspec* , který se používá pro balení.

> [!NOTE]
> Je-li zadán soubor *. nuspec* , používá se **výhradně** k balení informací a žádné informace v projektech se nepoužívají.

### <a name="nuspecbasepath"></a>NuspecBasePath

Základní cesta pro soubor *. nuspec*

### <a name="nuspecproperties"></a>NuspecProperties

Seznam párů klíč = hodnota oddělený středníkem.

## <a name="assemblyinfo-properties"></a>Vlastnosti AssemblyInfo

[Atributy sestavení](../../standard/assembly/set-attributes.md) , které byly obvykle přítomny v souboru *AssemblyInfo* , se nyní automaticky generují z vlastností.

### <a name="properties-per-attribute"></a>Vlastnosti na atribut

Jak je znázorněno v následující tabulce, každý atribut má vlastnost, která řídí svůj obsah a druhý, který zakazuje jeho generaci:

| Atribut                                                      | Vlastnost               | Vlastnost, která se má zakázat                             |
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

- `AssemblyVersion``FileVersion`ve výchozím nastavení je to, že se má přebírat hodnota `$(Version)` bez přípony. Například pokud `$(Version)` je `1.2.3-beta.4` , pak hodnota by byla `1.2.3` .
- `InformationalVersion`Výchozí hodnota je `$(Version)` .
- `InformationalVersion`má `$(SourceRevisionId)` připojení, pokud je vlastnost přítomna. Dá se zakázat pomocí `IncludeSourceRevisionInInformationalVersion` .
- `Copyright`a `Description` vlastnosti se také používají pro metadata NuGet.
- `Configuration`je sdílen se všemi procesy sestavení a nastavena prostřednictvím `--configuration` parametru `dotnet` příkazů.

### <a name="generateassemblyinfo"></a>GenerateAssemblyInfo

Logická hodnota, která povolí nebo zakáže všechny generace AssemblyInfo. Výchozí hodnota je `true`.

### <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

Cesta k vygenerovanému souboru s informacemi o sestavení Ve výchozím nastavení se jedná o soubor v `$(IntermediateOutputPath)` adresáři (obj).
