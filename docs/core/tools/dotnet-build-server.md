---
title: příkaz DotNet serveru sestavení
description: Příkaz dotnet sestavení serveru komunikuje se servery tím, že sestavení.
ms.date: 12/04/2018
ms.openlocfilehash: 7f78a0cae6e3297f3084754dc56b0da4eac38caf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665309"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="3c60b-103">DotNet – server sestavení</span><span class="sxs-lookup"><span data-stu-id="3c60b-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="3c60b-104">Název</span><span class="sxs-lookup"><span data-stu-id="3c60b-104">Name</span></span>

<span data-ttu-id="3c60b-105">`dotnet build-server` -Komunikuje se servery pro spuštění sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c60b-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3c60b-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="3c60b-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="3c60b-107">Příkazy</span><span class="sxs-lookup"><span data-stu-id="3c60b-107">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="3c60b-108">Vypne sestavovací servery, které jsou spuštěny z dotnet.</span><span class="sxs-lookup"><span data-stu-id="3c60b-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="3c60b-109">Ve výchozím nastavení jsou všechny servery vypnout.</span><span class="sxs-lookup"><span data-stu-id="3c60b-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="3c60b-110">Možnosti</span><span class="sxs-lookup"><span data-stu-id="3c60b-110">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="3c60b-111">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="3c60b-111">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="3c60b-112">Ukončí MSBuild serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c60b-112">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="3c60b-113">Server sestavení vypne syntaxi Razor.</span><span class="sxs-lookup"><span data-stu-id="3c60b-113">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="3c60b-114">Vypne jazyce Visual Basic / server sestavení kompilátor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="3c60b-114">Shuts down the VB/C# compiler build server.</span></span>