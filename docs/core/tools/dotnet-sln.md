---
title: příkaz SLN – DotNet - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet sln poskytuje vhodnou možnost přidávat, odstraňovat a seznam projekty v řešení souboru.
author: mairaw
ms.author: mairaw
ms.date: 06/13/2018
ms.openlocfilehash: 65ae402ef5519863886c8cf833598f5314b4bdad
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208320"
---
# <a name="dotnet-sln"></a><span data-ttu-id="af648-103">SLN – DotNet.</span><span class="sxs-lookup"><span data-stu-id="af648-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="af648-104">Název</span><span class="sxs-lookup"><span data-stu-id="af648-104">Name</span></span>

<span data-ttu-id="af648-105">`dotnet sln` -Upravuje soubor řešení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="af648-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="af648-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="af648-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="af648-107">Popis</span><span class="sxs-lookup"><span data-stu-id="af648-107">Description</span></span>

<span data-ttu-id="af648-108">`dotnet sln` Příkaz nabízí pohodlný způsob, jak přidat, odebrat a seznam projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="af648-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="af648-109">Použít `dotnet sln` příkaz, musí již existovat soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="af648-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="af648-110">Pokud potřebujete vytvořit, použijte [dotnet nové](dotnet-new.md) příkazu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="af648-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="af648-111">Příkazy</span><span class="sxs-lookup"><span data-stu-id="af648-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="af648-112">Přidá do řešení souboru projektu nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="af648-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="af648-113">[Vzory expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux, na základě terminály.</span><span class="sxs-lookup"><span data-stu-id="af648-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="af648-114">Odebere projektu nebo více projektů ze souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="af648-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="af648-115">[Vzory expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux, na základě terminály.</span><span class="sxs-lookup"><span data-stu-id="af648-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="af648-116">Zobrazí všechny projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="af648-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="af648-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="af648-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="af648-118">Soubor řešení se má použít.</span><span class="sxs-lookup"><span data-stu-id="af648-118">Solution file to use.</span></span> <span data-ttu-id="af648-119">Pokud není zadaný, hledá příkaz aktuální adresář pro jednu.</span><span class="sxs-lookup"><span data-stu-id="af648-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="af648-120">Pokud se nachází několik souborů řešení v adresáři, jeden musí být zadán.</span><span class="sxs-lookup"><span data-stu-id="af648-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="af648-121">Možnosti</span><span class="sxs-lookup"><span data-stu-id="af648-121">Options</span></span>

`-h|--help`

<span data-ttu-id="af648-122">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="af648-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="af648-123">Příklady</span><span class="sxs-lookup"><span data-stu-id="af648-123">Examples</span></span>

<span data-ttu-id="af648-124">Přidejte projekt C# do řešení:</span><span class="sxs-lookup"><span data-stu-id="af648-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="af648-125">Odebrání řešení projekt C#:</span><span class="sxs-lookup"><span data-stu-id="af648-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="af648-126">Přidání více projektů C# do řešení:</span><span class="sxs-lookup"><span data-stu-id="af648-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="af648-127">Odebrání řešení více projektů C#:</span><span class="sxs-lookup"><span data-stu-id="af648-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="af648-128">Přidání více projektů C# do řešení pomocí vzoru expanze názvů:</span><span class="sxs-lookup"><span data-stu-id="af648-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="af648-129">Odebrání řešení pomocí vzoru expanze názvů více projektů C#:</span><span class="sxs-lookup"><span data-stu-id="af648-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`
