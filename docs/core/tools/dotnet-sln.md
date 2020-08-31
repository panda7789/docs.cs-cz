---
title: dotnet sln – příkaz
description: Příkaz dotnet-sln nabízí pohodlný způsob přidávání, odebírání a vypsání projektů v souboru řešení.
ms.date: 02/14/2020
ms.openlocfilehash: efe52f64a29c8825070bae9ee96b430b32176ffa
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053028"
---
# <a name="dotnet-sln"></a><span data-ttu-id="d64f2-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d64f2-103">dotnet sln</span></span>

<span data-ttu-id="d64f2-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="d64f2-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d64f2-105">Name</span><span class="sxs-lookup"><span data-stu-id="d64f2-105">Name</span></span>

<span data-ttu-id="d64f2-106">`dotnet sln` – Zobrazí nebo upraví projekty v souboru řešení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d64f2-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d64f2-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d64f2-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a><span data-ttu-id="d64f2-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d64f2-108">Description</span></span>

<span data-ttu-id="d64f2-109">`dotnet sln`Příkaz nabízí pohodlný způsob, jak zobrazit a upravit projekty v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="d64f2-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="d64f2-110">Chcete-li použít `dotnet sln` příkaz, soubor řešení již musí existovat.</span><span class="sxs-lookup"><span data-stu-id="d64f2-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="d64f2-111">Pokud ho potřebujete vytvořit, použijte příkaz [dotnet New](dotnet-new.md) , jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d64f2-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="d64f2-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="d64f2-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d64f2-113">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="d64f2-113">The solution file to use.</span></span> <span data-ttu-id="d64f2-114">Pokud je tento argument vynechán, příkaz vyhledá v aktuálním adresáři jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="d64f2-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="d64f2-115">Pokud nenajde žádný soubor řešení nebo více souborů řešení, příkaz se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="d64f2-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="d64f2-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d64f2-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d64f2-117">Vytiskne popis způsobu použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="d64f2-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="d64f2-118">Příkazy</span><span class="sxs-lookup"><span data-stu-id="d64f2-118">Commands</span></span>

### `list`

<span data-ttu-id="d64f2-119">Zobrazí seznam všech projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="d64f2-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d64f2-120">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d64f2-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="d64f2-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="d64f2-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d64f2-122">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="d64f2-122">The solution file to use.</span></span> <span data-ttu-id="d64f2-123">Pokud je tento argument vynechán, příkaz vyhledá v aktuálním adresáři jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="d64f2-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="d64f2-124">Pokud nenajde žádný soubor řešení nebo více souborů řešení, příkaz se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="d64f2-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="d64f2-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d64f2-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d64f2-126">Vytiskne popis způsobu použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="d64f2-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="d64f2-127">Přidá do souboru řešení jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="d64f2-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d64f2-128">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d64f2-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="d64f2-129">Arguments</span><span class="sxs-lookup"><span data-stu-id="d64f2-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d64f2-130">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="d64f2-130">The solution file to use.</span></span> <span data-ttu-id="d64f2-131">Pokud tento parametr není zadán, příkaz vyhledá v aktuálním adresáři jeden a v případě, že existuje více souborů řešení, bude neúspěšný.</span><span class="sxs-lookup"><span data-stu-id="d64f2-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="d64f2-132">Cesta k projektu nebo projektům, které se mají přidat do řešení</span><span class="sxs-lookup"><span data-stu-id="d64f2-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="d64f2-133">Rozšíření [vzoru expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) prostředí systému UNIX/Linux jsou správně zpracována `dotnet sln` příkazem.</span><span class="sxs-lookup"><span data-stu-id="d64f2-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="d64f2-134">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d64f2-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d64f2-135">Vytiskne popis způsobu použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="d64f2-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="d64f2-136">Umístí projekty do kořenového adresáře řešení namísto vytvoření složky řešení.</span><span class="sxs-lookup"><span data-stu-id="d64f2-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="d64f2-137">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d64f2-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder <PATH>`**

  <span data-ttu-id="d64f2-138">Cílová cesta ke složce řešení, do které se mají přidat projekty</span><span class="sxs-lookup"><span data-stu-id="d64f2-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="d64f2-139">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d64f2-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="d64f2-140">Odebere projekt nebo více projektů ze souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="d64f2-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d64f2-141">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d64f2-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="d64f2-142">Arguments</span><span class="sxs-lookup"><span data-stu-id="d64f2-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d64f2-143">Soubor řešení, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="d64f2-143">The solution file to use.</span></span> <span data-ttu-id="d64f2-144">Pokud parametr není zadán, příkaz vyhledá soubor v aktuálním adresáři a dojde k chybě, pokud existuje více souborů řešení.</span><span class="sxs-lookup"><span data-stu-id="d64f2-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="d64f2-145">Cesta k projektu nebo projektům, které se mají přidat do řešení</span><span class="sxs-lookup"><span data-stu-id="d64f2-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="d64f2-146">Rozšíření [vzoru expanze názvů](https://en.wikipedia.org/wiki/Glob_(programming)) prostředí systému UNIX/Linux jsou správně zpracována `dotnet sln` příkazem.</span><span class="sxs-lookup"><span data-stu-id="d64f2-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="d64f2-147">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d64f2-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d64f2-148">Vytiskne popis způsobu použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="d64f2-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="d64f2-149">Příklady</span><span class="sxs-lookup"><span data-stu-id="d64f2-149">Examples</span></span>

- <span data-ttu-id="d64f2-150">Seznam projektů v řešení:</span><span class="sxs-lookup"><span data-stu-id="d64f2-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="d64f2-151">Přidat projekt C# do řešení:</span><span class="sxs-lookup"><span data-stu-id="d64f2-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="d64f2-152">Odebrat projekt C# z řešení:</span><span class="sxs-lookup"><span data-stu-id="d64f2-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="d64f2-153">Přidání více projektů C# do kořenového adresáře řešení:</span><span class="sxs-lookup"><span data-stu-id="d64f2-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="d64f2-154">Přidání více projektů C# do řešení:</span><span class="sxs-lookup"><span data-stu-id="d64f2-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="d64f2-155">Odebrání více projektů C# z řešení:</span><span class="sxs-lookup"><span data-stu-id="d64f2-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="d64f2-156">Přidání více projektů C# do řešení pomocí vzoru expanze názvů (jenom UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="d64f2-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="d64f2-157">Přidání více projektů C# do řešení pomocí vzoru expanze (pouze Windows PowerShell):</span><span class="sxs-lookup"><span data-stu-id="d64f2-157">Add multiple C# projects to a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add (ls -r **/*.csproj)
  ```

- <span data-ttu-id="d64f2-158">Odebrání více projektů C# z řešení pomocí vzoru expanze názvů (pouze systémy UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="d64f2-158">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- <span data-ttu-id="d64f2-159">Odebrání více projektů C# z řešení pomocí vzoru expanze názvů (jenom Windows PowerShell):</span><span class="sxs-lookup"><span data-stu-id="d64f2-159">Remove multiple C# projects from a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove (ls -r **/*.csproj)
  ```
