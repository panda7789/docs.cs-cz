---
title: Přidání do formátu csproj pro .NET Core
description: Přečtěte si o rozdílech mezi existujícími a soubory .NET Core csproj.
ms.date: 04/08/2019
ms.openlocfilehash: 4ce9227839a610308071c36185b63db8b1ee86ed
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739297"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Přidání do formátu csproj pro .NET Core

Tento dokument popisuje změny, které byly přidány do souborů projektu jako součást přesunutí z *Project. JSON* na *csproj* a [MSBuild](https://github.com/Microsoft/MSBuild). Další informace o obecných syntaxech souborů projektu a referenčních informacích naleznete v dokumentaci k [souboru projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .

## <a name="implicit-package-references"></a>Odkazy na implicitní balíčky

Na metabalíčky se implicitně odkazuje na základě cílových rozhraní .NET Framework určených ve vlastnosti `<TargetFramework>` nebo `<TargetFrameworks>` souboru projektu. `<TargetFrameworks>` se ignoruje, pokud je zadána hodnota `<TargetFramework>`, nezávisle na pořadí. Další informace najdete v tématu [balíčky, metabalíčky a rozhraní](../packages.md). 

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

### <a name="recommendations"></a>Doporučit

Vzhledem k tomu, že jsou implicitně odkazovány `Microsoft.NETCore.App` nebo `NETStandard.Library` metabalíčky, následující doporučené osvědčené postupy:

- Pokud cílíte na rozhraní .NET Core nebo .NET Standard, nikdy nemusíte mít explicitní odkaz na `Microsoft.NETCore.App` nebo `NETStandard.Library` metabalíčky prostřednictvím položky `<PackageReference>` v souboru projektu.
- Pokud potřebujete specifickou verzi modulu runtime při cílení na .NET Core, měli byste použít vlastnost `<RuntimeFrameworkVersion>` v projektu (například `1.0.4`) namísto odkazování na Metapackage.
  - K tomu může dojít, pokud používáte [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) a potřebujete konkrétní opravu verze 1.0.0 LTS runtime, například.
- Pokud potřebujete specifickou verzi `NETStandard.Library` Metapackage při cílení .NET Standard, můžete použít vlastnost `<NetStandardImplicitPackageVersion>` a nastavit požadovanou verzi.
- Nedávejte explicitně odkazy ani neaktualizujte `Microsoft.NETCore.App` ani `NETStandard.Library` Metapackage v projektech .NET Framework. Pokud je při použití balíčku NuGet založeného na .NET Standard nutná jakákoli verze `NETStandard.Library`, NuGet tuto verzi nainstaluje automaticky.

## <a name="implicit-version-for-some-package-references"></a>Implicitní verze pro některé odkazy na balíčky

Většina použití [`<PackageReference>`](#packagereference) vyžaduje nastavení atributu `Version` pro určení verze balíčku NuGet, která se má použít. Při použití .NET Core 2,1 nebo 2,2 a odkazování na [Microsoft. AspNetCore. app](/aspnet/core/fundamentals/metapackage-app) nebo [Microsoft. AspNetCore. All](/aspnet/core/fundamentals/metapackage)ale atribut není zbytečný. .NET Core SDK může automaticky vybrat verzi těchto balíčků, které by se měly použít.

### <a name="recommendation"></a>Základě

Při odkazování na balíčky `Microsoft.AspNetCore.App` nebo `Microsoft.AspNetCore.All` nezadávejte jejich verzi. Pokud je zadána verze, sada SDK může vytvořit upozornění NETSDK1071. Chcete-li toto upozornění vyřešit, odeberte verzi balíčku, jako v následujícím příkladu:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> Známý problém: sada .NET Core 2,1 SDK podporuje pouze tuto syntaxi pouze v případě, že projekt používá také Microsoft. NET. SDK. Web. To je vyřešeno v sadě .NET Core 2,2 SDK.

Tyto odkazy na ASP.NET Core metabalíčky mají mírně odlišné chování z většiny běžných balíčků NuGet. [Nasazení aplikací závislých na rozhraních](../deploying/index.md#framework-dependent-deployments-fdd) , která používají tyto metabalíčky, automaticky využívají ASP.NET Core sdílené rozhraní. Při použití metabalíčky se s aplikací nasadí **žádné** prostředky z odkazovaného ASP.NET Core balíčků NuGet – ASP.NET Core sdílené rozhraní obsahuje tyto prostředky. Prostředky ve sdíleném rozhraní jsou optimalizované pro cílovou platformu pro zlepšení času spuštění aplikace. Další informace o sdílených rozhraních naleznete v tématu [distribuční balíček .NET Core](../build/distribution-packaging.md).

*Je* -li zadána verze, je zpracována jako *minimální* verze ASP.NET Core sdílené architektury pro nasazení závislá na rozhraních a jako *Přesná* verze pro samostatně nasazená nasazení. To může mít následující důsledky:

- Pokud je verze ASP.NET Core nainstalovaná na serveru menší než verze zadaná na PackageReference, proces .NET Core se nepovede spustit. Aktualizace Metapackage jsou často k dispozici v NuGet.org před zpřístupněním aktualizací v hostitelských prostředích, jako je Azure. Aktualizace verze PackageReference na ASP.NET Core by mohla způsobit selhání nasazené aplikace.
- Pokud je aplikace nasazena jako [samostatné nasazení](../deploying/index.md#self-contained-deployments-scd), aplikace nemusí obsahovat nejnovější aktualizace zabezpečení .NET Core. Pokud není určena verze, může sada SDK automaticky zahrnovat nejnovější verzi ASP.NET Core v samostatném nasazení.

## <a name="default-compilation-includes-in-net-core-projects"></a>Výchozí kompilace zahrnuje v projektech .NET Core

S přesunem do formátu *csproj* v nejnovějších verzích sady SDK jsme přesunuli výchozí zahrnutí a vyloučení položek kompilace a integrovaných prostředků do souborů vlastností sady SDK. To znamená, že už nemusíte tyto položky v souboru projektu zadávat.

Hlavním důvodem pro to, aby to bylo, je omezit zbytečné soubory projektu. Výchozí hodnoty, které jsou obsaženy v sadě SDK, by měly pokrývat většinu běžných případů použití, takže je nemusíte opakovat v každém vytvořeném projektu. To vede k menšímu množství souborů projektu, které jsou v případě potřeby mnohem snazší a v případě potřeby upravitelné.

Následující tabulka ukazuje, který prvek a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuty a vyloučeny v sadě SDK:

| Prvek           | Zahrnout glob                              | Vyloučit glob                                                  | Odebrat glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Sestavení           | \* \* / \*. cs (nebo jiné jazykové rozšíření) | \* \* / \*. User;   \* \* / \*. \*proj;   \* 0 1 2. sln;   3 4 5 6. vssscc  | Není k dispozici                      |
| EmbeddedResource  | \* \* / \*. resx                              | \* \* / \*. User;  \* \* / \*. \*proj;  \* 0 1 2. sln;  3 4 5 6. vssscc     | Není k dispozici                      |
| Žádné              | \*\*/\*                                   | \* \* / \*. User;  \* \* / \*. \*proj;  \* 0 1 2. sln;  3 4 5 6. vssscc     | \* \* / \*. cs;  \* \* / \*. resx   |

> [!NOTE]
> **Exclude glob** vždy vyloučí složky `./bin` a `./obj`, které jsou reprezentovány vlastnostmi MSBuild v uvedeném pořadí `$(BaseOutputPath)` a `$(BaseIntermediateOutputPath)`. Všechna vyloučení jsou představována `$(DefaultItemExcludes)`.

Pokud jste v projektu globy a pokusíte se ho sestavit pomocí nejnovější sady SDK, zobrazí se následující chyba:

> Byly zahrnuty duplicitní položky kompilace. Sada .NET SDK obsahuje ve výchozím nastavení položky kompilace z adresáře projektu. Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultCompileItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.

Chcete-li se této chybě vyhnout, můžete buď odebrat explicitní položky `Compile`, které odpovídají těm, které jsou uvedeny v předchozí tabulce, nebo můžete nastavit vlastnost `<EnableDefaultCompileItems>` na `false`, například takto:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Nastavením této vlastnosti na `false` zakážete implicitní zahrnutí, vrátíte se do chování předchozích sad SDK, kde jste museli v projektu zadat výchozí globy.

Tato změna neupravuje hlavní mechanismy ostatních zahrnutí. Nicméně pokud chcete určit, například některé soubory, které mají být publikovány s vaší aplikací, můžete stále používat známé mechanismy v *csproj* pro to (například prvek `<Content>`).

`<EnableDefaultCompileItems>` zakazuje pouze `Compile` globy, ale nemá vliv na jiné globy, jako je například implicitní `None` glob, které platí také pro položky \*.cs. Z tohoto důvodu **Průzkumník řešení** v rámci projektu dál zobrazovat položky \*.cs, které jsou zahrnuté jako položky `None`. Podobným způsobem můžete nastavit `<EnableDefaultNoneItems>` na hodnotu false, chcete-li zakázat implicitní `None` glob, například:

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Chcete-li zakázat **všechna implicitní globy**, můžete vlastnost `<EnableDefaultItems>` nastavit na hodnotu `false`, jak je uvedeno v následujícím příkladu:

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Jak zobrazit celý projekt, když ho MSBuild uvidí

I když tyto změny csproj značně zjednodušují soubory projektu, je možné, že budete chtít zobrazit plně rozbalený projekt jako nástroj MSBuild, jakmile bude sada SDK a její cíle zahrnuté. Projekt předzpracování pomocí [přepínače `/pp`](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) příkazu [`dotnet msbuild`](dotnet-msbuild.md) , který ukazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky do sestavení bez skutečného sestavení projektu:

`dotnet msbuild -pp:fullproject.xml`

Pokud má projekt více cílových rozhraní, výsledky příkazu by měly být zaměřené jenom na jeden z nich zadáním jako vlastnost MSBuild:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Rozšíření

### <a name="sdk-attribute"></a>Atribut sady SDK

Kořenový element `<Project>` souboru *. csproj* má nový atribut nazvaný `Sdk`. `Sdk` určuje, kterou sadu SDK bude používat projekt. Sada SDK, jak popisuje [dokument vrstvení](cli-msbuild-architecture.md) , je sada [úloh](/visualstudio/msbuild/msbuild-tasks) a [cílů](/visualstudio/msbuild/msbuild-targets) nástroje MSBuild, které mohou sestavovat kód .NET Core. Pro .NET Core jsou k dispozici následující sady SDK:

1. .NET Core SDK s ID `Microsoft.NET.Sdk`
2. Sada Web SDK .NET Core s ID `Microsoft.NET.Sdk.Web`
3. Sada SDK knihovny tříd .NET Core Razor s ID `Microsoft.NET.Sdk.Razor`
4. Služba pracovních procesů .NET Core s ID `Microsoft.NET.Sdk.Worker` (od .NET Core 3,0)
5. WinForms rozhraní .NET Core a WPF s ID `Microsoft.NET.Sdk.WindowsDesktop` (od .NET Core 3,0)

Aby bylo možné používat nástroje .NET Core a sestavovat kód, je nutné mít atribut `Sdk` nastaven na jedno z těchto identifikátorů v prvku `<Project>`.

### <a name="packagereference"></a>PackageReference

Prvek položky `<PackageReference>` určuje [závislost NuGet v projektu](/nuget/consume-packages/package-references-in-project-files). Atribut `Include` určuje ID balíčku.

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Version

Požadovaný atribut `Version` určuje verzi balíčku, který se má obnovit. Atribut respektuje pravidla schématu [správy verzí NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards) . Výchozí chování je přesné porovnávání verzí. Například zadání `Version="1.2.3"` je ekvivalentní `[1.2.3]` notace NuGet pro přesný balíček verze balíčku.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets a PrivateAssets

atribut `IncludeAssets` určuje, které prostředky patřící k balíčku určenému parametrem `<PackageReference>` by měly být spotřebovány. Ve výchozím nastavení jsou zahrnuty všechny prostředky balíčku.

atribut `ExcludeAssets` určuje, které prostředky patřící k balíčku určenému parametrem `<PackageReference>` by neměly být spotřebovány.

atribut `PrivateAssets` určuje, které prostředky patřící k balíčku určenému parametrem `<PackageReference>` by měly být spotřebovány, ale nikoli do dalšího projektu. `Analyzers`, `Build` a `ContentFiles` assety jsou ve výchozím nastavení privátní, pokud tento atribut není k dispozici.

> [!NOTE]
> `PrivateAssets` je ekvivalentní prvku *Project. json*/*xproj* `SuppressParent`.

Tyto atributy mohou obsahovat jednu nebo více následujících položek oddělených středníkem `;`, pokud je uvedeno více než jedna položka:

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

Prvek položky `<DotNetCliToolReference>` Určuje nástroj CLI, který uživatel chce obnovit v kontextu projektu. Je náhradou za uzel `tools` v *Project. JSON*.

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a>Version

`Version` určuje verzi balíčku, který se má obnovit. Atribut respektuje pravidla schématu [správy verzí NuGet](/nuget/create-packages/dependency-versions#version-ranges) . Výchozí chování je přesné porovnávání verzí. Například zadání `Version="1.2.3"` je ekvivalentní `[1.2.3]` notace NuGet pro přesný balíček verze balíčku.

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

Pokud potřebujete publikovat více modulů runtime, použijte místo toho `<RuntimeIdentifiers>` (plural). `<RuntimeIdentifier>` může poskytovat rychlejší sestavení, je-li vyžadován pouze jeden modul runtime.

### <a name="packagetargetfallback"></a>PackageTargetFallback

Prvek vlastnosti `<PackageTargetFallback>` umožňuje zadat sadu kompatibilních cílů, které se mají použít při obnovování balíčků. Je navržena tak, aby povolovala balíčky, které používají dotnet [TxM (Target x moniker)](/nuget/schema/target-frameworks) pro práci s balíčky, které nedeklarují dotnet TxM. Pokud váš projekt používá TxM dotnet, pak všechny balíčky, na kterých závisí, musí mít také hodnotu dotnet TxM, pokud do projektu nepřidáte `<PackageTargetFallback>`, aby bylo možné platformy, které nejsou v dotnet, být kompatibilní s dotnet.

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

Při přechodu na MSBuild jsme přesunuli vstupní metadata, která se používají při balení balíčku NuGet z *Project. JSON* do souborů *. csproj* . Vstupy jsou vlastnosti nástroje MSBuild, takže musí přejít do skupiny `<PropertyGroup>`. Následuje seznam vlastností, které se používají jako vstupy do procesu balení při použití příkazu `dotnet pack` nebo `Pack`ho cíle MSBuild, který je součástí sady SDK:

### <a name="ispackable"></a>Ispackable nastavenou

Logická hodnota, která určuje, zda lze projekt zabalit. Výchozí hodnota je `true`.

### <a name="packageversion"></a>PackageVersion

Určuje verzi, kterou výsledný balíček bude mít. Akceptuje všechny formy řetězce verze NuGet. Výchozí hodnota je hodnota `$(Version)`, to znamená vlastnost `Version` v projektu.

### <a name="packageid"></a>PackageId

Určuje název výsledného balíčku. Pokud není zadaný, operace `pack` ve výchozím nastavení použije jako název balíčku název `AssemblyName` nebo adresáře.

### <a name="title"></a>Název

Popisný název balíčku, který se obvykle používá v uživatelském rozhraní, se zobrazuje jako v nuget.org a správce balíčků v aplikaci Visual Studio. Pokud není zadaný, použije se místo toho ID balíčku.

### <a name="authors"></a>Autoři

Středníkem oddělený seznam autorů balíčků, které odpovídají názvům profilů v nuget.org. Ty se zobrazí v galerii NuGet na nuget.org a používají se pro balíčky křížového odkazu stejnými autory.

### <a name="packagedescription"></a>PackageDescription

Dlouhý popis balíčku pro zobrazení uživatelského rozhraní.

### <a name="description"></a>Popis

Dlouhý popis pro sestavení. Pokud není zadaný `PackageDescription`, použije se tato vlastnost také jako Popis balíčku.

### <a name="copyright"></a>Úprava

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

Cesta k souboru s licencí v rámci balíčku Pokud používáte licenci, ke které se nepřiřadil identifikátor SPDX, nebo se jedná o vlastní licenci (jinak `PackageLicenseExpression` upřednostňovaná)

Nahrazuje `PackageLicenseUrl`, nelze kombinovat s `PackageLicenseExpression` a vyžaduje Visual Studio 15.9.4, .NET SDK 2.1.502 nebo 2.2.101 nebo novější.

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

Tato logická hodnota označuje, zda by měl proces balíčku vytvořit zdrojový balíček. Zdrojový balíček obsahuje zdrojový kód knihovny i soubory PDB. Zdrojové soubory jsou umístěny do složky `src/ProjectName` ve výsledném souboru balíčku.

### <a name="istool"></a>Nástroj

Určuje, zda jsou všechny výstupní soubory zkopírovány do složky *Tools* namísto složky *lib* . Všimněte si, že se liší od `DotNetCliTool`, který je určen nastavením `PackageType` v souboru *. csproj* .

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

Tato logická hodnota určuje, zda budou do výsledného balíčku automaticky zahrnuty všechny položky, které mají typ `Content`. Výchozí hodnota je `true`.

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder

Určuje složku, kam se mají umístit výstupní sestavení. Výstupní sestavení (a další výstupní soubory) se zkopírují do příslušných složek rozhraní.

### <a name="contenttargetfolders"></a>ContentTargetFolders

Tato vlastnost určuje výchozí umístění, kde mají všechny soubory obsahu jít, pokud pro ně není zadána `PackagePath`. Výchozí hodnota je Content; contentFiles.

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

Každý atribut má vlastnost, která řídí svůj obsah a druhý pro zakázání jeho generování, jak je znázorněno v následující tabulce:

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

- `AssemblyVersion` a `FileVersion` se standardně převezme hodnota `$(Version)` bez přípony. Pokud je například `$(Version)` `1.2.3-beta.4`, hodnota by byla `1.2.3`.
- `InformationalVersion` je výchozí hodnotou `$(Version)`.
- `InformationalVersion` má připojené `$(SourceRevisionId)`, pokud je vlastnost přítomná. Dá se zakázat pomocí `IncludeSourceRevisionInInformationalVersion`.
- pro metadata NuGet se používají také vlastnosti `Copyright` a `Description`.
- `Configuration` se sdílí se všemi procesy sestavení a nastavuje se pomocí parametru `--configuration` příkazů `dotnet`.

### <a name="generateassemblyinfo"></a>GenerateAssemblyInfo

Logická hodnota, která povolí nebo zakáže všechny generace AssemblyInfo. Výchozí hodnota je `true`.

### <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

Cesta k vygenerovanému souboru s informacemi o sestavení Ve výchozím nastavení se jedná o soubor v adresáři `$(IntermediateOutputPath)` (obj).
