---
title: příkaz serveru sestavení DotNet - .NET Core rozhraní příkazového řádku
description: Serveru sestavení dotnet komunikuje se servery, které jsou spouštěné sestavení.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 929b8d74aa5f3f0ad73b108be8a5bf22f86e30d6
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696251"
---
# <a name="dotnet-build"></a><span data-ttu-id="43c21-103">sestavení pro DotNet.</span><span class="sxs-lookup"><span data-stu-id="43c21-103">dotnet-build</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="43c21-104">Název</span><span class="sxs-lookup"><span data-stu-id="43c21-104">Name</span></span>

<span data-ttu-id="43c21-105">`dotnet build-server` -Komunikuje se servery, které jsou spouštěné sestavení.</span><span class="sxs-lookup"><span data-stu-id="43c21-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="43c21-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="43c21-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="43c21-107">Příkazy</span><span class="sxs-lookup"><span data-stu-id="43c21-107">Commands</span></span>

`shutdown`

<span data-ttu-id="43c21-108">Vypne servery sestavení, které jsou spuštěné z dotnet.</span><span class="sxs-lookup"><span data-stu-id="43c21-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="43c21-109">Ve výchozím nastavení jsou všechny servery vypnout.</span><span class="sxs-lookup"><span data-stu-id="43c21-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="43c21-110">Možnosti</span><span class="sxs-lookup"><span data-stu-id="43c21-110">Options</span></span>

`-h|--help`

<span data-ttu-id="43c21-111">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="43c21-111">Prints out a short help for the command.</span></span>

`--msbuild`

<span data-ttu-id="43c21-112">Jejím ukončení MSBuild sestavení serveru.</span><span class="sxs-lookup"><span data-stu-id="43c21-112">Shuts down the MSBuild build server.</span></span>

`--razor`

<span data-ttu-id="43c21-113">Jejím ukončení syntaxi Razor sestavení serveru.</span><span class="sxs-lookup"><span data-stu-id="43c21-113">Shuts down the Razor build server.</span></span>

`--vbcscompiler`

<span data-ttu-id="43c21-114">Ukončí jazyce Visual Basic / kompilátor jazyka C# sestavení serveru.</span><span class="sxs-lookup"><span data-stu-id="43c21-114">Shuts down the VB/C# compiler build server.</span></span>
