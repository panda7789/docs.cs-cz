---
title: dotnet – sestavení – příkaz serveru
description: Příkaz dotnet Build-Server komunikuje s servery spuštěnými sestavením.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503776"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="69f4a-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="69f4a-103">dotnet build-server</span></span>

<span data-ttu-id="69f4a-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="69f4a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="69f4a-105">Název</span><span class="sxs-lookup"><span data-stu-id="69f4a-105">Name</span></span>

<span data-ttu-id="69f4a-106">`dotnet build-server` – spolupracuje se servery spuštěnými sestavením.</span><span class="sxs-lookup"><span data-stu-id="69f4a-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="69f4a-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="69f4a-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="69f4a-108">Příkazy</span><span class="sxs-lookup"><span data-stu-id="69f4a-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="69f4a-109">Ukončí sestavovací servery, které jsou spuštěny z dotnet.</span><span class="sxs-lookup"><span data-stu-id="69f4a-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="69f4a-110">Ve výchozím nastavení jsou všechny servery vypnuté.</span><span class="sxs-lookup"><span data-stu-id="69f4a-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="69f4a-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="69f4a-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="69f4a-112">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="69f4a-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="69f4a-113">Vypne server sestavení MSBuild.</span><span class="sxs-lookup"><span data-stu-id="69f4a-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="69f4a-114">Vypne server sestavení Razor.</span><span class="sxs-lookup"><span data-stu-id="69f4a-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="69f4a-115">Ukončí server sestavení VB/C# Compiler.</span><span class="sxs-lookup"><span data-stu-id="69f4a-115">Shuts down the VB/C# compiler build server.</span></span>
