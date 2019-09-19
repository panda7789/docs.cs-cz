---
title: dotnet sln – příkaz
description: Příkaz dotnet-sln nabízí pohodlný způsob přidávání, odebírání a vypsání projektů v souboru řešení.
ms.date: 06/13/2018
ms.openlocfilehash: 84508aaefff61b31e2965576ebc2daaae7331951
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117583"
---
# <a name="dotnet-sln"></a>dotnet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet sln`– Upraví soubor řešení .NET Core.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Popis

`dotnet sln` Příkaz nabízí pohodlný způsob, jak přidávat, odebírat a vypisovat projekty v souboru řešení.

Chcete-li `dotnet sln` použít příkaz, soubor řešení již musí existovat. Pokud ho potřebujete vytvořit, použijte příkaz [dotnet New](dotnet-new.md) , jako v následujícím příkladu:

```dotnetcli
dotnet new sln
```

## <a name="commands"></a>Příkazy

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Přidá do souboru řešení projekt nebo více projektů. [Vzory expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) se podporují v terminálech založených na systému UNIX/Linux.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Odebere projekt nebo více projektů ze souboru řešení. [Vzory expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) se podporují v terminálech založených na systému UNIX/Linux.

`list`

Zobrazí seznam všech projektů v souboru řešení.

## <a name="arguments"></a>Arguments

`SOLUTION_NAME`

Soubor řešení, který se má použít Pokud není zadán, příkaz vyhledá v aktuálním adresáři. Pokud je v adresáři více souborů řešení, je nutné zadat jeden.

## <a name="options"></a>Možnosti

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

## <a name="examples"></a>Příklady

Přidání C# projektu do řešení:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Odebrání C# projektu z řešení:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Přidání více C# projektů do řešení:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Odebrání více C# projektů z řešení:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Přidání více C# projektů do řešení pomocí vzorového expanze názvů:

`dotnet sln todo.sln add **/*.csproj`

Odebrání více C# projektů z řešení pomocí vzoru expanze názvů:

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> Expanze názvů není funkcí CLI, ale spíše funkcí příkazového prostředí. Aby bylo možné soubory úspěšně rozšířit, je nutné použít prostředí, které podporuje expanze názvů. Další informace o expanzi názvů naleznete v tématu [Wikipedii](https://en.wikipedia.org/wiki/Glob_(programming)).
