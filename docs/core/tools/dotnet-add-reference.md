---
title: dotnet přidat odkaz, příkaz
description: Dotnet add reference příkaz poskytuje vhodnou možnost přidat projekt do odkazů projektu.
ms.date: 02/14/2020
ms.openlocfilehash: f2bd67d181784c4858b8971d05053d196df7818e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463737"
---
# <a name="dotnet-add-reference"></a>dotnet add reference

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Název

`dotnet add reference`- Přidá odkazy projekt-projekt (P2P).

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet add [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     [--interactive] <PROJECT_REFERENCES>

dotnet add reference -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet add reference` poskytuje vhodnou možnost přidání odkazů na projekt do projektu. Po spuštění příkazu `<ProjectReference>` jsou prvky přidány do souboru projektu.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Argumenty

- **`PROJECT`**

  Určuje soubor projektu. Pokud není zadán, příkaz prohledá aktuální adresář pro jeden.

- **`PROJECT_REFERENCES`**

  Odkazy projektu na projekt (P2P), které chcete přidat. Zadejte jeden nebo více projektů. Glob vzory jsou [podporovány](https://en.wikipedia.org/wiki/Glob_(programming)) na Unix / Linux-založené systémy.

## <a name="options"></a>Možnosti

- **`-f|--framework <FRAMEWORK>`**

  Přidá odkazy na projekt pouze v případě, že cílí na konkrétní [rámec](../../standard/frameworks.md).

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--interactive`**

  Umožňuje příkazu zastavit a čekat na vstup nebo akci uživatele (například k dokončení ověřování). K dispozici od .NET Core 3.0 SDK.

## <a name="examples"></a>Příklady

- Přidejte odkaz na projekt:

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- Přidejte do projektu více odkazů na projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Přidejte více odkazů na projekt pomocí globbingového vzoru na Linuxu/Unixu:

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
