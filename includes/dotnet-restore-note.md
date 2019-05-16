---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632119"
---
> [!NOTE]
> <span data-ttu-id="27906-101">Počínaje .NET Core 2.0 SDK, není nutné spustit [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) vzhledem k tomu, že je implicitně spouštět všechny příkazy, které vyžadují obnovení pravděpodobnější, jako například `dotnet new`, `dotnet build` a `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="27906-101">Starting with .NET Core 2.0 SDK, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build` and `dotnet run`.</span></span>
> <span data-ttu-id="27906-102">Je stále platný příkaz v některých scénářích, kde to explicitního obnovení dává smysl, jako například [sestavení kontinuální integrace ve službě Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které je nutné explicitně určit čas, kdy dojde k obnovení.</span><span class="sxs-lookup"><span data-stu-id="27906-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
