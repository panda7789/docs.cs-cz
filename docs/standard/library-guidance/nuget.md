---
title: Knihovny NuGet a .NET
description: Doporučení osvědčených postupů pro balení s NuGet pro knihovny .NET
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 9cf30fa41af2d31e416bae1d75d8880ece7dde3e
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895208"
---
# <a name="nuget"></a>NuGet

NuGet je správce balíčků pro ekosystém .NET a je primárním způsobem, jak vývojáři zjišťují a získávají knihovny .NET open source. [NuGet.org](https://www.nuget.org/)je bezplatná služba poskytovaná Microsoftem pro hostování balíčků NuGet, je primárním hostitelem pro veřejné balíčky NuGet, ale můžete publikovat ve vlastních službách NuGet, jako je [MyGet](https://www.myget.org/) a [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>Vytvoření balíčku NuGet

Balíček NuGet (`*.nupkg`) je soubor zip, který obsahuje sestavení .NET a přidružená metadata.

Existují dva hlavní způsoby, jak vytvořit balíček NuGet. Novější a doporučený způsob je vytvořit balíček z projektu ve stylu sady SDK (soubor projektu, `<Project Sdk="Microsoft.NET.Sdk">`jehož obsah začíná). Sestavení a cíle jsou automaticky přidány do balíčku a zbývající metadata jsou přidána do souboru MSBuild, jako je název balíčku a číslo verze. Kompilace pomocí [`dotnet pack`](../../core/tools/dotnet-pack.md) příkazu provede `*.nupkg` výstup souboru místo sestavení.

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

Starší způsob vytváření balíčku NuGet je `*.nuspec` soubor `nuget.exe` a nástroj příkazového řádku. Soubor nuspec vám dává Skvělé řízení, ale musíte pečlivě určit, jaká sestavení a cíle se mají zahrnout do finálního balíčku NuGet. Je snadné vytvořit chybu nebo někoho, aby se při provádění změn aktualizoval nuspec. Výhodou nuspec je, že můžete použít vytvoření balíčků NuGet pro architektury, které ještě nepodporují soubor projektu ve stylu sady SDK.

**✔️ zvažte** použití souboru projektu ve stylu sady SDK k vytvoření balíčku NuGet.

## <a name="package-dependencies"></a>Závislosti balíčků

Závislosti balíčků NuGet jsou podrobně popsané v článku [závislosti](./dependencies.md) .

## <a name="important-nuget-package-metadata"></a>Důležitá metadata balíčku NuGet

Balíček NuGet podporuje mnoho [vlastností metadat](/nuget/reference/nuspec). Následující tabulka obsahuje základní metadata, která by měl každý balíček v NuGet.org poskytnout:

| Název vlastnosti MSBuild              | Název nuspec              | Popis  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | Identifikátor balíčku. Předpona z identifikátoru může být vyhrazena, pokud splňuje [kritéria](/nuget/reference/id-prefix-reservation). |
| `PackageVersion`                   | `version`                  | Verze balíčku NuGet Další informace najdete v tématu [verze balíčku NuGet](./versioning.md#nuget-package-version).             |
| `Title`                            | `title`                    | Popisný název balíčku. Výchozí hodnota `PackageId`je.             |
| `Description`                      | `description`              | Dlouhý popis balíčku zobrazeného v uživatelském rozhraní.             |
| `Authors`                          | `authors`                  | Čárkami oddělený seznam autorů balíčků, které odpovídají názvům profilů v nuget.org.             |
| `PackageTags`                      | `tags`                     | Mezerou oddělený seznam značek a klíčových slov, které popisují balíček. Značky se používají při hledání balíčků.             |
| `PackageIconUrl`                   | `iconUrl`                  | Adresa URL obrázku, který má být použit jako ikona balíčku. Adresa URL by měla být HTTPS a Image by měla být 64 × 64 a měla by mít transparentní pozadí.             |
| `PackageProjectUrl`                | `projectUrl`               | Adresa URL domovské stránky projektu nebo zdrojového úložiště.             |
| `PackageLicenseExpression`         | `license`                  | [Identifikátor SPDX](https://spdx.org/licenses/)licence projektu. Identifikátor můžou používat jenom licence OSI a FSF schválené. Ostatní licence by se `PackageLicenseFile`měly používat. Přečtěte si další informace o [ `license` metadatech](/nuget/reference/nuspec#license). |

> [!IMPORTANT]
> Projekt bez licence se standardně [vylučuje na výhradní Copyright](https://choosealicense.com/no-permission/), což umožňuje, aby ho jiní uživatelé mohli používat.

**✔️ zvažte** možnost zvolit název balíčku NuGet s předponou, která splňuje [kritéria](/nuget/reference/id-prefix-reservation)rezervace předpon NuGet.

**✔️** použijte odkaz HTTPS href na ikonu balíčku.

> Weby, jako je NuGet.org spuštěná s povoleným protokolem HTTPS a zobrazením image bez HTTPS, vytvoří upozornění na smíšený obsah.

**✔️** použít obrázek ikony balíčku, který je 64 × 64 a má transparentní pozadí pro nejlepší výsledky zobrazení.

**✔️ zvažte** nastavení [zdrojového odkazu](./sourcelink.md) pro přidání metadat správy zdrojů do sestavení a balíčku NuGet.

> Odkaz na zdroj automaticky `RepositoryUrl` přidá `RepositoryType` a metadata do balíčku NuGet. Odkaz na zdroj také přidá informace o přesném zdrojovém kódu, ze kterého byl balíček sestaven. Například balíček vytvořený z úložiště Git bude obsahovat hodnotu hash potvrzení přidané jako metadata.

## <a name="pre-release-packages"></a>Předběžné verze balíčků

Balíčky NuGet s příponou verze se považují za [předběžné verze](/nuget/create-packages/prerelease-packages). Ve výchozím nastavení uživatelské rozhraní Správce balíčků NuGet zobrazuje stabilní verze, pokud se uživatel výslovný k předběžným balíčkům, takže předběžné verze balíčků jsou ideální pro omezené testování uživatelů.

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> Stabilní balíček nemůže záviset na předběžné verzi balíčku. Musíte buď udělat předběžnou verzi balíčku, nebo závisí na starší verzi stabilní verze.

![Závislost předběžné verze balíčku NuGet](./media/nuget/nuget-prerelease-package.png "Závislost předběžné verze balíčku NuGet")

**✔️** publikovat předběžnou verzi balíčku při testování, náhledu nebo experimentování.

**✔️** po jeho přípravě publikovat stabilní balíček, aby na něj mohli odkazovat další stabilní balíčky.

## <a name="symbol-packages"></a>Balíčky symbolů

Soubory symbolů (`*.pdb`) jsou vytvářeny kompilátorem rozhraní .NET spolu se sestaveními. Soubory symbolů mapují umístění spuštění na původní zdrojový kód, takže můžete procházet zdrojový kód tak, jak je spuštěn pomocí ladicího programu. NuGet podporuje [vygenerování samostatného balíčku symbolů`*.snupkg`()](/nuget/create-packages/symbol-packages-snupkg) , který obsahuje soubory symbolů společně s hlavním balíčkem obsahujícím sestavení .NET. Nápad balíčků symbolů je hostovaný na serveru symbolů a stahuje se jenom nástrojem, jako je Visual Studio na vyžádání.

NuGet.org hostuje své vlastní [úložiště symbolů serveru](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server). Vývojáři mohou používat symboly publikované na serveru symbolů NuGet.org přidáním `https://symbols.nuget.org/download/symbols` do jejich [zdrojů symbolů v aplikaci Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).

> [!IMPORTANT]
> Server symbolů NuGet.org podporuje pouze nové [přenositelné soubory symbolů](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) vytvořené projekty stylu sady SDK.
>
> Chcete-li použít server symbolů NuGet.org při ladění knihovny .NET, musí mít vývojáři Visual Studio 2017 15,9 nebo novější.

Alternativou k vytvoření balíčku symbolů je vkládání souborů symbolů do hlavního balíčku NuGet. Hlavní balíček NuGet bude větší, ale vložené soubory symbolů znamená, že vývojáři nepotřebují konfigurovat server symbolů NuGet.org. Pokud vytváříte balíček NuGet pomocí projektu ve stylu sady SDK, můžete vložit soubory symbolů nastavením `AllowedOutputExtensionsInPackageBuildOutputFolder` vlastnosti:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

Nevýhodou soubory symbolů vkládání je to, že zvyšují velikost balíčku o přibližně 30% pro knihovny .NET zkompilované pomocí projektů ve stylu sady SDK. Pokud je velikost balíčku obavou, místo toho byste měli publikovat symboly v balíčku symbolů.

**✔️ zvažte** publikování symbolů jako balíčku symbolů (`*.snupkg`) do NuGet.org

> Balíčky symbolů (`*.snupkg`) poskytují vývojářům kvalitní možnosti ladění na vyžádání, aniž by bloating hlavní velikost balíčku a ovlivnily výkon obnovení pro uživatele, kteří nemají v úmyslu ladit balíček NuGet.
>
> Upozornění je, že uživatelé mohou potřebovat vyhledat a nakonfigurovat server symbolů NuGet v integrovaném vývojovém prostředí (jako jednorázovou instalaci) a získat tak soubory symbolů. Visual Studio 2019 verze 16,1 přidala server symbolů NuGet. org do seznamu výchozích symbolových serverů.

>[!div class="step-by-step"]
>[Předchozí](strong-naming.md)Další
>[](dependencies.md)
