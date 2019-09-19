---
title: dotnet – příkaz Add Reference
description: Příkaz dotnet Add Reference poskytuje pohodlný způsob, jak přidat projekt do odkazů projektu.
ms.date: 06/26/2019
ms.openlocfilehash: 06d10f6903251bc9d29ae856a900a20610565a14
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117786"
---
# <a name="dotnet-add-reference"></a>dotnet – přidat odkaz

**Tento článek se týká: ✓** .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet add reference`– Přidá odkazy na projekt na projekt (P2P).

## <a name="synopsis"></a>Stručný obsah

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Popis

`dotnet add reference` Příkaz nabízí pohodlný možnost Přidat odkazy na projekt do projektu. Po spuštění příkazu `<ProjectReference>` se prvky přidají do souboru projektu.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Určuje soubor projektu. Pokud není zadán, příkaz vyhledá v aktuálním adresáři.

* **`PROJECT_REFERENCES`**

  Odkazy na projekt (P2P), které se mají přidat. Zadejte jeden nebo více projektů. [Glob vzory](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systémech UNIX/Linux.

## <a name="options"></a>Možnosti

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

* **`-f|--framework <FRAMEWORK>`**

  Přidá odkazy projektu pouze v případě cílení na konkrétní [rozhraní](../../standard/frameworks.md).

* **`--interactive`**

  Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování). K dispozici od verze .NET Core 3,0 SDK.

## <a name="examples"></a>Příklady

* Přidat odkaz na projekt:

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* Přidat do projektu více odkazů na projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* Přidání více odkazů na projekt pomocí vzoru expanze názvů na platformě Linux/UNIX:

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
