---
title: dotnet sln – příkaz
description: Příkaz dotnet-sln nabízí pohodlný způsob přidávání, odebírání a vypsání projektů v souboru řešení.
ms.date: 06/13/2018
ms.openlocfilehash: 3f18d6a2851d955d07cecc0cbc4c161cf0ec3e08
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202789"
---
# <a name="dotnet-sln"></a><span data-ttu-id="f77c7-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="f77c7-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f77c7-104">Name</span><span class="sxs-lookup"><span data-stu-id="f77c7-104">Name</span></span>

<span data-ttu-id="f77c7-105">`dotnet sln`– Upraví soubor řešení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f77c7-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f77c7-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="f77c7-106">Synopsis</span></span>

```console
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f77c7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f77c7-107">Description</span></span>

<span data-ttu-id="f77c7-108">`dotnet sln` Příkaz nabízí pohodlný způsob, jak přidávat, odebírat a vypisovat projekty v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="f77c7-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="f77c7-109">Chcete-li `dotnet sln` použít příkaz, soubor řešení již musí existovat.</span><span class="sxs-lookup"><span data-stu-id="f77c7-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="f77c7-110">Pokud ho potřebujete vytvořit, použijte příkaz [dotnet New](dotnet-new.md) , jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f77c7-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```console
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="f77c7-111">Příkazy</span><span class="sxs-lookup"><span data-stu-id="f77c7-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="f77c7-112">Přidá do souboru řešení projekt nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="f77c7-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="f77c7-113">[Vzory expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) se podporují v terminálech založených na systému UNIX/Linux.</span><span class="sxs-lookup"><span data-stu-id="f77c7-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="f77c7-114">Odebere projekt nebo více projektů ze souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="f77c7-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="f77c7-115">[Vzory expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) se podporují v terminálech založených na systému UNIX/Linux.</span><span class="sxs-lookup"><span data-stu-id="f77c7-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="f77c7-116">Zobrazí seznam všech projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="f77c7-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="f77c7-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="f77c7-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="f77c7-118">Soubor řešení, který se má použít</span><span class="sxs-lookup"><span data-stu-id="f77c7-118">Solution file to use.</span></span> <span data-ttu-id="f77c7-119">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="f77c7-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="f77c7-120">Pokud je v adresáři více souborů řešení, je nutné zadat jeden.</span><span class="sxs-lookup"><span data-stu-id="f77c7-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="f77c7-121">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f77c7-121">Options</span></span>

`-h|--help`

<span data-ttu-id="f77c7-122">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="f77c7-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="f77c7-123">Příklady</span><span class="sxs-lookup"><span data-stu-id="f77c7-123">Examples</span></span>

<span data-ttu-id="f77c7-124">Přidání C# projektu do řešení:</span><span class="sxs-lookup"><span data-stu-id="f77c7-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="f77c7-125">Odebrání C# projektu z řešení:</span><span class="sxs-lookup"><span data-stu-id="f77c7-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="f77c7-126">Přidání více C# projektů do řešení:</span><span class="sxs-lookup"><span data-stu-id="f77c7-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="f77c7-127">Odebrání více C# projektů z řešení:</span><span class="sxs-lookup"><span data-stu-id="f77c7-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="f77c7-128">Přidání více C# projektů do řešení pomocí vzorového expanze názvů:</span><span class="sxs-lookup"><span data-stu-id="f77c7-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="f77c7-129">Odebrání více C# projektů z řešení pomocí vzoru expanze názvů:</span><span class="sxs-lookup"><span data-stu-id="f77c7-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> <span data-ttu-id="f77c7-130">Expanze názvů není funkcí CLI, ale spíše funkcí příkazového prostředí.</span><span class="sxs-lookup"><span data-stu-id="f77c7-130">Globbing is not a CLI feature but rather a feature of the command shell.</span></span> <span data-ttu-id="f77c7-131">Aby bylo možné soubory úspěšně rozšířit, je nutné použít prostředí, které podporuje expanze názvů.</span><span class="sxs-lookup"><span data-stu-id="f77c7-131">To successfully expand the files, you must use a shell that supports globbing.</span></span> <span data-ttu-id="f77c7-132">Další informace o expanzi názvů naleznete v tématu [Wikipedii](https://en.wikipedia.org/wiki/Glob_(programming)).</span><span class="sxs-lookup"><span data-stu-id="f77c7-132">For more information about globbing, see [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span></span>
