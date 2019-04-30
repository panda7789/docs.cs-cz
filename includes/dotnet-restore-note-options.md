---
ms.openlocfilehash: 319aca3c5edea7e7bb64fe9081d9f23d3012ff9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648620"
---
> [!NOTE]
> Od verze rozhraní .NET Core 2.0, není nutné spustit [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) vzhledem k tomu, když ji spustí implicitně všechny příkazy, jako například `dotnet build` a `dotnet run`, které vyžadují obnovení každý. Je stále platný příkaz v některých scénářích, kde to explicitního obnovení dává smysl, jako například [sestavení kontinuální integrace ve službě Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které je nutné explicitně určit čas, kdy dojde k obnovení.
>
> Tento příkaz také podporuje `dotnet restore` možnosti při předání v dlouhých úseků (například `--source`). Krátký formulář možnosti, jako například `-s`, nejsou podporovány.