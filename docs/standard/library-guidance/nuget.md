---
title: Knihovny a rozhraní .NET NuGet
description: Doporučené osvědčené postupy pro vytváření balíčků nuget pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 845af3b34827e1f284bb52e040f9de09f22baf37
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087867"
---
# <a name="nuget"></a>NuGet

NuGet je Správce balíčků pro .NET ekosystému a vývojáři hlavní způsob, jak vyhledat a získat open source knihoven .NET. Primární hostitele pro veřejné balíčky NuGet je NuGet.org, bezplatná služba poskytovaného společností Microsoft pro hostování balíčků NuGet, ale můžete publikovat do vlastní služby NuGet jako MyGet a Azure DevOps.

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>Vytvoří balíček NuGet

Balíček NuGet (`*.nupkg`) je soubor zip, který obsahuje sestavení .NET a přidružená metadata.

Existují dva hlavní způsoby, jak vytvořit balíček NuGet. Novější a doporučený způsob je pro vytvoření balíčku sady SDK – vizuální styl projektu (soubor projektu obsah začíná `<Project Sdk="Microsoft.NET.Sdk">`). Sestavení a cíle jsou automaticky přidány do balíčku a zbývající metadat se přidá do souboru MSBuild, jako je číslo název a verzi balíčku. Kompilace s [ `dotnet pack` ](../../core/tools/dotnet-pack.md) příkaz výstupy `*.nupkg` souboru místo sestavení.

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

**✔️ ZVAŽTE** nastavení SourceLink přidat metadata ovládací prvek zdroje k sestavení a balíček NuGet.

## <a name="package-dependencies"></a>Závislosti balíčků

Závislosti balíčků NuGet je podrobně popsána v [závislosti](./dependencies.md) článku.

## <a name="important-nuget-package-metadata"></a>Důležitá metadata balíčku NuGet

Balíček NuGet podporuje mnoho [vlastnosti metadat](/nuget/reference/nuspec). Následující tabulka obsahuje základní metadata, která by měla poskytnout každý projekt open source:

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
| `PackageLicenseUrl`                | `licenseUrl`               | Adresa URL licence projektu. Může být adresa URL `LICENSE` soubor ve správě zdrojového kódu.             |

**✔️ ZVAŽTE** zvolíte název balíčku NuGet s předponou, který splňuje rezervace předpony Nugetu [kritéria](/nuget/reference/id-prefix-reservation).

**✔️ ZVAŽTE** pomocí `LICENSE` soubor ve správě zdrojového kódu, jako `LicenseUrl`. Třeba https://github.com/JamesNK/Newtonsoft.Json/blob/master/LICENSE.md.

> [!IMPORTANT]
> Projekt bez licence výchozí hodnota je [exkluzivní copyright](https://choosealicense.com/no-permission/), může znemožnit ostatním uživatelům.

**PROVEĎTE ✔️** použít href HTTPS na ikonu vašeho balíčku.

> NuGet.org, jako jsou spuštění pomocí protokolu HTTPS povolené a zobrazování obrázků bez HTTPS vytvoří smíšený obsah upozornění.

**PROVEĎTE ✔️** použít bitovou kopii balíčku ikonu, která je 64 x 64 a má průhledné pozadí nejlepšího zobrazení výsledků.

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

Podporuje NuGet [generování balíčku samostatný symbol](/nuget/create-packages/symbol-packages) obsahující ladit soubory PDB souběžně s hlavní balíček, který obsahuje sestavení .NET. Představu o balíčky symbolů je už hostovaný na serveru symbolů a stáhnou jenom nástroje, jako je Visual Studio na vyžádání.

Aktuálně hlavní veřejný hostitel pro symboly – [SymbolSource](http://www.symbolsource.org/) -nepodporuje souborům portable PDB vytvořené pomocí sady SDK – vizuální styl není užitečné projekty a balíčky symbolů.

**✔️ ZVAŽTE** vkládání PDB do hlavního balíčku NuGet.

**❌ Nepoužívejte** vytváří se balíček symbolů, který obsahuje soubory PDB.

>[!div class="step-by-step"]
[Předchozí](./strong-naming.md)
[další](./dependencies.md)
