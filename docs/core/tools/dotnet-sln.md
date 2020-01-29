---
title: dotnet sln – příkaz
description: Příkaz dotnet-sln nabízí pohodlný způsob přidávání, odebírání a vypsání projektů v souboru řešení.
ms.date: 10/29/2019
ms.openlocfilehash: e344deaae0867202a79a3c38df48a2be8d4d7d13
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733084"
---
# <a name="dotnet-sln"></a><span data-ttu-id="344c8-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="344c8-103">dotnet sln</span></span>

<span data-ttu-id="344c8-104">**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="344c8-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="344c8-105">Name</span><span class="sxs-lookup"><span data-stu-id="344c8-105">Name</span></span>

<span data-ttu-id="344c8-106">`dotnet sln` – upraví soubor řešení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="344c8-106">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="344c8-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="344c8-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a><span data-ttu-id="344c8-108">Popis</span><span class="sxs-lookup"><span data-stu-id="344c8-108">Description</span></span>

<span data-ttu-id="344c8-109">Příkaz `dotnet sln` poskytuje pohodlný způsob, jak přidávat, odebírat a vypisovat projekty v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="344c8-109">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="344c8-110">Chcete-li použít příkaz `dotnet sln`, soubor řešení již musí existovat.</span><span class="sxs-lookup"><span data-stu-id="344c8-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="344c8-111">Pokud ho potřebujete vytvořit, použijte příkaz [dotnet New](dotnet-new.md) , jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="344c8-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="344c8-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="344c8-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="344c8-113">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="344c8-113">The solution file to use.</span></span> <span data-ttu-id="344c8-114">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="344c8-114">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="344c8-115">Pokud je v adresáři více souborů řešení, je nutné zadat jeden.</span><span class="sxs-lookup"><span data-stu-id="344c8-115">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="344c8-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="344c8-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="344c8-117">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="344c8-117">Prints out a short help for the command.</span></span>

## <a name="commands"></a><span data-ttu-id="344c8-118">Příkazy</span><span class="sxs-lookup"><span data-stu-id="344c8-118">Commands</span></span>

### `add`

<span data-ttu-id="344c8-119">Přidá do souboru řešení projekt nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="344c8-119">Adds a project or multiple projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="344c8-120">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="344c8-120">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH>
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="344c8-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="344c8-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="344c8-122">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="344c8-122">The solution file to use.</span></span> <span data-ttu-id="344c8-123">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="344c8-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="344c8-124">Pokud je v adresáři více souborů řešení, je nutné zadat jeden.</span><span class="sxs-lookup"><span data-stu-id="344c8-124">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="344c8-125">Cesta k projektu, který se má přidat do řešení</span><span class="sxs-lookup"><span data-stu-id="344c8-125">The path to the project to add to the solution.</span></span> <span data-ttu-id="344c8-126">Přidejte více projektů přidáním jednoho po druhém oddělené mezery.</span><span class="sxs-lookup"><span data-stu-id="344c8-126">Add multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="344c8-127">Rozšíření [vzoru expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) prostředí systému UNIX/Linux jsou zpracována správně pomocí příkazu `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="344c8-127">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="344c8-128">Možnosti</span><span class="sxs-lookup"><span data-stu-id="344c8-128">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="344c8-129">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="344c8-129">Prints out a short help for the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="344c8-130">Umístí projekty do kořenového adresáře řešení namísto vytvoření složky řešení.</span><span class="sxs-lookup"><span data-stu-id="344c8-130">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="344c8-131">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="344c8-131">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder`**

  <span data-ttu-id="344c8-132">Cílová cesta ke složce řešení, do které se mají přidat projekty</span><span class="sxs-lookup"><span data-stu-id="344c8-132">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="344c8-133">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="344c8-133">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="344c8-134">Odebere projekt nebo více projektů ze souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="344c8-134">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="344c8-135">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="344c8-135">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH>
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="344c8-136">Arguments</span><span class="sxs-lookup"><span data-stu-id="344c8-136">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="344c8-137">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="344c8-137">The solution file to use.</span></span> <span data-ttu-id="344c8-138">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="344c8-138">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="344c8-139">Pokud je v adresáři více souborů řešení, je nutné zadat jeden.</span><span class="sxs-lookup"><span data-stu-id="344c8-139">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="344c8-140">Cesta k projektu, který se má odebrat z řešení</span><span class="sxs-lookup"><span data-stu-id="344c8-140">The path to the project to remove from the solution.</span></span> <span data-ttu-id="344c8-141">Odeberte více projektů přidáním jednoho po druhém odděleném mezerami.</span><span class="sxs-lookup"><span data-stu-id="344c8-141">Remove multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="344c8-142">Rozšíření [vzoru expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) prostředí systému UNIX/Linux jsou zpracována správně pomocí příkazu `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="344c8-142">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="344c8-143">Možnosti</span><span class="sxs-lookup"><span data-stu-id="344c8-143">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="344c8-144">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="344c8-144">Prints out a short help for the command.</span></span>

### `list`

<span data-ttu-id="344c8-145">Zobrazí seznam všech projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="344c8-145">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="344c8-146">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="344c8-146">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="344c8-147">Arguments</span><span class="sxs-lookup"><span data-stu-id="344c8-147">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="344c8-148">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="344c8-148">The solution file to use.</span></span> <span data-ttu-id="344c8-149">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="344c8-149">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="344c8-150">Pokud je v adresáři více souborů řešení, je nutné zadat jeden.</span><span class="sxs-lookup"><span data-stu-id="344c8-150">If there are multiple solution files in the directory, one must be specified.</span></span>

#### <a name="options"></a><span data-ttu-id="344c8-151">Možnosti</span><span class="sxs-lookup"><span data-stu-id="344c8-151">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="344c8-152">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="344c8-152">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="344c8-153">Příklady</span><span class="sxs-lookup"><span data-stu-id="344c8-153">Examples</span></span>

- <span data-ttu-id="344c8-154">Přidání C# projektu do řešení:</span><span class="sxs-lookup"><span data-stu-id="344c8-154">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="344c8-155">Odebrání C# projektu z řešení:</span><span class="sxs-lookup"><span data-stu-id="344c8-155">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="344c8-156">Přidání více C# projektů do řešení:</span><span class="sxs-lookup"><span data-stu-id="344c8-156">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="344c8-157">Odebrání více C# projektů z řešení:</span><span class="sxs-lookup"><span data-stu-id="344c8-157">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="344c8-158">Přidání více C# projektů do řešení pomocí vzoru expanze názvů (jenom UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="344c8-158">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="344c8-159">Odebrání více C# projektů z řešení pomocí vzoru expanze (pouze systém UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="344c8-159">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
