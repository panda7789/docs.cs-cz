---
title: příkaz DotNet serveru sestavení
description: Příkaz dotnet sestavení serveru komunikuje se servery tím, že sestavení.
ms.date: 04/24/2019
ms.openlocfilehash: 491ac37e7f75f930423b3c7e43e3c090ec1ed07d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754287"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="e9bff-103">DotNet – server sestavení</span><span class="sxs-lookup"><span data-stu-id="e9bff-103">dotnet build-server</span></span>

<span data-ttu-id="e9bff-104">**Tento článek se týká: ✓** sady SDK .NET Core 2.1 a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="e9bff-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="e9bff-105">Name</span><span class="sxs-lookup"><span data-stu-id="e9bff-105">Name</span></span>

<span data-ttu-id="e9bff-106">`dotnet build-server` -Komunikuje se servery pro spuštění sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9bff-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e9bff-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="e9bff-107">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="e9bff-108">Příkazy</span><span class="sxs-lookup"><span data-stu-id="e9bff-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="e9bff-109">Vypne sestavovací servery, které jsou spuštěny z dotnet.</span><span class="sxs-lookup"><span data-stu-id="e9bff-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="e9bff-110">Ve výchozím nastavení jsou všechny servery vypnout.</span><span class="sxs-lookup"><span data-stu-id="e9bff-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="e9bff-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e9bff-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="e9bff-112">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="e9bff-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="e9bff-113">Ukončí MSBuild serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9bff-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="e9bff-114">Server sestavení vypne syntaxi Razor.</span><span class="sxs-lookup"><span data-stu-id="e9bff-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="e9bff-115">Vypne jazyce Visual Basic / server sestavení kompilátor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e9bff-115">Shuts down the VB/C# compiler build server.</span></span>