---
title: příkaz SLN – DotNet - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet sln poskytuje vhodnou možnost přidávat, odstraňovat a seznam projekty v řešení souboru.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: dd77281b55b3e7fc7c293e402d11de016ef73cf8
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696709"
---
# <a name="dotnet-sln"></a><span data-ttu-id="aeb49-103">SLN – DotNet.</span><span class="sxs-lookup"><span data-stu-id="aeb49-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="aeb49-104">Název</span><span class="sxs-lookup"><span data-stu-id="aeb49-104">Name</span></span>

<span data-ttu-id="aeb49-105">`dotnet sln` -Upravuje soubor řešení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aeb49-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="aeb49-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="aeb49-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="aeb49-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aeb49-107">Description</span></span>

<span data-ttu-id="aeb49-108">`dotnet sln` Příkaz nabízí pohodlný způsob, jak přidat, odebrat a seznam projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="aeb49-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

## <a name="commands"></a><span data-ttu-id="aeb49-109">Příkazy</span><span class="sxs-lookup"><span data-stu-id="aeb49-109">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="aeb49-110">Přidá do řešení souboru projektu nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="aeb49-110">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="aeb49-111">[Vzory expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux, na základě terminály.</span><span class="sxs-lookup"><span data-stu-id="aeb49-111">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="aeb49-112">Odebere projektu nebo více projektů ze souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="aeb49-112">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="aeb49-113">[Vzory expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux, na základě terminály.</span><span class="sxs-lookup"><span data-stu-id="aeb49-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="aeb49-114">Zobrazí všechny projekty v řešení souboru.</span><span class="sxs-lookup"><span data-stu-id="aeb49-114">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="aeb49-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="aeb49-115">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="aeb49-116">Soubor řešení se má použít.</span><span class="sxs-lookup"><span data-stu-id="aeb49-116">Solution file to use.</span></span> <span data-ttu-id="aeb49-117">Pokud není zadaný, hledá příkaz aktuální adresář pro jednu.</span><span class="sxs-lookup"><span data-stu-id="aeb49-117">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="aeb49-118">Pokud se nachází několik souborů řešení v adresáři, jeden musí být zadán.</span><span class="sxs-lookup"><span data-stu-id="aeb49-118">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="aeb49-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="aeb49-119">Options</span></span>

`-h|--help`

<span data-ttu-id="aeb49-120">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="aeb49-120">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="aeb49-121">Příklady</span><span class="sxs-lookup"><span data-stu-id="aeb49-121">Examples</span></span>

<span data-ttu-id="aeb49-122">Přidejte projekt C# do řešení:</span><span class="sxs-lookup"><span data-stu-id="aeb49-122">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="aeb49-123">Odebrání řešení projekt C#:</span><span class="sxs-lookup"><span data-stu-id="aeb49-123">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="aeb49-124">Přidání více projektů C# do řešení:</span><span class="sxs-lookup"><span data-stu-id="aeb49-124">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="aeb49-125">Odebrání řešení více projektů C#:</span><span class="sxs-lookup"><span data-stu-id="aeb49-125">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="aeb49-126">Přidání více projektů C# do řešení pomocí vzoru expanze názvů:</span><span class="sxs-lookup"><span data-stu-id="aeb49-126">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="aeb49-127">Odebrání řešení pomocí vzoru expanze názvů více projektů C#:</span><span class="sxs-lookup"><span data-stu-id="aeb49-127">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`
