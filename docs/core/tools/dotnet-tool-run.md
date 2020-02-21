---
title: příkaz pro spuštění nástroje dotnet
description: Příkaz pro spuštění nástroje dotnet vyvolá místní nástroj.
ms.date: 02/14/2020
ms.openlocfilehash: 05b21c0f5ea86f4b99b220f556c61bf83f464114
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543878"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="d6167-103">spuštění nástroje dotnet</span><span class="sxs-lookup"><span data-stu-id="d6167-103">dotnet tool run</span></span>

<span data-ttu-id="d6167-104">**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="d6167-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d6167-105">Název</span><span class="sxs-lookup"><span data-stu-id="d6167-105">Name</span></span>

<span data-ttu-id="d6167-106">`dotnet tool run` – vyvolá místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="d6167-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d6167-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d6167-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME> 
dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="d6167-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d6167-108">Description</span></span>

<span data-ttu-id="d6167-109">Příkaz `dotnet tool run` vyhledá soubory manifestu nástroje, které jsou v oboru pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="d6167-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="d6167-110">Když najde odkaz na zadaný nástroj, nástroj ho spustí.</span><span class="sxs-lookup"><span data-stu-id="d6167-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="d6167-111">Další informace naleznete v tématu [vyvolání místního nástroje](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="d6167-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="d6167-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d6167-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="d6167-113">Název příkazu nástroje, který se má spustit.</span><span class="sxs-lookup"><span data-stu-id="d6167-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="d6167-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d6167-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d6167-115">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="d6167-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="d6167-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6167-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="d6167-117">Spustí místní nástroj `dotnetsay`.</span><span class="sxs-lookup"><span data-stu-id="d6167-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6167-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6167-118">See also</span></span>

- [<span data-ttu-id="d6167-119">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6167-119">.NET Core tools</span></span>](global-tools.md)
