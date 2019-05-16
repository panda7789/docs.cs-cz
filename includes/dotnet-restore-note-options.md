---
ms.openlocfilehash: 497ac09e5c9a10470d3ae1932d7e3dc114d121dd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632021"
---
> [!NOTE]
> Od verze rozhraní .NET Core 2.0, není nutné spustit [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) vzhledem k tomu, když ji spustí implicitně všechny příkazy, jako například `dotnet build` a `dotnet run`, které vyžadují obnovení každý. Je stále platný příkaz v některých scénářích, kde to explicitního obnovení dává smysl, jako například [sestavení kontinuální integrace ve službě Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které je nutné explicitně určit čas, kdy dojde k obnovení.
>
> Tento příkaz také podporuje `dotnet restore` možnosti při předání v dlouhých úseků (například `--source`). Krátký formulář možnosti, jako například `-s`, nejsou podporovány.
