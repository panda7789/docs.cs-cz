---
title: příkaz DotNet sln
description: Příkaz dotnet sln poskytuje vhodnou možnost pro přidání, odebrání a výpis projektů v souboru řešení.
ms.date: 06/13/2018
ms.openlocfilehash: a88e22c68f639f2a42e59f9a271e431f04e24a2b
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169141"
---
# <a name="dotnet-sln"></a>DotNet Run

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet sln` -Upraví soubor řešení .NET Core.

## <a name="synopsis"></a>Souhrn

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Popis

`dotnet sln` Příkaz poskytuje pohodlný způsob, jak přidat, odebrat a zobrazení seznamu projektů v souboru řešení.

Použít `dotnet sln` příkazu soubor řešení již musí existovat. Pokud je potřeba ho vytvořit, použijte [dotnet nové](dotnet-new.md) příkazu, stejně jako v následujícím příkladu:

```
dotnet new sln
```

## <a name="commands"></a>Příkazy

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Přidá projekt nebo více projektů do souboru řešení. [Vzorů podpory zástupných znaků](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux na základě terminály.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Odebere projekt nebo více projektů ze souboru řešení. [Vzorů podpory zástupných znaků](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux na základě terminály.

`list`

Vypíše všechny projekty v souboru řešení.

## <a name="arguments"></a>Arguments

`SOLUTION_NAME`

Soubor řešení se má použít. Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden. Pokud v adresáři existuje více souborů řešení, musí zadat jeden.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

## <a name="examples"></a>Příklady

Přidáte do řešení projektu v jazyce C#:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Odeberte z řešení projektu v jazyce C#:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Přidání více projekty jazyka C# do řešení:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Odeberte z řešení více projekty jazyka C#:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Přidání více projekty jazyka C# do řešení pomocí podpory zástupných znaků vzoru:

`dotnet sln todo.sln add **/*.csproj`

Odeberte z řešení, které využívá model podpory zástupných znaků více projekty jazyka C#:

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> Podpory zástupných znaků není funkce rozhraní příkazového řádku, ale místo toho funkci z příkazového řádku. Chcete-li úspěšně rozbalit soubory, je nutné použít prostředí, které podporuje podpory zástupných znaků. Další informace o podpory zástupných znaků naleznete v tématu [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).
