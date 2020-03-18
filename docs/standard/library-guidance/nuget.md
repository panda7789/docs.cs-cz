---
title: Knihovny NuGet a .NET
description: Doporučení osvědčených postupů pro balení s NuGet pro knihovny .NET.
ms.date: 01/15/2019
ms.openlocfilehash: f1e8d39fe2988f11ce7fd351a4d6bee6d322f2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400517"
---
# <a name="nuget"></a>NuGet

NuGet je správce balíčků pro ekosystém .NET a je primární způsob, jak vývojáři zjišťovat a získávat knihovny open source .NET. [NuGet.org](https://www.nuget.org/), bezplatná služba poskytovaná společností Microsoft pro hostování balíčků NuGet, je primárním hostitelem pro veřejné balíčky NuGet, ale můžete publikovat na vlastních službách NuGet, jako jsou [MyGet](https://www.myget.org/) a [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>Vytvoření balíčku NuGet

Balíček NuGet`*.nupkg`( ) je soubor ZIP, který obsahuje sestavení rozhraní .NET a přidružená metadata.

Existují dva hlavní způsoby, jak vytvořit balíček NuGet. Novější a doporučený způsob je vytvořit balíček z projektu ve stylu sady SDK (soubor projektu, jehož obsah začíná `<Project Sdk="Microsoft.NET.Sdk">`). Sestavení a cíle jsou automaticky přidány do balíčku a zbývající metadata je přidán a soubor MSBuild, jako je název balíčku a číslo verze. Kompilace s [`dotnet pack`](../../core/tools/dotnet-pack.md) příkazem výstupy souboru `*.nupkg` namísto sestavení.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

Starší způsob vytvoření balíčku NuGet je `*.nuspec` se `nuget.exe` souborem a nástrojem příkazového řádku. Soubor nuspec poskytuje skvělou kontrolu, ale musíte pečlivě určit, jaké sestavení a cíle zahrnout do konečného balíčku NuGet. Je snadné udělat chybu nebo pro někoho, kdo zapomene aktualizovat nuspec při provádění změn. Výhodou nuspec je můžete použít vytvořit Balíčky NuGet pro architektury, které ještě nepodporují soubor projektu ve stylu SDK.

✔️ zvažte použití souboru projektu ve stylu sady SDK k vytvoření balíčku NuGet.

## <a name="package-dependencies"></a>Závislosti balíčků

NuGet balíček závislosti jsou podrobně popsány v článku [závislosti.](./dependencies.md)

## <a name="important-nuget-package-metadata"></a>Důležitá metadata balíčku NuGet

Balíček NuGet podporuje mnoho [vlastností metadat](/nuget/reference/nuspec). Následující tabulka obsahuje základní metadata, která by měl každý balíček v NuGet.org poskytnout:

| Název vlastnosti MSBuild              | Název Nuspec              | Popis  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | Identifikátor balíčku. Předponu z identifikátoru lze rezervovat, pokud splňuje [kritéria](/nuget/reference/id-prefix-reservation). |
| `PackageVersion`                   | `version`                  | NuGet verze balíčku. Další informace naleznete v tématu [NuGet verze balíčku](./versioning.md#nuget-package-version).             |
| `Title`                            | `title`                    | Lidský název balíčku. Je výchozí na `PackageId`.             |
| `Description`                      | `description`              | Dlouhý popis balíčku zobrazeného v ui.             |
| `Authors`                          | `authors`                  | Seznam autorů balíčků oddělených čárkami, který odpovídá názvům profilů na nuget.org.             |
| `PackageTags`                      | `tags`                     | Mezera oddělený seznam značek a klíčových slov, které popisují balíček. Značky se používají při hledání balíčků.             |
| `PackageIconUrl`                   | `iconUrl`                  | Adresa URL obrázku, který má být používán jako ikona balíčku. Adresa URL by měla být HTTPS a obrázek by měl být 64x64 a měl by mít průhledné pozadí.             |
| `PackageProjectUrl`                | `projectUrl`               | Adresa URL domovské stránky projektu nebo zdrojového úložiště.             |
| `PackageLicenseExpression`         | `license`                  | [Identifikátor SPDX](https://spdx.org/licenses/)licence projektu . Identifikátor mohou používat pouze licence schválené OSI a FSF. Ostatní licence by `PackageLicenseFile`měly používat . Přečtěte si další informace o [ `license` metadatech](/nuget/reference/nuspec#license). |

> [!IMPORTANT]
> Projekt bez licence výchozí [výhradní autorská práva](https://choosealicense.com/no-permission/), takže je právně nemožné pro ostatní lidi k použití.

✔️ zvažte výběr názvu balíčku NuGet s předponou, která splňuje [kritéria](/nuget/reference/id-prefix-reservation)rezervace předpony NuGet .

✔️ do použít HTTPS href na ikonu balíčku.

> Weby, jako je NuGet.org spuštěna s povoleným protokolem HTTPS a zobrazení obrázku, který není https, vytvoří upozornění na smíšený obsah.

✔️ do použít obrázek ikony balíčku, který je 64x64 a má průhledné pozadí pro nejlepší výsledky zobrazení.

✔️ zvažte nastavení [zdrojového odkazu](./sourcelink.md) pro přidání metadat správy zdrojového kódu do sestavení a balíčku NuGet.

> Zdrojový odkaz `RepositoryUrl` automaticky `RepositoryType` přidá a metadata nuget balíčku. Zdrojový odkaz také přidává informace o přesném zdrojovém kódu, ze kterého byl balíček vytvořen. Například balíček vytvořený z úložiště Git bude mít hash potvrzení přidánjako metadata.

## <a name="pre-release-packages"></a>Předběžné verze balíčků

Balíčky NuGet s příponou verze jsou považovány za [předběžnou verzi](/nuget/create-packages/prerelease-packages). Ve výchozím nastavení uživatelské rozhraní NuGet Package Manager zobrazuje stabilní verze, pokud se uživatel nepřihlásí k předběžným verzím balíčků, takže předběžné verze balíčků jsou ideální pro testování uživatelů s omezenýmpřístupem.

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> Stabilní balíček nemůže záviset na předběžné verzi balíčku. Musíte buď vytvořit svůj vlastní balíček pre-release, nebo závisí na starší stabilní verzi.

![Závislost balíčku před vydáním nuget](./media/nuget/nuget-prerelease-package.png "Závislost balíčku před vydáním nuget")

✔️ do publikovat předběžný balíček při testování, náhledu nebo experimentování.

✔️ do publikovat stabilní balíček, když jeho připraven, takže ostatní stabilní balíčky mohou odkazovat.

## <a name="symbol-packages"></a>Balíčky symbolů

Soubory symbolů (`*.pdb`) jsou vytvářeny kompilátorem .NET vedle sestavení. Soubory symbolů mapují umístění spuštění na původní zdrojový kód, takže můžete krokovat zdrojový kód při spuštění pomocí ladicího programu. NuGet podporuje [generování samostatného`*.snupkg`balíčku symbolů ( )](/nuget/create-packages/symbol-packages-snupkg) obsahujícísoubory symbolů vedle hlavního balíčku obsahujícího sestavení .NET. Myšlenka symbolbalíčky je, že jsou hostovány na serveru symbolů a jsou staženy pouze nástrojem, jako je Visual Studio na vyžádání.

NuGet.org hostí vlastní [úložiště serverů symbolů](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server). Vývojáři mohou použít symboly publikované na `https://symbols.nuget.org/download/symbols` serveru symbolů NuGet.org přidáním [zdrojů symbolů v sadě Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).

> [!IMPORTANT]
> Server symbolů NuGet.org podporuje pouze nové`*.pdb` [přenosné soubory symbolů](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) ( ) vytvořené projekty ve stylu sady SDK.
>
> Chcete-li při ladění knihovny .NET používat NuGet.org server symbolů, musí mít vývojáři visual studio 2017 verze 15.9 nebo novější.

Alternativou k vytvoření balíčku symbolje vkládání souborů symbolů v hlavním balíčku NuGet. Hlavní balíček NuGet bude větší, ale vložené soubory symbolů znamená, že vývojáři nemusí konfigurovat NuGet.org server symbolů. Pokud vytváříte balíček NuGet pomocí projektu ve stylu sady SDK, můžete `AllowedOutputExtensionsInPackageBuildOutputFolder` vložit soubory symbolů nastavením vlastnosti:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

Nevýhodou vkládání souborů symbolů je, že zvětšují velikost balíčku přibližně o 30 % pro knihovny .NET zkompilované pomocí projektů ve stylu sady SDK. Pokud velikost balíčku je problém, měli byste publikovat symboly v balíčku symbolmísto.

✔️ ZVAŽTe publikování symbolů`*.snupkg`jako balíčku symbolů ( ) k NuGet.org

> Balíčky`*.snupkg`symbolů ( ) poskytují vývojářům dobré prostředí ladění na vyžádání bez nadýmání velikosti hlavního balíčku a ovlivňující výkon obnovení pro ty, kteří nemají v úmyslu ladit balíček NuGet.
>
> Upozornění je, že uživatelé mohou potřebovat najít a nakonfigurovat server symbolů NuGet v jejich IDE (jako jednorázové nastavení) získat soubory symbolů. Visual Studio 2019 verze 16.1 přidalo symbolový server NuGet.org do seznamu výchozích serverů symbolů.

>[!div class="step-by-step"]
>[Předchozí](strong-naming.md)
>[další](dependencies.md)
