---
title: příkaz DotNet server sestavení – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet sestavení serveru komunikuje se servery tím, že sestavení.
author: mairaw
ms.author: mairaw
ms.date: 07/02/2018
ms.openlocfilehash: 1c59c85f246b79c7e2552f704db5b4f076f9b502
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404330"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="05f8d-103">DotNet – server sestavení</span><span class="sxs-lookup"><span data-stu-id="05f8d-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="05f8d-104">Název</span><span class="sxs-lookup"><span data-stu-id="05f8d-104">Name</span></span>

<span data-ttu-id="05f8d-105">`dotnet build-server` -Komunikuje se servery pro spuštění sestavení.</span><span class="sxs-lookup"><span data-stu-id="05f8d-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="05f8d-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="05f8d-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="05f8d-107">Příkazy</span><span class="sxs-lookup"><span data-stu-id="05f8d-107">Commands</span></span>

`shutdown`

<span data-ttu-id="05f8d-108">Vypne sestavovací servery, které jsou spuštěny z dotnet.</span><span class="sxs-lookup"><span data-stu-id="05f8d-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="05f8d-109">Ve výchozím nastavení jsou všechny servery vypnout.</span><span class="sxs-lookup"><span data-stu-id="05f8d-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="05f8d-110">Možnosti</span><span class="sxs-lookup"><span data-stu-id="05f8d-110">Options</span></span>

`-h|--help`

<span data-ttu-id="05f8d-111">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="05f8d-111">Prints out a short help for the command.</span></span>

`--msbuild`

<span data-ttu-id="05f8d-112">Ukončí MSBuild serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="05f8d-112">Shuts down the MSBuild build server.</span></span>

`--razor`

<span data-ttu-id="05f8d-113">Server sestavení vypne syntaxi Razor.</span><span class="sxs-lookup"><span data-stu-id="05f8d-113">Shuts down the Razor build server.</span></span>

`--vbcscompiler`

<span data-ttu-id="05f8d-114">Vypne jazyce Visual Basic / server sestavení kompilátor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="05f8d-114">Shuts down the VB/C# compiler build server.</span></span>
