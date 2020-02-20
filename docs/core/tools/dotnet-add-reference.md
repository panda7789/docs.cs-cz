---
title: dotnet – příkaz Add Reference
description: Příkaz dotnet Add Reference poskytuje pohodlný způsob, jak přidat projekt do odkazů projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 84ea25e94efc8d84aebfeccf62c30a64551c5019
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503797"
---
# <a name="dotnet-add-reference"></a>dotnet add reference

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Název

`dotnet add reference` – přidá odkazy z projektu na projekt (P2P).

## <a name="synopsis"></a>Stručný obsah

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Popis

Příkaz `dotnet add reference` poskytuje pohodlný způsob, jak přidat odkazy na projekt do projektu. Po spuštění příkazu se prvky `<ProjectReference>` přidají do souboru projektu.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Argumenty

- **`PROJECT`**

  Určuje soubor projektu. Pokud není zadán, příkaz vyhledá v aktuálním adresáři.

- **`PROJECT_REFERENCES`**

  Odkazy na projekt (P2P), které se mají přidat. Zadejte jeden nebo více projektů. [Glob vzory](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systémech UNIX/Linux.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`-f|--framework <FRAMEWORK>`**

  Přidá odkazy projektu pouze v případě cílení na konkrétní [rozhraní](../../standard/frameworks.md).

- **`--interactive`**

  Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování). K dispozici od verze .NET Core 3,0 SDK.

## <a name="examples"></a>Příklady

- Přidat odkaz na projekt:

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- Přidat do projektu více odkazů na projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Přidání více odkazů na projekt pomocí vzoru expanze názvů na platformě Linux/UNIX:

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
