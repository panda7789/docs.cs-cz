---
title: Přidání do formátu csproj pro .NET Core
description: Přečtěte si o rozdílech mezi existujícími a soubory .NET Core csproj.
ms.date: 04/08/2019
ms.openlocfilehash: 202c1867ae6404db074e6196b28ffe5f453ef5bf
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965604"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Přidání do formátu csproj pro .NET Core

Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunutí z *Project. JSON* na *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild). Další informace o obecných syntaxech souborů projektu a referenčních informacích naleznete v dokumentaci k [souboru projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .

## <a name="implicit-package-references"></a>Odkazy na implicitní balíčky

Na metabalíčky se implicitně odkazuje na základě cílových rozhraní .NET Framework určených ve vlastnosti `<TargetFramework>` nebo `<TargetFrameworks>` souboru projektu. `<TargetFrameworks>` se ignoruje, pokud je zadána `<TargetFramework>`, nezávisle na pořadí. Další informace najdete v tématech [balíčky, metabalíčky a rozhraní](../packages.md).

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

Vzhledem k tomu, že se na `Microsoft.NETCore.App` nebo `NETStandard.Library` metabalíčky implicitně odkazují, následující doporučené osvědčené postupy:

- Pokud cílíte na rozhraní .NET Core nebo .NET Standard, nikdy nemusíte mít explicitní odkaz na `Microsoft.NETCore.App` nebo `NETStandard.Library` metabalíčky prostřednictvím položky `<PackageReference>` v souboru projektu.
- Pokud potřebujete specifickou verzi modulu runtime při cílení na .NET Core, měli byste použít vlastnost `<RuntimeFrameworkVersion>` v projektu (například `1.0.4`) namísto odkazování na Metapackage.
  - K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) a potřebujete konkrétní opravu verze 1.0.0 LTS runtime, například.
- Pokud potřebujete specifickou verzi `NETStandard.Library` Metapackage při cílení na .NET Standard, můžete použít vlastnost `<NetStandardImplicitPackageVersion>` a nastavit požadovanou verzi.
- Nedávejte explicitně odkazy ani neaktualizujte `Microsoft.NETCore.App` ani `NETStandard.Library` Metapackage v projektech .NET Framework. Pokud je při použití balíčku NuGet založeného na .NET Standard potřeba libovolná verze `NETStandard.Library`, NuGet tuto verzi nainstaluje automaticky.

## <a name="implicit-version-for-some-package-references"></a>Implicitní verze pro některé odkazy na balíčky

