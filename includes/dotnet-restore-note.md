---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632119"
---
> [!NOTE]
> <span data-ttu-id="118cd-101">Počínaje sadou .NET Core 2.0 SDK není [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) nutné spouštět, protože je spuštěna implicitně všemi `dotnet new` `dotnet build` příkazy, které vyžadují obnovení, například . `dotnet run`</span><span class="sxs-lookup"><span data-stu-id="118cd-101">Starting with .NET Core 2.0 SDK, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build` and `dotnet run`.</span></span>
> <span data-ttu-id="118cd-102">Je to stále platný příkaz v určitých scénářích, kde dělá explicitní obnovení dává smysl, jako je [například průběžné integrace sestavení ve službě Azure DevOps](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které je třeba explicitně řídit čas, kdy dojde k obnovení.</span><span class="sxs-lookup"><span data-stu-id="118cd-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
