---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179986"
---
> [!NOTE]
> <span data-ttu-id="f3a6c-101">Počínaje rozhraním .NET Core 2,0 není nutné spouštět [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) , protože se spouští implicitně všemi příkazy, které vyžadují obnovení, například `dotnet build` a `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="f3a6c-101">Starting with .NET Core 2.0, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet build` and `dotnet run`.</span></span> <span data-ttu-id="f3a6c-102">V některých scénářích je stále platný příkaz, kde provede explicitní obnovení smysl, jako je například [průběžná integrace sestavení v Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, která potřebují explicitně řídit čas, kdy k obnovení dochází.</span><span class="sxs-lookup"><span data-stu-id="f3a6c-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
>
> <span data-ttu-id="f3a6c-103">Tento příkaz také podporuje možnosti `dotnet restore`, pokud jsou předány dlouhé formuláře (například `--source`).</span><span class="sxs-lookup"><span data-stu-id="f3a6c-103">This command also supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="f3a6c-104">Možnosti krátké formy, například `-s`, nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="f3a6c-104">Short form options, such as `-s`, are not supported.</span></span>
