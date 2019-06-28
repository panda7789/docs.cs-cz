---
title: DotNet – přidat odkaz na – příkaz
description: Příkaz dotnet add příkaz odkaz poskytuje vhodnou možnost pro přidání odkazů typu projekt na projekt.
ms.date: 06/26/2019
ms.openlocfilehash: 6e0ca40e701b62dcc18147f9de83cafa6aa2f50f
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422008"
---
# <a name="dotnet-add-reference"></a>DotNet – přidat odkaz

**Tento článek se týká: ✓** .NET Core 1.x sady SDK a novějších verzích

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet add reference` -Přidá odkazy typu projekt projekt (P2P).

## <a name="synopsis"></a>Souhrn

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Popis

`dotnet add reference` Příkaz poskytuje vhodnou možnost přidat odkazy na projekt do projektu. Po spuštění příkazu [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) prvky jsou přidány do souboru projektu.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Určuje soubor projektu. Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.

* **`PROJECT_REFERENCES`**

  Chcete-li přidat odkazuje na projekt na projekt (P2P). Zadejte jeden nebo více projektů. [Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systémech založené na systému Unix/Linux.

## <a name="options"></a>Možnosti

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`-f|--framework <FRAMEWORK>`**

  Přidá odkazy na projekt jenom při cílení na konkrétní [framework](../../standard/frameworks.md).

* **`--interactive`**

  Povoluje příkazu zastavit a počkat na vstup uživatele nebo akci (třeba k dokončení ověřování). Tato možnost je k dispozici, protože .NET Core 3.0 SDK.

## <a name="examples"></a>Příklady

* Přidáte odkaz na projekt:

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* Přidání více odkazů projektu na projekt v aktuálním adresáři:

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* Přidání více odkazů projektu pomocí vzoru podpory zástupných znaků v systému Linux/Unix:

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
