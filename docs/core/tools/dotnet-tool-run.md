---
title: dotnet nástroj spustit, příkaz
description: Příkaz spuštění nástroje dotnet vyvolá místní nástroj.
ms.date: 02/14/2020
ms.openlocfilehash: f79c239363e8b3abbd55c54dd1912443e6777fb7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463330"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="3d998-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="3d998-103">dotnet tool run</span></span>

<span data-ttu-id="3d998-104">**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="3d998-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3d998-105">Název</span><span class="sxs-lookup"><span data-stu-id="3d998-105">Name</span></span>

<span data-ttu-id="3d998-106">`dotnet tool run`- Vyvolá místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="3d998-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3d998-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="3d998-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a><span data-ttu-id="3d998-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3d998-108">Description</span></span>

<span data-ttu-id="3d998-109">Příkaz `dotnet tool run` prohledává soubory manifestů nástroje, které jsou v oboru pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="3d998-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="3d998-110">Když najde odkaz na zadaný nástroj, spustí nástroj.</span><span class="sxs-lookup"><span data-stu-id="3d998-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="3d998-111">Další informace naleznete [v tématu Invoke a local tool](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="3d998-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="3d998-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3d998-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="3d998-113">Název příkazu nástroje, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="3d998-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="3d998-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="3d998-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="3d998-115">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="3d998-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="3d998-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d998-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="3d998-117">Spustí `dotnetsay` místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="3d998-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d998-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d998-118">See also</span></span>

- [<span data-ttu-id="3d998-119">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="3d998-119">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="3d998-120">Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="3d998-120">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
