---
ms.openlocfilehash: 319aca3c5edea7e7bb64fe9081d9f23d3012ff9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648620"
---
> [!NOTE]
> <span data-ttu-id="66863-101">Od verze rozhraní .NET Core 2.0, není nutné spustit [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) vzhledem k tomu, když ji spustí implicitně všechny příkazy, jako například `dotnet build` a `dotnet run`, které vyžadují obnovení každý.</span><span class="sxs-lookup"><span data-stu-id="66863-101">Starting with .NET Core 2.0, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands, such as `dotnet build` and `dotnet run`, that require a restore to occur.</span></span> <span data-ttu-id="66863-102">Je stále platný příkaz v některých scénářích, kde to explicitního obnovení dává smysl, jako například [sestavení kontinuální integrace ve službě Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které je nutné explicitně určit čas, kdy dojde k obnovení.</span><span class="sxs-lookup"><span data-stu-id="66863-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
>
> <span data-ttu-id="66863-103">Tento příkaz také podporuje `dotnet restore` možnosti při předání v dlouhých úseků (například `--source`).</span><span class="sxs-lookup"><span data-stu-id="66863-103">This command also supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="66863-104">Krátký formulář možnosti, jako například `-s`, nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="66863-104">Short form options, such as `-s`, are not supported.</span></span>