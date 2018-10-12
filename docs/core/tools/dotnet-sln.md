---
title: příkaz DotNet sln – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet sln poskytuje vhodnou možnost pro přidání, odebrání a výpis projektů v souboru řešení.
author: mairaw
ms.author: mairaw
ms.date: 06/13/2018
ms.openlocfilehash: 2651e8e14ad43f41354b8165179f95f65e732f4c
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121217"
---
# <a name="dotnet-sln"></a><span data-ttu-id="48fd3-103">DotNet Run</span><span class="sxs-lookup"><span data-stu-id="48fd3-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="48fd3-104">Název</span><span class="sxs-lookup"><span data-stu-id="48fd3-104">Name</span></span>

<span data-ttu-id="48fd3-105">`dotnet sln` -Upraví soubor řešení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="48fd3-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="48fd3-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="48fd3-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="48fd3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="48fd3-107">Description</span></span>

<span data-ttu-id="48fd3-108">`dotnet sln` Příkaz poskytuje pohodlný způsob, jak přidat, odebrat a zobrazení seznamu projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="48fd3-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="48fd3-109">Použít `dotnet sln` příkazu soubor řešení již musí existovat.</span><span class="sxs-lookup"><span data-stu-id="48fd3-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="48fd3-110">Pokud je potřeba ho vytvořit, použijte [dotnet nové](dotnet-new.md) příkazu, stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="48fd3-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="48fd3-111">Příkazy</span><span class="sxs-lookup"><span data-stu-id="48fd3-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="48fd3-112">Přidá projekt nebo více projektů do souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="48fd3-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="48fd3-113">[Vzorů podpory zástupných znaků](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux na základě terminály.</span><span class="sxs-lookup"><span data-stu-id="48fd3-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="48fd3-114">Odebere projekt nebo více projektů ze souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="48fd3-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="48fd3-115">[Vzorů podpory zástupných znaků](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux na základě terminály.</span><span class="sxs-lookup"><span data-stu-id="48fd3-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="48fd3-116">Vypíše všechny projekty v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="48fd3-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="48fd3-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="48fd3-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="48fd3-118">Soubor řešení se má použít.</span><span class="sxs-lookup"><span data-stu-id="48fd3-118">Solution file to use.</span></span> <span data-ttu-id="48fd3-119">Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.</span><span class="sxs-lookup"><span data-stu-id="48fd3-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="48fd3-120">Pokud v adresáři existuje více souborů řešení, musí zadat jeden.</span><span class="sxs-lookup"><span data-stu-id="48fd3-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="48fd3-121">Možnosti</span><span class="sxs-lookup"><span data-stu-id="48fd3-121">Options</span></span>

`-h|--help`

<span data-ttu-id="48fd3-122">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="48fd3-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="48fd3-123">Příklady</span><span class="sxs-lookup"><span data-stu-id="48fd3-123">Examples</span></span>

<span data-ttu-id="48fd3-124">Přidáte do řešení projektu v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="48fd3-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="48fd3-125">Odeberte z řešení projektu v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="48fd3-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="48fd3-126">Přidání více projekty jazyka C# do řešení:</span><span class="sxs-lookup"><span data-stu-id="48fd3-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="48fd3-127">Odeberte z řešení více projekty jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="48fd3-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="48fd3-128">Přidání více projekty jazyka C# do řešení pomocí podpory zástupných znaků vzoru:</span><span class="sxs-lookup"><span data-stu-id="48fd3-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="48fd3-129">Odeberte z řešení, které využívá model podpory zástupných znaků více projekty jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="48fd3-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> <span data-ttu-id="48fd3-130">Podpory zástupných znaků není funkce rozhraní příkazového řádku, ale místo toho funkci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="48fd3-130">Globbing is not a CLI feature but rather a feature of the command shell.</span></span> <span data-ttu-id="48fd3-131">Chcete-li úspěšně rozbalit soubory, je nutné použít prostředí, které podporuje podpory zástupných znaků.</span><span class="sxs-lookup"><span data-stu-id="48fd3-131">To successfully expand the files, you must use a shell that supports globbing.</span></span> <span data-ttu-id="48fd3-132">Další informace o podpory zástupných znaků naleznete v tématu [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span><span class="sxs-lookup"><span data-stu-id="48fd3-132">For more information about globbing, see [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span></span>
