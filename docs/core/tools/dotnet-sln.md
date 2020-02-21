---
title: dotnet sln – příkaz
description: Příkaz dotnet-sln nabízí pohodlný způsob přidávání, odebírání a vypsání projektů v souboru řešení.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543479"
---
# <a name="dotnet-sln"></a><span data-ttu-id="38e2e-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="38e2e-103">dotnet sln</span></span>

<span data-ttu-id="38e2e-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="38e2e-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="38e2e-105">Název</span><span class="sxs-lookup"><span data-stu-id="38e2e-105">Name</span></span>

<span data-ttu-id="38e2e-106">`dotnet sln` – zobrazí nebo upraví projekty v souboru řešení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38e2e-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="38e2e-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="38e2e-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a><span data-ttu-id="38e2e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="38e2e-108">Description</span></span>

<span data-ttu-id="38e2e-109">Příkaz `dotnet sln` poskytuje pohodlný způsob, jak zobrazit a upravit projekty v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="38e2e-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="38e2e-110">Chcete-li použít příkaz `dotnet sln`, soubor řešení již musí existovat.</span><span class="sxs-lookup"><span data-stu-id="38e2e-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="38e2e-111">Pokud ho potřebujete vytvořit, použijte příkaz [dotnet New](dotnet-new.md) , jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="38e2e-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="38e2e-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="38e2e-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="38e2e-113">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="38e2e-113">The solution file to use.</span></span> <span data-ttu-id="38e2e-114">Pokud je tento argument vynechán, příkaz vyhledá v aktuálním adresáři jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="38e2e-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="38e2e-115">Pokud nenajde žádný soubor řešení nebo více souborů řešení, příkaz se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="38e2e-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="38e2e-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="38e2e-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="38e2e-117">Vytiskne popis způsobu použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="38e2e-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="38e2e-118">Příkazy</span><span class="sxs-lookup"><span data-stu-id="38e2e-118">Commands</span></span>

### `list`

<span data-ttu-id="38e2e-119">Zobrazí seznam všech projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="38e2e-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="38e2e-120">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="38e2e-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="38e2e-121">Argumenty</span><span class="sxs-lookup"><span data-stu-id="38e2e-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="38e2e-122">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="38e2e-122">The solution file to use.</span></span> <span data-ttu-id="38e2e-123">Pokud je tento argument vynechán, příkaz vyhledá v aktuálním adresáři jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="38e2e-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="38e2e-124">Pokud nenajde žádný soubor řešení nebo více souborů řešení, příkaz se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="38e2e-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="38e2e-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="38e2e-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="38e2e-126">Vytiskne popis způsobu použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="38e2e-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="38e2e-127">Přidá do souboru řešení jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="38e2e-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="38e2e-128">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="38e2e-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="38e2e-129">Argumenty</span><span class="sxs-lookup"><span data-stu-id="38e2e-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="38e2e-130">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="38e2e-130">The solution file to use.</span></span> <span data-ttu-id="38e2e-131">Pokud tento parametr není zadán, příkaz vyhledá v aktuálním adresáři jeden a v případě, že existuje více souborů řešení, bude neúspěšný.</span><span class="sxs-lookup"><span data-stu-id="38e2e-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="38e2e-132">Cesta k projektu nebo projektům, které se mají přidat do řešení</span><span class="sxs-lookup"><span data-stu-id="38e2e-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="38e2e-133">Rozšíření [vzoru expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) prostředí systému UNIX/Linux jsou zpracována správně pomocí příkazu `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="38e2e-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="38e2e-134">Možnosti</span><span class="sxs-lookup"><span data-stu-id="38e2e-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="38e2e-135">Vytiskne popis způsobu použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="38e2e-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="38e2e-136">Umístí projekty do kořenového adresáře řešení namísto vytvoření složky řešení.</span><span class="sxs-lookup"><span data-stu-id="38e2e-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="38e2e-137">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="38e2e-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder`**

  <span data-ttu-id="38e2e-138">Cílová cesta ke složce řešení, do které se mají přidat projekty</span><span class="sxs-lookup"><span data-stu-id="38e2e-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="38e2e-139">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="38e2e-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="38e2e-140">Odebere projekt nebo více projektů ze souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="38e2e-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="38e2e-141">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="38e2e-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="38e2e-142">Argumenty</span><span class="sxs-lookup"><span data-stu-id="38e2e-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="38e2e-143">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="38e2e-143">The solution file to use.</span></span> <span data-ttu-id="38e2e-144">Pokud parametr není zadán, příkaz vyhledá soubor v aktuálním adresáři a dojde k chybě, pokud existuje více souborů řešení.</span><span class="sxs-lookup"><span data-stu-id="38e2e-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="38e2e-145">Cesta k projektu nebo projektům, které se mají přidat do řešení</span><span class="sxs-lookup"><span data-stu-id="38e2e-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="38e2e-146">Rozšíření [vzoru expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) prostředí systému UNIX/Linux jsou zpracována správně pomocí příkazu `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="38e2e-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="38e2e-147">Možnosti</span><span class="sxs-lookup"><span data-stu-id="38e2e-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="38e2e-148">Vytiskne popis způsobu použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="38e2e-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="38e2e-149">Příklady</span><span class="sxs-lookup"><span data-stu-id="38e2e-149">Examples</span></span>

- <span data-ttu-id="38e2e-150">Seznam projektů v řešení:</span><span class="sxs-lookup"><span data-stu-id="38e2e-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="38e2e-151">Přidání C# projektu do řešení:</span><span class="sxs-lookup"><span data-stu-id="38e2e-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="38e2e-152">Odebrání C# projektu z řešení:</span><span class="sxs-lookup"><span data-stu-id="38e2e-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="38e2e-153">Přidání více C# projektů do kořenového adresáře řešení:</span><span class="sxs-lookup"><span data-stu-id="38e2e-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="38e2e-154">Přidání více C# projektů do řešení:</span><span class="sxs-lookup"><span data-stu-id="38e2e-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="38e2e-155">Odebrání více C# projektů z řešení:</span><span class="sxs-lookup"><span data-stu-id="38e2e-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="38e2e-156">Přidání více C# projektů do řešení pomocí vzoru expanze názvů (jenom UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="38e2e-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="38e2e-157">Odebrání více C# projektů z řešení pomocí vzoru expanze (pouze systém UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="38e2e-157">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