Většina použití [`<PackageReference>`](#packagereference) vyžaduje nastavení atributu `Version` k určení verze balíčku NuGet, která se má použít. Při použití .NET Core 2,1 nebo 2,2 a odkazování na [Microsoft. AspNetCore. app](/aspnet/core/fundamentals/metapackage-app) nebo [Microsoft. AspNetCore. All](/aspnet/core/fundamentals/metapackage)ale atribut není zbytečný. .NET Core SDK může automaticky vybrat verzi těchto balíčků, které by se měly použít.

### <a name="recommendation"></a>Doporučení

Při odkazování na balíčky `Microsoft.AspNetCore.App` nebo `Microsoft.AspNetCore.All` nezadávejte jejich verzi. Pokud je zadána verze, sada SDK může vytvořit upozornění NETSDK1071. Chcete-li toto upozornění vyřešit, odeberte verzi balíčku, jako v následujícím příkladu:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> Známý problém: sada .NET Core 2,1 SDK podporuje pouze tuto syntaxi pouze v případě, že projekt používá také Microsoft. NET. SDK. Web. To je vyřešeno v sadě .NET Core 2,2 SDK.

Tyto odkazy na ASP.NET Core metabalíčky mají mírně odlišné chování z většiny běžných balíčků NuGet. [Nasazení aplikací závislých na rozhraních](../deploying/index.md#framework-dependent-deployments-fdd) , která používají tyto metabalíčky, automaticky využívají ASP.NET Core sdílené rozhraní. Při použití metabalíčky se s aplikací nasadí **žádné** prostředky z odkazovaného ASP.NET Core balíčků NuGet – ASP.NET Core sdílené rozhraní obsahuje tyto prostředky. Prostředky ve sdíleném rozhraní jsou optimalizované pro cílovou platformu pro zlepšení času spuštění aplikace. Další informace o sdílených rozhraních naleznete v tématu [distribuční balíček .NET Core](../distribution-packaging.md).

*Je* -li zadána verze, je zpracována jako *minimální* verze ASP.NET Core sdílené architektury pro nasazení závislá na rozhraních a jako *Přesná* verze pro samostatně nasazená nasazení. To může mít následující důsledky:

- Pokud je verze ASP.NET Core nainstalovaná na serveru menší než verze zadaná na PackageReference, proces .NET Core se nepovede spustit. Aktualizace Metapackage jsou často k dispozici v NuGet.org před zpřístupněním aktualizací v hostitelských prostředích, jako je Azure. Aktualizace verze PackageReference na ASP.NET Core by mohla způsobit selhání nasazené aplikace.
- Pokud je aplikace nasazena jako [samostatné nasazení](../deploying/index.md#self-contained-deployments-scd), aplikace nemusí obsahovat nejnovější aktualizace zabezpečení .NET Core. Pokud není určena verze, může sada SDK automaticky zahrnovat nejnovější verzi ASP.NET Core v samostatném nasazení.

## <a name="default-compilation-includes-in-net-core-projects"></a>Výchozí kompilace zahrnuje v projektech .NET Core

S přesunem do formátu *csproj* v nejnovějších verzích sady SDK jsme přesunuli výchozí zahrnutí a vyloučení položek kompilace a integrovaných prostředků do souborů vlastností sady SDK. To znamená, že už nemusíte tyto položky v souboru projektu zadávat.

Hlavním důvodem pro to, aby to bylo, je omezit zbytečné soubory projektu. Výchozí hodnoty, které jsou obsaženy v sadě SDK, by měly pokrývat většinu běžných případů použití, takže je nemusíte opakovat v každém vytvořeném projektu. To vede k menšímu množství souborů projektu, které jsou v případě potřeby mnohem snazší a v případě potřeby upravitelné.

Následující tabulka ukazuje, který prvek a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuty a vyloučeny v sadě SDK:

| Prvek           | Zahrnout glob                              | Vyloučit glob                                                  | Odebrat glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Kompilace           | \*\*/\*. cs (nebo jiné jazykové rozšíření) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | NEUŽÍVÁ SE.                      |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | NEUŽÍVÁ SE.                      |
| Žádné              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*. cs; \*\*/\*. resx   |

> [!NOTE]
> **Vyloučit glob** vždy vylučuje `./bin` a `./obj` složky, které jsou reprezentovány `$(BaseOutputPath)` a `$(BaseIntermediateOutputPath)` vlastnostech nástroje MSBuild v uvedeném pořadí. Všechna vyloučení jsou představována `$(DefaultItemExcludes)`.

Pokud jste v projektu globy a pokusíte se ho sestavit pomocí nejnovější sady SDK, zobrazí se následující chyba:

> Byly zahrnuty duplicitní položky kompilace. Sada .NET SDK obsahuje ve výchozím nastavení položky kompilace z adresáře projektu. Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultCompileItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.

Chcete-li se této chybě vyhnout, můžete buď odebrat explicitní `Compile` položky, které odpovídají těm, které jsou uvedeny v předchozí tabulce, nebo můžete nastavit vlastnost `<EnableDefaultCompileItems>` na `false`, například takto:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Nastavením této vlastnosti na `false` zakážete implicitní zahrnutí, vrátíte se do chování předchozích sad SDK, kde jste museli zadat výchozí globy v projektu.

Tato změna neupravuje hlavní mechanismy ostatních zahrnutí. Nicméně pokud chcete určit, například některé soubory, které mají být publikovány s vaší aplikací, můžete i nadále používat známé mechanismy v souboru *csproj* pro to (například `<Content>` element).

`<EnableDefaultCompileItems>` zakáže pouze `Compile` globy, ale nemá vliv na jiné globy, jako je například implicitní `None` glob, které platí i pro \*položky. cs. Z tohoto důvodu **Průzkumník řešení** nadále zobrazovat \*. cs položky jako součást projektu, včetně položek `None`. Podobným způsobem můžete nastavit `<EnableDefaultNoneItems>` na hodnotu false, chcete-li zakázat implicitní `None` glob, například:

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Chcete-li zakázat **všechny implicitní globy**, můžete nastavit vlastnost `<EnableDefaultItems>` tak, aby `false` jako v následujícím příkladu:

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Jak zobrazit celý projekt, když ho MSBuild uvidí

I když tyto změny csproj značně zjednodušují soubory projektu, je možné, že budete chtít zobrazit plně rozbalený projekt jako nástroj MSBuild, jakmile bude sada SDK a její cíle zahrnuté. Projekt předzpracování pomocí [`/pp`ového přepínače](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) příkazu [`dotnet msbuild`](dotnet-msbuild.md) , který ukazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky na sestavení bez skutečného sestavení projektu:

`dotnet msbuild -pp:fullproject.xml`

Pokud má projekt více cílových rozhraní, výsledky příkazu by měly být zaměřené jenom na jeden z nich zadáním jako vlastnost MSBuild:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Rozšíření

### <a name="sdk-attribute"></a>Atribut sady SDK

Kořenový `<Project>` element souboru *. csproj* má nový atribut nazvaný `Sdk`. `Sdk` určuje, kterou sadu SDK bude projekt používat. Sada SDK, jak popisuje [dokument vrstvení](cli-msbuild-architecture.md) , je sada [úloh](/visualstudio/msbuild/msbuild-tasks) a [cílů](/visualstudio/msbuild/msbuild-targets) nástroje MSBuild, které mohou sestavovat kód .NET Core. Pro .NET Core jsou k dispozici následující sady SDK:

1. .NET Core SDK s ID `Microsoft.NET.Sdk`
2. Sada Web SDK .NET Core s ID `Microsoft.NET.Sdk.Web`
3. Sada SDK knihovny tříd .NET Core Razor s ID `Microsoft.NET.Sdk.Razor`
4. Služba pracovních procesů .NET Core s ID `Microsoft.NET.Sdk.Worker` (od .NET Core 3,0)
5. WinForms rozhraní .NET Core a WPF s ID `Microsoft.NET.Sdk.WindowsDesktop` (od .NET Core 3,0)

Aby bylo možné používat nástroje .NET Core a sestavovat kód, je nutné mít atribut `Sdk` nastaven na jedno z těchto identifikátorů `<Project>` elementu.

### <a name="packagereference"></a>PackageReference

Element `<PackageReference>` Item Určuje [závislost NuGet v projektu](/nuget/consume-packages/package-references-in-project-files). Atribut `Include` Určuje ID balíčku.

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Version

Atribut Required `Version` určuje verzi balíčku, který má být obnoven. Atribut respektuje pravidla schématu [správy verzí NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards) . Výchozí chování je minimální verze (včetně shody). Například zadání `Version="1.2.3"` odpovídá zápisu NuGet `[1.2.3, )` a znamená, že vyřešený balíček bude mít verzi 1.2.3, je-li k dispozici, nebo více jinak.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets a PrivateAssets

`IncludeAssets` atribut určuje, které prostředky patřící k balíčku určenému `<PackageReference>` by měly být spotřebovány. Ve výchozím nastavení jsou zahrnuty všechny prostředky balíčku.

atribut `ExcludeAssets` určuje, které prostředky patřící k balíčku určenému `<PackageReference>` by neměly být spotřebovány.

atribut `PrivateAssets` určuje, které prostředky patřící k balíčku určenému `<PackageReference>` by měly být spotřebovány, ale nikoli do dalšího projektu. `Analyzers`, `Build` a `ContentFiles` assety jsou ve výchozím nastavení privátní, pokud tento atribut není k dispozici.

> [!NOTE]
> `PrivateAssets` je ekvivalentem elementu *Project. json*/*xproj* `SuppressParent`.

Tyto atributy mohou obsahovat jednu nebo více následujících položek oddělených středníkem `;` znak, pokud je uvedena více než jedna z těchto hodnot:

- `Compile` – obsah složky *lib* je k dispozici pro zkompilování.
- `Runtime` – obsah *běhové* složky se distribuuje.
- `ContentFiles` – používá se obsah složky *contentFiles* .
- `Build` – používají se props/targets ve složce *Build* .
- `Native` – obsah z nativních assetů se zkopíruje do *výstupní* složky pro modul runtime.
- `Analyzers` – používají se analyzátory.

Atribut může případně obsahovat:

- `None` – žádný z prostředků se nepoužívá.
- `All` – používají se všechny prostředky.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference

Element `<DotNetCliToolReference>` Item Určuje nástroj CLI, který uživatel chce obnovit v kontextu projektu. Je náhradou pro `tools` uzel v *Project. JSON*.

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

Všimněte si, že `DotNetCliToolReference` se [teď už nepoužívá](https://github.com/dotnet/announcements/issues/107) , a to ve prospěch [místních nástrojů .NET Core](https://aka.ms/local-tools).

#### <a name="version"></a>Version

`Version` určuje verzi balíčku, který má být obnoven. Atribut respektuje pravidla schématu [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) . Výchozí chování je minimální verze (včetně shody). Například zadání `Version="1.2.3"` odpovídá zápisu NuGet `[1.2.3, )` a znamená, že vyřešený balíček bude mít verzi 1.2.3, je-li k dispozici, nebo více jinak.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

Element vlastnosti `<RuntimeIdentifiers>` umožňuje zadat seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) pro daný projekt oddělený středníkem.
Identifikátorů RID umožňuje publikování samostatně obsažených nasazení.

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier

Prvek vlastnosti `<RuntimeIdentifier>` umožňuje zadat pouze jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt. Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

Pokud potřebujete publikovat více modulů runtime, použijte místo toho `<RuntimeIdentifiers>` (plural). `<RuntimeIdentifier>` můžou poskytovat rychlejší buildy, když je potřeba jenom jeden modul runtime.

### <a name="packagetargetfallback"></a>PackageTargetFallback

Prvek vlastnosti `<PackageTargetFallback>` umožňuje zadat sadu kompatibilních cílů, které se mají použít při obnovování balíčků. Je navržena tak, aby povolovala balíčky, které používají dotnet [TxM (Target x moniker)](/nuget/schema/target-frameworks) pro práci s balíčky, které nedeklarují dotnet TxM. Pokud váš projekt používá TxM dotnet, pak všechny balíčky, na kterých závisí, musí mít také hodnotu dotnet TxM, pokud nepřidáte `<PackageTargetFallback>` do projektu, aby bylo umožněno kompatibilitu platforem mimo dotnet s dotnet.

Následující příklad poskytuje záložní hodnoty pro všechny cíle v projektu:

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

Následující příklad určuje pouze zálohy pro cíl `netcoreapp2.1`:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a>Události sestavení

Způsob, jakým se změnily události před sestavením a po sestavení, jsou uvedeny v souboru projektu. Vlastnosti PreBuildEvent a PostBuildEvent nejsou doporučovány ve formátu projektu ve stylu sady SDK, protože makra jako $ (ProjectDir) nejsou vyřešena. Například následující kód již není podporován:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

V projektech se styly sady SDK použijte cíl MSBuild s názvem `PreBuild` nebo `PostBuild` a nastavte vlastnost `BeforeTargets` pro `PreBuild` nebo vlastnost `AfterTargets` pro `PostBuild`. Pro předchozí příklad použijte následující kód:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>Můžete použít libovolný název pro cíle nástroje MSBuild, ale rozhraní IDE sady Visual Studio rozpozná `PreBuild` a `PostBuild` cíle, proto doporučujeme použít tyto názvy, abyste mohli upravovat příkazy v integrovaném vývojovém prostředí sady Visual Studio.

## <a name="nuget-metadata-properties"></a>Vlastnosti metadat NuGet

Při přechodu na MSBuild jsme přesunuli vstupní metadata, která se používají při balení balíčku NuGet z *Project. JSON* do souborů *. csproj* . Vstupy jsou vlastnosti nástroje MSBuild, takže musí jít do skupiny `<PropertyGroup>`. Následuje seznam vlastností, které se používají jako vstupy do procesu balení při použití příkazu `dotnet pack` nebo `Pack`ho cíle MSBuild, který je součástí sady SDK:

### <a name="ispackable"></a>Ispackable nastavenou

Logická hodnota, která určuje, zda lze projekt zabalit. Výchozí hodnota je `true`.

### <a name="packageversion"></a>PackageVersion

Určuje verzi, kterou výsledný balíček bude mít. Akceptuje všechny formy řetězce verze NuGet. Výchozí hodnota je hodnota `$(Version)`, to znamená vlastnost `Version` v projektu.

### <a name="packageid"></a>PackageId

Určuje název výsledného balíčku. Pokud tento parametr nezadáte, použije operace `pack` ve výchozím nastavení jako název balíčku název `AssemblyName` nebo adresáře.

### <a name="title"></a>Název

Popisný název balíčku, který se obvykle používá v uživatelském rozhraní, se zobrazuje jako v nuget.org a správce balíčků v aplikaci Visual Studio. Pokud není zadaný, použije se místo toho ID balíčku.

### <a name="authors"></a>Autoři

Středníkem oddělený seznam autorů balíčků, které odpovídají názvům profilů v nuget.org. Ty se zobrazí v galerii NuGet na nuget.org a používají se pro balíčky křížového odkazu stejnými autory.

### <a name="packagedescription"></a>PackageDescription

Dlouhý popis balíčku pro zobrazení uživatelského rozhraní.

### <a name="description"></a>Popis

Dlouhý popis pro sestavení. Pokud není zadán `PackageDescription`, tato vlastnost se používá také jako Popis balíčku.

### <a name="copyright"></a>Copyright

Podrobnosti o autorských právech pro balíček.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance

Logická hodnota, která určuje, zda klient musí požádat spotřebitele o přijetí licence k balíčku před instalací balíčku. Výchozí hodnota je `false`.

### <a name="packagelicenseexpression"></a>PackageLicenseExpression

Identifikátor nebo výraz [licence SPDX](https://spdx.org/licenses/) Například `Apache-2.0`.

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
> V jednom okamžiku může být zadána pouze jedna z `PackageLicenseExpression`, `PackageLicenseFile` a `PackageLicenseUrl`.

### <a name="packagelicensefile"></a>PackageLicenseFile

Cesta k souboru s licencí v rámci balíčku, pokud používáte licenci, ke které se nepřiřadil identifikátor SPDX, nebo se jedná o vlastní licenci (jinak `PackageLicenseExpression` upřednostňovaná)

Nahrazuje `PackageLicenseUrl`, nelze kombinovat s `PackageLicenseExpression`a vyžaduje Visual Studio verze 15.9.4 a .NET SDK 2.1.502 nebo 2.2.101 nebo novější.

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

### <a name="packageiconurl"></a>PackageIconUrl

Adresa URL obrázku 64 × 64 s průhledným pozadím, který se má použít jako ikona balíčku v zobrazení uživatelského rozhraní.

### <a name="packagereleasenotes"></a>PackageReleaseNotes

Poznámky k verzi balíčku

### <a name="packagetags"></a>PackageTags

Seznam značek oddělených středníkem, který určuje balíček.

### <a name="packageoutputpath"></a>PackageOutputPath

Určuje výstupní cestu, do které bude zahozen zabalený balíček. Výchozí hodnota je `$(OutputPath)`.

### <a name="includesymbols"></a>IncludeSymbols
Tato logická hodnota označuje, zda má balíček při zabalení projektu vytvořit další balíček symbolů. Formát balíčku symbolů je řízen vlastností `SymbolPackageFormat`.

### <a name="symbolpackageformat"></a>SymbolPackageFormat
Určuje formát balíčku symbolů. Pokud "Symbols. nupkg", bude balíček starších symbolů vytvořen s příponou *. Symbols. nupkg* , která obsahuje soubory PDB, knihovny DLL a další výstupní soubory. Pokud bude "snupkg", vytvoří se balíček symbolů snupkg obsahující přenosné soubory PDB. Výchozí hodnota je "Symbols. nupkg".

### <a name="includesource"></a>IncludeSource

Tato logická hodnota označuje, zda by měl proces balíčku vytvořit zdrojový balíček. Zdrojový balíček obsahuje zdrojový kód knihovny i soubory PDB. Zdrojové soubory jsou umístěny pod `src/ProjectName` adresář ve výsledném souboru balíčku.

### <a name="istool"></a>Nástroj

Určuje, zda jsou všechny výstupní soubory zkopírovány do složky *Tools* namísto složky *lib* . To se liší od `DotNetCliTool`, která je určena nastavením `PackageType` v souboru *. csproj* .

### <a name="repositoryurl"></a>RepositoryUrl

Určuje adresu URL úložiště, ve kterém se nachází zdrojový kód balíčku, nebo ze kterého se vytváří.

### <a name="repositorytype"></a>RepositoryType

Určuje typ úložiště. Výchozí hodnota je "git".

### <a name="repositorybranch"></a>RepositoryBranch
Určuje název zdrojové větve v úložišti. Když je projekt zabalen do balíčku NuGet, přidá se do metadat balíčku.

### <a name="repositorycommit"></a>RepositoryCommit
Volitelné potvrzení změn úložiště nebo sada změn, které označují, na který zdroj byl balíček vytvořen. pro zahrnutí této vlastnosti je také nutné zadat `RepositoryUrl`. Když je projekt zabalen v balíčku NuGet, toto potvrzení nebo sada změn se přidá do metadat balíčku.

### <a name="nopackageanalysis"></a>NoPackageAnalysis

Určuje, že sada by neměla po sestavení balíčku spustit analýzu balíčku.

### <a name="minclientversion"></a>MinClientVersion

Určuje minimální verzi klienta NuGet, která může nainstalovat tento balíček, který vynutila NuGet. exe a správce balíčků sady Visual Studio.

### <a name="includebuildoutput"></a>IncludeBuildOutput

Tato logická hodnota určuje, zda mají být výstupní sestavení sestavení zabalena do souboru *. nupkg* nebo ne.

### <a name="includecontentinpack"></a>IncludeContentInPack

Tato logická hodnota určuje, zda budou všechny položky, které mají typ `Content`, zahrnuty do výsledného balíčku automaticky. Výchozí hodnota je `true`.

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder

Určuje složku, kam se mají umístit výstupní sestavení. Výstupní sestavení (a další výstupní soubory) se zkopírují do příslušných složek rozhraní.

### <a name="contenttargetfolders"></a>ContentTargetFolders

Tato vlastnost určuje výchozí umístění, ve kterém mají všechny soubory obsahu jít, pokud pro ně není `PackagePath` určena. Výchozí hodnota je Content; contentFiles.

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

- `AssemblyVersion` a `FileVersion` výchozím nastavení je přebírat hodnotu `$(Version)` bez přípony. Například pokud je `$(Version)` `1.2.3-beta.4`, hodnota by byla `1.2.3`.
- `InformationalVersion` výchozí hodnotu `$(Version)`.
- `InformationalVersion` má `$(SourceRevisionId)` připojen, pokud je vlastnost přítomna. Dá se zakázat pomocí `IncludeSourceRevisionInInformationalVersion`.
- vlastnosti `Copyright` a `Description` se také používají pro metadata NuGet.
- `Configuration` se sdílí se všemi procesy sestavení a nastavuje se prostřednictvím parametru `--configuration` `dotnet` příkazů.

### <a name="generateassemblyinfo"></a>GenerateAssemblyInfo

Logická hodnota, která povolí nebo zakáže všechny generace AssemblyInfo. Výchozí hodnota je `true`.

### <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

Cesta k vygenerovanému souboru s informacemi o sestavení Ve výchozím nastavení se jedná o soubor v adresáři `$(IntermediateOutputPath)` (obj).
