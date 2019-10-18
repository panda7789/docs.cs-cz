---
title: dotnet – sestavení – příkaz serveru
description: Příkaz dotnet Build-Server komunikuje s servery spuštěnými sestavením.
ms.date: 04/24/2019
ms.openlocfilehash: 1c6c6dcdb53d779426daf5daa470d2ad0470a7a1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523012"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="65635-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="65635-103">dotnet build-server</span></span>

<span data-ttu-id="65635-104">**Tento článek se týká: ✓** .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="65635-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="65635-105">Name</span><span class="sxs-lookup"><span data-stu-id="65635-105">Name</span></span>

<span data-ttu-id="65635-106">`dotnet build-server` – spolupracuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="65635-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="65635-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="65635-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="65635-108">Příkazy</span><span class="sxs-lookup"><span data-stu-id="65635-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="65635-109">Ukončí sestavovací servery, které jsou spuštěny z dotnet.</span><span class="sxs-lookup"><span data-stu-id="65635-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="65635-110">Ve výchozím nastavení jsou všechny servery vypnuté.</span><span class="sxs-lookup"><span data-stu-id="65635-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="65635-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="65635-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="65635-112">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="65635-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="65635-113">Vypne server sestavení MSBuild.</span><span class="sxs-lookup"><span data-stu-id="65635-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="65635-114">Vypne server sestavení Razor.</span><span class="sxs-lookup"><span data-stu-id="65635-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="65635-115">Ukončí server sestavení VB/C# Compiler.</span><span class="sxs-lookup"><span data-stu-id="65635-115">Shuts down the VB/C# compiler build server.</span></span>
