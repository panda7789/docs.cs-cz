---
title: dotnet sln, příkaz
description: Příkaz dotnet-sln poskytuje vhodnou možnost přidání, odebrání a seznamu projektů v souboru řešení.
ms.date: 02/14/2020
ms.openlocfilehash: 231287477d986f9ec4a5404cc5278e76c297faa4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463402"
---
# <a name="dotnet-sln"></a><span data-ttu-id="55eee-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="55eee-103">dotnet sln</span></span>

<span data-ttu-id="55eee-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="55eee-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="55eee-105">Název</span><span class="sxs-lookup"><span data-stu-id="55eee-105">Name</span></span>

<span data-ttu-id="55eee-106">`dotnet sln`- Uvádí nebo upravuje projekty v souboru řešení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55eee-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="55eee-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="55eee-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a><span data-ttu-id="55eee-108">Popis</span><span class="sxs-lookup"><span data-stu-id="55eee-108">Description</span></span>

<span data-ttu-id="55eee-109">Příkaz `dotnet sln` poskytuje pohodlný způsob, jak vypsat a upravit projekty v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="55eee-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="55eee-110">Chcete-li `dotnet sln` použít příkaz, musí již existovat soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="55eee-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="55eee-111">Pokud ho potřebujete vytvořit, použijte nový příkaz [dotnet,](dotnet-new.md) jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="55eee-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="55eee-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="55eee-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="55eee-113">Soubor řešení, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="55eee-113">The solution file to use.</span></span> <span data-ttu-id="55eee-114">Pokud je tento argument vynechán, příkaz prohledá aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="55eee-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="55eee-115">Pokud nenalezne žádný soubor řešení nebo více souborů řešení, příkaz se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="55eee-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="55eee-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="55eee-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="55eee-117">Vytiskne popis použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="55eee-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="55eee-118">Příkazy</span><span class="sxs-lookup"><span data-stu-id="55eee-118">Commands</span></span>

### `list`

<span data-ttu-id="55eee-119">Zobrazí seznam všech projektů v souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="55eee-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="55eee-120">Synopse</span><span class="sxs-lookup"><span data-stu-id="55eee-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="55eee-121">Argumenty</span><span class="sxs-lookup"><span data-stu-id="55eee-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="55eee-122">Soubor řešení, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="55eee-122">The solution file to use.</span></span> <span data-ttu-id="55eee-123">Pokud je tento argument vynechán, příkaz prohledá aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="55eee-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="55eee-124">Pokud nenalezne žádný soubor řešení nebo více souborů řešení, příkaz se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="55eee-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="55eee-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="55eee-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="55eee-126">Vytiskne popis použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="55eee-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="55eee-127">Přidá jeden nebo více projektů do souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="55eee-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="55eee-128">Synopse</span><span class="sxs-lookup"><span data-stu-id="55eee-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="55eee-129">Argumenty</span><span class="sxs-lookup"><span data-stu-id="55eee-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="55eee-130">Soubor řešení, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="55eee-130">The solution file to use.</span></span> <span data-ttu-id="55eee-131">Pokud není zadán, příkaz vyhledá aktuální adresář pro jeden a selže, pokud existuje více souborů řešení.</span><span class="sxs-lookup"><span data-stu-id="55eee-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="55eee-132">Cesta k projektu nebo projekty přidat do řešení.</span><span class="sxs-lookup"><span data-stu-id="55eee-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="55eee-133">Unix/Linux shell [globbing vzor](https://en.wikipedia.org/wiki/Glob_(programming)) expanze jsou `dotnet sln` zpracovány správně příkazem.</span><span class="sxs-lookup"><span data-stu-id="55eee-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="55eee-134">Možnosti</span><span class="sxs-lookup"><span data-stu-id="55eee-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="55eee-135">Vytiskne popis použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="55eee-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="55eee-136">Umístí projekty do kořenového adresáře řešení, nikoli do vytvoření složky řešení.</span><span class="sxs-lookup"><span data-stu-id="55eee-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="55eee-137">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="55eee-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder <PATH>`**

  <span data-ttu-id="55eee-138">Cílová cesta ke složce řešení, do které chcete přidat projekty.</span><span class="sxs-lookup"><span data-stu-id="55eee-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="55eee-139">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="55eee-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="55eee-140">Odebere projekt nebo více projektů ze souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="55eee-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="55eee-141">Synopse</span><span class="sxs-lookup"><span data-stu-id="55eee-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="55eee-142">Argumenty</span><span class="sxs-lookup"><span data-stu-id="55eee-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="55eee-143">Soubor řešení, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="55eee-143">The solution file to use.</span></span> <span data-ttu-id="55eee-144">Pokud je ponecháno neurčeno, příkaz hledá aktuální adresář pro jeden a selže, pokud existuje více souborů řešení.</span><span class="sxs-lookup"><span data-stu-id="55eee-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="55eee-145">Cesta k projektu nebo projekty přidat do řešení.</span><span class="sxs-lookup"><span data-stu-id="55eee-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="55eee-146">Unix/Linux shell [globbing vzor](https://en.wikipedia.org/wiki/Glob_(programming)) expanze jsou `dotnet sln` zpracovány správně příkazem.</span><span class="sxs-lookup"><span data-stu-id="55eee-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="55eee-147">Možnosti</span><span class="sxs-lookup"><span data-stu-id="55eee-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="55eee-148">Vytiskne popis použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="55eee-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="55eee-149">Příklady</span><span class="sxs-lookup"><span data-stu-id="55eee-149">Examples</span></span>

- <span data-ttu-id="55eee-150">Seznam projektů v řešení:</span><span class="sxs-lookup"><span data-stu-id="55eee-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="55eee-151">Přidejte projekt Jazyka C# do řešení:</span><span class="sxs-lookup"><span data-stu-id="55eee-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="55eee-152">Odeberte projekt Jazyka C# z řešení:</span><span class="sxs-lookup"><span data-stu-id="55eee-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="55eee-153">Přidejte více projektů jazyka C# do kořenového adresáře řešení:</span><span class="sxs-lookup"><span data-stu-id="55eee-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="55eee-154">Přidejte do řešení více projektů jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="55eee-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="55eee-155">Odeberte z řešení více projektů jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="55eee-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="55eee-156">Přidejte do řešení více projektů Jazyka C# pomocí globbingového vzoru (pouze Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="55eee-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="55eee-157">Přidejte více projektů Jazyka C# do řešení pomocí globbing vzor (pouze Windows PowerShell):</span><span class="sxs-lookup"><span data-stu-id="55eee-157">Add multiple C# projects to a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add (ls **/*.csproj)
  ```

- <span data-ttu-id="55eee-158">Odebrání více projektů Jazyka C# z řešení pomocí globbing ového vzoru (pouze Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="55eee-158">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- <span data-ttu-id="55eee-159">Odeberte více projektů jazyka C# z řešení pomocí globbing vzor (pouze windows powershellu):</span><span class="sxs-lookup"><span data-stu-id="55eee-159">Remove multiple C# projects from a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove (ls **/*.csproj)
  ```
