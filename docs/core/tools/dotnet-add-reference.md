---
title: DotNet – přidat odkaz na příkaz - .NET Core rozhraní příkazového řádku
description: Dotnet přidat odkaz na příkaz poskytuje vhodnou možnost přidat odkazy na projekt na projekt.
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: c82696eee2fbe4bbad86e59cf5de1c2e74d048f6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-add-reference"></a>DotNet – přidání odkazu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet add reference` -Přidá odkazy na projekt na projekt (P2P).

## <a name="synopsis"></a>Stručný obsah

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Popis

`dotnet add reference` Příkaz poskytuje vhodnou možnost přidat odkazy na projekt na projekt. Po spuštění příkazu [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) prvky jsou přidány do souboru projektu.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

`PROJECT`

Určuje soubor projektu. Pokud není zadaný, hledá příkaz aktuální adresář pro jednu.

`PROJECT_REFERENCES`

Chcete-li přidat odkazuje na projekt na projekt (P2P). Zadejte jeden nebo více projektů. [Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systémech UNIX/Linux.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-f|--framework <FRAMEWORK>`

Přidá odkazy na projekt jenom při cílení na konkrétní [framework](../../standard/frameworks.md).

## <a name="examples"></a>Příklady

Přidáte odkaz na projekt:

`dotnet add app/app.csproj reference lib/lib.csproj`

Přidání více odkazy na projekt na projekt v aktuálním adresáři:

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

Přidání více odkazů projektu pomocí vzoru expanze názvů v systému Linux nebo Unix:

`dotnet add app/app.csproj reference **/*.csproj`
