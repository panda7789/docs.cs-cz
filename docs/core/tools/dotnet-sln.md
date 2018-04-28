---
title: příkaz SLN – DotNet - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet sln poskytuje vhodnou možnost přidávat, odstraňovat a seznam projekty v řešení souboru.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 837d47c38119f9a7aa75c74576ed75b8ef3813dd
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-sln"></a>SLN – DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet sln` -Upravuje soubor řešení .NET Core.

## <a name="synopsis"></a>Stručný obsah

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Popis

`dotnet sln` Příkaz nabízí pohodlný způsob, jak přidat, odebrat a seznam projekty v řešení souboru.

## <a name="commands"></a>Příkazy

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Přidá do řešení souboru projektu nebo více projektů. [Vzory expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux, na základě terminály.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Odebere projektu nebo více projektů ze souboru řešení. [Vzory expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux, na základě terminály.

`list`

Zobrazí všechny projekty v řešení souboru.

## <a name="arguments"></a>Arguments

`SOLUTION_NAME`

Soubor řešení se má použít. Pokud není zadaný, hledá příkaz aktuální adresář pro jednu. Pokud se nachází několik souborů řešení v adresáři, jeden musí být zadán.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

## <a name="examples"></a>Příklady

Přidejte projekt C# do řešení:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Odebrání řešení projekt C#:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Přidání více projektů C# do řešení:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Odebrání řešení více projektů C#:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Přidání více projektů C# do řešení pomocí vzoru expanze názvů:

`dotnet sln todo.sln add **/*.csproj`

Odebrání řešení pomocí vzoru expanze názvů více projektů C#:

`dotnet sln todo.sln remove **/*.csproj`
