---
title: příkaz pro spuštění nástroje dotnet
description: Příkaz pro spuštění nástroje dotnet vyvolá místní nástroj.
ms.date: 02/14/2020
ms.openlocfilehash: 76830b8a8088fbf21f14ab0722b9547eabde7ba4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156956"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="ada50-103">spuštění nástroje dotnet</span><span class="sxs-lookup"><span data-stu-id="ada50-103">dotnet tool run</span></span>

<span data-ttu-id="ada50-104">**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="ada50-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ada50-105">Název</span><span class="sxs-lookup"><span data-stu-id="ada50-105">Name</span></span>

<span data-ttu-id="ada50-106">`dotnet tool run` – vyvolá místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="ada50-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ada50-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="ada50-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>
dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="ada50-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ada50-108">Description</span></span>

<span data-ttu-id="ada50-109">Příkaz `dotnet tool run` vyhledá soubory manifestu nástroje, které jsou v oboru pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="ada50-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="ada50-110">Když najde odkaz na zadaný nástroj, nástroj ho spustí.</span><span class="sxs-lookup"><span data-stu-id="ada50-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="ada50-111">Další informace naleznete v tématu [vyvolání místního nástroje](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="ada50-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="ada50-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ada50-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="ada50-113">Název příkazu nástroje, který se má spustit.</span><span class="sxs-lookup"><span data-stu-id="ada50-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="ada50-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ada50-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="ada50-115">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="ada50-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="ada50-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="ada50-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="ada50-117">Spustí místní nástroj `dotnetsay`.</span><span class="sxs-lookup"><span data-stu-id="ada50-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="ada50-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ada50-118">See also</span></span>

- [<span data-ttu-id="ada50-119">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="ada50-119">.NET Core tools</span></span>](global-tools.md)
