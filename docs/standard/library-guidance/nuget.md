---
title: Knihovny a rozhraní .NET NuGet
description: Doporučené osvědčené postupy pro vytváření balíčků nuget pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: a721c642dd92eb299eef3b62fc845afa99f81ddc
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204610"
---
# <a name="nuget"></a>NuGet

NuGet je Správce balíčků pro .NET ekosystému a vývojáři hlavní způsob, jak vyhledat a získat open source knihoven .NET. [NuGet.org](https://www.nuget.org/), je bezplatná služba poskytovaného společností Microsoft pro balíčky NuGet hostují primární hostitele pro veřejné balíčky NuGet, ale můžete publikovat vlastní služeb NuGet, třeba [MyGet](https://www.myget.org/) a [artefakty Azure ](https://azure.microsoft.com/services/devops/artifacts/).

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>Vytvoří balíček NuGet

Balíček NuGet (`*.nupkg`) je soubor zip, který obsahuje sestavení .NET a přidružená metadata.

Existují dva hlavní způsoby, jak vytvořit balíček NuGet. Novější a doporučený způsob je pro vytvoření balíčku sady SDK – vizuální styl projektu (soubor projektu, jehož obsah začíná `<Project Sdk="Microsoft.NET.Sdk">`). Sestavení a cíle jsou automaticky přidány do balíčku a zbývající metadat se přidá do souboru MSBuild, jako je číslo název a verzi balíčku. Kompilace s [ `dotnet pack` ](../../core/tools/dotnet-pack.md) příkaz výstupy `*.nupkg` souboru místo sestavení.

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

Starší způsob vytváření balíčku NuGet se `*.nuspec` souboru a `nuget.exe` nástroj příkazového řádku. Soubor nuspec získáte skvělou kontrolu, ale musí pečlivě určit, jaké sestavení a cíle, které mají být zahrnuty do koncového balíčku NuGet. Je snadné vytvořit chybu nebo pro uživatele nezapomeňte aktualizovat soubor nuspec při provádění změn. Výhodou rámci souboru nuspec je můžete vytvořit balíčky NuGet pro rozhraní, které se zatím nepodporují souboru SDK – vizuální styl projektu.

**✔️ ZVAŽTE** pomocí souboru SDK – vizuální styl projektu k vytvoření balíčku NuGet.

## <a name="package-dependencies"></a>Závislosti balíčků

Závislosti balíčků NuGet je podrobně popsána v [závislosti](./dependencies.md) článku.

## <a name="important-nuget-package-metadata"></a>Důležitá metadata balíčku NuGet

Balíček NuGet podporuje mnoho [vlastnosti metadat](/nuget/reference/nuspec). Následující tabulka obsahuje základní metadata, která by měla poskytnout všech balíčků na NuGet.org:

| Název vlastnosti nástroje MSBuild              | Název souboru Nuspec              | Popis  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | Identifikátor balíčku. Je možné vyhradit předpony z identifikátoru, pokud splňuje [kritéria](/nuget/reference/id-prefix-reservation). |
| `PackageVersion`                   | `version`                  | Verze balíčku NuGet. Další informace najdete v tématu [verze balíčku NuGet](./versioning.md#nuget-package-version).             |
| `Title`                            | `title`                    | Lidské popisný název balíčku. Výchozí hodnota `PackageId`.             |
| `Description`                      | `description`              | Dlouhý popis balíčku zobrazeného v uživatelském rozhraní.             |
| `Authors`                          | `authors`                  | Čárkou oddělený seznam autorů balíčků, odpovídající názvy profilů na nuget.org.             |
| `PackageTags`                      | `tags`                     | Mezerami oddělený seznam značek a klíčových slov, které popisují balíček. Značky se používají při vyhledávání balíčků.             |
| `PackageIconUrl`                   | `iconUrl`                  | Adresa URL obrázku má použít jako ikona pro balíček. Adresa URL by měla být HTTPS a bitové kopie by měl být 64 x 64 a průhledné pozadí.             |
| `PackageProjectUrl`                | `projectUrl`               | Adresa URL pro projekt domovskou stránku a zdrojového úložiště.             |
| `PackageLicenseExpression`         | `license`                  | Licence projektu [SPDX identifikátor](https://spdx.org/licenses/). Pouze OSI a FSF schválené licencí můžete použít identifikátor. Licence na ostatní používejte `PackageLicenseFile`. Další informace o [ `license` metadat](/nuget/reference/nuspec#license). |

> [!IMPORTANT]
> Projekt bez licence výchozí hodnota je [exkluzivní copyright](https://choosealicense.com/no-permission/), může znemožnit právně pro používání jiným lidem.

**✔️ ZVAŽTE** zvolíte název balíčku NuGet s předponou, který splňuje rezervace předpony Nugetu [kritéria](/nuget/reference/id-prefix-reservation).

**PROVEĎTE ✔️** použít href HTTPS na ikonu vašeho balíčku.

> NuGet.org, jako jsou spuštění pomocí protokolu HTTPS povolené a zobrazování obrázků bez HTTPS vytvoří smíšený obsah upozornění.

**PROVEĎTE ✔️** použít bitovou kopii balíčku ikonu, která je 64 x 64 a má průhledné pozadí nejlepšího zobrazení výsledků.

**✔️ ZVAŽTE** nastavení [odkazu na zdroj](./sourcelink.md) přidat metadata ovládací prvek zdroje k sestavení a balíček NuGet.

> Zdrojový odkaz automaticky přidá `RepositoryUrl` a `RepositoryType` metadata balíčku NuGet. Odkaz na zdroj přidá také informace o kódu konkrétním použitém zdroji balíčku byla vytvořena z. Hodnota hash zápisu přidán jako metadata bude mít například balíček vytvořen z úložiště Git.

## <a name="pre-release-packages"></a>Balíčky v předběžné verzi

Balíčky NuGet s příponou verze jsou považovány za [předběžné verze](/nuget/create-packages/prerelease-packages). Ve výchozím nastavení uživatelského rozhraní Správce balíčků NuGet zobrazuje stabilní verze, pokud uživatel požádá o výslovný souhlas a předběžné verze balíčků, díky tomu balíčky v předběžné verzi ideální pro testování uživatel s omezenými oprávněními.

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> Stabilní balíček nemohou záviset na předběžnou verzi balíčku. Musíte vytvořit vlastní balíček předběžné verze nebo závisí na starší stabilní verzi.

![Závislost předběžné verze balíčku NuGet](./media/nuget/nuget-prerelease-package.png "závislost předběžné verze balíčku NuGet")

**PROVEĎTE ✔️** publikovat předběžné verze balíčků při testování, náhled nebo experimentování.

**PROVEĎTE ✔️** publikovat stabilní balíček, když je připraven tak další stabilní balíčky na něj mohli odkazovat.

## <a name="symbol-packages"></a>Balíčky symbolů

Soubory symbolů (`*.pdb`) jsou produkované kompilátorem .NET spolu s sestavení. Umístění se symboly mapy provádění soubory do původního zdrojového kódu, můžete procházet zdrojový kód, protože je spuštěn pomocí ladicího programu. Podporuje NuGet [generování balíčku samostatný symbol (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) obsahující soubory symbolů souběžně s hlavní balíček, který obsahuje sestavení .NET. Představu o balíčky symbolů je už hostovaný na serveru symbolů a stáhnou jenom nástroje, jako je Visual Studio na vyžádání.

NuGet.org hostuje vlastní [úložiště serveru symbolů](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server). Vývojáři mohou použít symboly publikované na NuGet.org symbol server tak, že přidáte `https://symbols.nuget.org/download/symbols` k jejich [symbol zdroje v sadě Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).

> [!IMPORTANT]
> Server symbolů NuGet.org podporuje pouze nové [soubory portable symbolů](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) vytvořené projekty založenými na sadě SDK.
>
> Použít NuGet.org serveru symbolů při ladění knihovny .NET, vývojáři musíte mít Visual Studio 2017 15.9 nebo vyšší.

Alternativa k vytvoření balíčku symbolů je vložení soubory symbolů do hlavního balíčku NuGet. Hlavní balíček NuGet bude větší, ale symbol vložené soubory znamená, že vývojáři nevyžaduje konfiguraci serveru symbolů NuGet.org. Pokud vytváříte balíček NuGet pomocí sady SDK styl projektu a pak můžete vložit soubory symbolů tak, že nastavíte `AllowedOutputExtensionsInPackageBuildOutputFolder` vlastnost:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

Nevýhodou vnoření soubory symbolů se zvyšují velikost balíčku o 30 % knihovnám .NET kompilováno s použitím projekty založenými na sadě SDK. Pokud velikost balíčku je problém, jste měli publikovat symboly místo toho v balíčku symbolů.

**✔️ ZVAŽTE** publikování symbolů jako balíček symbolů (`*.snupkg`) na NuGet.org

> Balíčky symbolů (`*.snupkg`) vývojářům poskytuje dobré ladicího prostředí na vyžádání bez nadměrnému nárůstu velikosti velikost hlavního balíčku a dopadu na zvyšuje výkon pro ty, kteří nechcete ladit balíček NuGet.
>
> Výstrahou je, že by potřebují najít a nakonfigurujte server symbolů NuGet v jejich prostředí IDE (jako jednorázová nastavení) Chcete-li získat soubory symbolů. Visual Studio 2019 plánuje zadejte server symbolů NuGet.org jako jednu z možností úprav. 


>[!div class="step-by-step"]
>[Předchozí](strong-naming.md)
>[další](dependencies.md)
