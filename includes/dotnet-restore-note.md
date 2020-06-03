---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102736"
---
Nemusíte spouštět [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) , protože se spouští implicitně všemi příkazy, které vyžadují obnovení, například `dotnet new` , `dotnet build` , `dotnet run` , `dotnet test` , `dotnet publish` a `dotnet pack` . Pokud chcete zakázat implicitní obnovení, použijte `--no-restore` možnost.

`dotnet restore`Příkaz je stále užitečný v některých scénářích, kde explicitní obnovení dává smysl, jako je například [průběžná integrace sestavení v Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které potřebují explicitně řídit, kdy dojde k obnovení.

Informace o tom, jak spravovat kanály NuGet, najdete v [ `dotnet restore` dokumentaci](../docs/core/tools/dotnet-restore.md).
