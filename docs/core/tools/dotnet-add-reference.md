---
title: dotnet přidat odkaz, příkaz
description: Dotnet add reference příkaz poskytuje vhodnou možnost přidat projekt do odkazů projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 84ea25e94efc8d84aebfeccf62c30a64551c5019
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503797"
---
# <a name="dotnet-add-reference"></a>dotnet add reference

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name (Název)

`dotnet add reference`- Přidá odkazy projekt-projekt (P2P).

## <a name="synopsis"></a>Synopse

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

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

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`-f|--framework <FRAMEWORK>`**

  Přidá odkazy na projekt pouze v případě, že cílí na konkrétní [rámec](../../standard/frameworks.md).

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
