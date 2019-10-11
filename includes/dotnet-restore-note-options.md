---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179986"
---
> [!NOTE]
> Počínaje rozhraním .NET Core 2,0 není nutné spouštět [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) , protože se spouští implicitně všemi příkazy, které vyžadují obnovení, například `dotnet build` a `dotnet run`. V některých scénářích je stále platný příkaz, kde provede explicitní obnovení smysl, jako je například [průběžná integrace sestavení v Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, která potřebují explicitně řídit čas, kdy k obnovení dochází.
>
> Tento příkaz také podporuje možnosti `dotnet restore`, pokud jsou předány dlouhé formuláře (například `--source`). Možnosti krátké formy, například `-s`, nejsou podporovány.
