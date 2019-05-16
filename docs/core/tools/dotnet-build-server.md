---
title: příkaz DotNet serveru sestavení
description: Příkaz dotnet sestavení serveru komunikuje se servery tím, že sestavení.
ms.date: 04/24/2019
ms.openlocfilehash: fa663bc045e8abfc3375a0226be7d16331b49740
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632087"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="2e7f0-103">DotNet – server sestavení</span><span class="sxs-lookup"><span data-stu-id="2e7f0-103">dotnet build-server</span></span>

<span data-ttu-id="2e7f0-104">**Tento článek se týká: ✓** sady SDK .NET Core 2.1 a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="2e7f0-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="2e7f0-105">Name</span><span class="sxs-lookup"><span data-stu-id="2e7f0-105">Name</span></span>

<span data-ttu-id="2e7f0-106">`dotnet build-server` -Komunikuje se servery pro spuštění sestavení.</span><span class="sxs-lookup"><span data-stu-id="2e7f0-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2e7f0-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="2e7f0-107">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="2e7f0-108">Příkazy</span><span class="sxs-lookup"><span data-stu-id="2e7f0-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="2e7f0-109">Vypne sestavovací servery, které jsou spuštěny z dotnet.</span><span class="sxs-lookup"><span data-stu-id="2e7f0-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="2e7f0-110">Ve výchozím nastavení jsou všechny servery vypnout.</span><span class="sxs-lookup"><span data-stu-id="2e7f0-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="2e7f0-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="2e7f0-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="2e7f0-112">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="2e7f0-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="2e7f0-113">Ukončí MSBuild serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="2e7f0-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="2e7f0-114">Server sestavení vypne syntaxi Razor.</span><span class="sxs-lookup"><span data-stu-id="2e7f0-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="2e7f0-115">Vypne jazyce Visual Basic / server sestavení kompilátor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2e7f0-115">Shuts down the VB/C# compiler build server.</span></span>
