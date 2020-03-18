---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72179986"
---
> [!NOTE]
> <span data-ttu-id="0583f-101">Počínaje rozhraním .NET Core 2.0 není [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) nutné spouštět, protože je spuštěno implicitně všemi `dotnet build` příkazy, které vyžadují obnovení, například a `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="0583f-101">Starting with .NET Core 2.0, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet build` and `dotnet run`.</span></span> <span data-ttu-id="0583f-102">Je to stále platný příkaz v určitých scénářích, kde dělá explicitní obnovení dává smysl, jako je [například průběžné integrace sestavení ve službě Azure DevOps](/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které je třeba explicitně řídit čas, kdy dojde k obnovení.</span><span class="sxs-lookup"><span data-stu-id="0583f-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
>
> <span data-ttu-id="0583f-103">Tento příkaz také `dotnet restore` podporuje možnosti při předání v `--source`dlouhé podobě (například ).</span><span class="sxs-lookup"><span data-stu-id="0583f-103">This command also supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="0583f-104">Možnosti krátkého `-s`formuláře, například , nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="0583f-104">Short form options, such as `-s`, are not supported.</span></span>
