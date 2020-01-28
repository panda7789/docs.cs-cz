---
title: dotnet – sestavení – příkaz serveru
description: Příkaz dotnet Build-Server komunikuje s servery spuštěnými sestavením.
ms.date: 04/24/2019
ms.openlocfilehash: e77a4d9f49f555ac847bb13380380599eef881b1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734373"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="e3b78-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="e3b78-103">dotnet build-server</span></span>

<span data-ttu-id="e3b78-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="e3b78-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="e3b78-105">Name</span><span class="sxs-lookup"><span data-stu-id="e3b78-105">Name</span></span>

<span data-ttu-id="e3b78-106">`dotnet build-server` – spolupracuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="e3b78-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e3b78-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="e3b78-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="e3b78-108">Příkazy</span><span class="sxs-lookup"><span data-stu-id="e3b78-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="e3b78-109">Ukončí sestavovací servery, které jsou spuštěny z dotnet.</span><span class="sxs-lookup"><span data-stu-id="e3b78-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="e3b78-110">Ve výchozím nastavení jsou všechny servery vypnuté.</span><span class="sxs-lookup"><span data-stu-id="e3b78-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="e3b78-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e3b78-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e3b78-112">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="e3b78-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="e3b78-113">Vypne server sestavení MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e3b78-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="e3b78-114">Vypne server sestavení Razor.</span><span class="sxs-lookup"><span data-stu-id="e3b78-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="e3b78-115">Ukončí server sestavení VB/C# Compiler.</span><span class="sxs-lookup"><span data-stu-id="e3b78-115">Shuts down the VB/C# compiler build server.</span></span>
