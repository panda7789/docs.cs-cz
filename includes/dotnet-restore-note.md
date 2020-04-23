---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102736"
---
<span data-ttu-id="50b55-101">Není [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) nutné spustit, protože je spuštěn implicitně všechny příkazy, které vyžadují obnovení `dotnet new` `dotnet build`dojít, například , `dotnet run`, `dotnet test`, `dotnet publish`a `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="50b55-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="50b55-102">Chcete-li zakázat `--no-restore` implicitní obnovení, použijte možnost.</span><span class="sxs-lookup"><span data-stu-id="50b55-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="50b55-103">`dotnet restore` Příkaz je stále užitečné v určitých scénářích, kde explicitní obnovení dává smysl, jako je [například průběžné integrace sestavení ve službě Azure DevOps](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které je třeba explicitně řídit, když dojde k obnovení.</span><span class="sxs-lookup"><span data-stu-id="50b55-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="50b55-104">Informace o tom, jak spravovat informační kanály NuGet, naleznete v [ `dotnet restore` dokumentaci](../docs/core/tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="50b55-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
