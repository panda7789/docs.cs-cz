---
title: DotNet – přidat odkaz na – příkaz
description: Příkaz dotnet add příkaz odkaz poskytuje vhodnou možnost pro přidání odkazů typu projekt na projekt.
ms.date: 04/24/2019
ms.openlocfilehash: f33a379534dca88133babbb5ca78bca614e441c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755190"
---
# <a name="dotnet-add-reference"></a>DotNet – přidat odkaz

**Tento článek se týká: ✓** .NET Core 1.x sady SDK a novějších verzích

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet add reference` -Přidá odkazy typu projekt projekt (P2P).

## <a name="synopsis"></a>Souhrn

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

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