---
title: dotnet build-server, příkaz
description: Příkaz dotnet build-server spolupracuje se servery spuštěnými sestavením.
ms.date: 02/14/2020
ms.openlocfilehash: 882b697c07aac0e20266f3ad4e6c11888a0b7acc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463728"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="f196f-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="f196f-103">dotnet build-server</span></span>

<span data-ttu-id="f196f-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="f196f-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f196f-105">Název</span><span class="sxs-lookup"><span data-stu-id="f196f-105">Name</span></span>

<span data-ttu-id="f196f-106">`dotnet build-server`- Spolupracuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="f196f-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f196f-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="f196f-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]

dotnet build-server shutdown -h|--help

dotnet build-server -h|--help
```

## <a name="commands"></a><span data-ttu-id="f196f-108">Příkazy</span><span class="sxs-lookup"><span data-stu-id="f196f-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="f196f-109">Vypne servery sestavení, které jsou spuštěny z dotnet.</span><span class="sxs-lookup"><span data-stu-id="f196f-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="f196f-110">Ve výchozím nastavení jsou všechny servery vypnuty.</span><span class="sxs-lookup"><span data-stu-id="f196f-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="f196f-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f196f-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f196f-112">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f196f-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="f196f-113">Vypne server sestavení MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f196f-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="f196f-114">Vypne server sestavení Razor.</span><span class="sxs-lookup"><span data-stu-id="f196f-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="f196f-115">Vypne server sestavení kompilátoru VB/C#.</span><span class="sxs-lookup"><span data-stu-id="f196f-115">Shuts down the VB/C# compiler build server.</span></span>
