---
title: příkaz DotNet serveru sestavení
description: Příkaz dotnet sestavení serveru komunikuje se servery tím, že sestavení.
ms.date: 12/04/2018
ms.openlocfilehash: 7f78a0cae6e3297f3084754dc56b0da4eac38caf
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169652"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="a9869-103">DotNet – server sestavení</span><span class="sxs-lookup"><span data-stu-id="a9869-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="a9869-104">Název</span><span class="sxs-lookup"><span data-stu-id="a9869-104">Name</span></span>

<span data-ttu-id="a9869-105">`dotnet build-server` -Komunikuje se servery pro spuštění sestavení.</span><span class="sxs-lookup"><span data-stu-id="a9869-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a9869-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="a9869-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="a9869-107">Příkazy</span><span class="sxs-lookup"><span data-stu-id="a9869-107">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="a9869-108">Vypne sestavovací servery, které jsou spuštěny z dotnet.</span><span class="sxs-lookup"><span data-stu-id="a9869-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="a9869-109">Ve výchozím nastavení jsou všechny servery vypnout.</span><span class="sxs-lookup"><span data-stu-id="a9869-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="a9869-110">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a9869-110">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="a9869-111">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a9869-111">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="a9869-112">Ukončí MSBuild serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="a9869-112">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="a9869-113">Server sestavení vypne syntaxi Razor.</span><span class="sxs-lookup"><span data-stu-id="a9869-113">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="a9869-114">Vypne jazyce Visual Basic / server sestavení kompilátor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="a9869-114">Shuts down the VB/C# compiler build server.</span></span>