---
ms.openlocfilehash: 6c04437c2a211b244e6c5eda0893b267c59668e9
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102763"
---
Není [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) nutné spustit, protože je spuštěn implicitně všechny příkazy, které vyžadují obnovení `dotnet new` `dotnet build`dojít, například , `dotnet run`, `dotnet test`, `dotnet publish`a `dotnet pack`. Chcete-li zakázat `--no-restore` implicitní obnovení, použijte možnost.

`dotnet restore` Příkaz je stále užitečné v určitých scénářích, kde explicitní obnovení dává smysl, jako je [například průběžné integrace sestavení ve službě Azure DevOps](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které je třeba explicitně řídit, když dojde k obnovení.

Informace o tom, jak spravovat informační kanály NuGet, naleznete v [ `dotnet restore` dokumentaci](../docs/core/tools/dotnet-restore.md).

Tento příkaz `dotnet restore` podporuje možnosti při předání v `--source`dlouhé matné podobě (například ). Možnosti krátkého `-s`formuláře, například , nejsou podporovány.
