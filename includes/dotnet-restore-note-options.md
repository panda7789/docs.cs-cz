---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72179986"
---
> [!NOTE]
> Počínaje rozhraním .NET Core 2.0 není [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) nutné spouštět, protože je spuštěno implicitně všemi `dotnet build` příkazy, které vyžadují obnovení, například a `dotnet run`. Je to stále platný příkaz v určitých scénářích, kde dělá explicitní obnovení dává smysl, jako je [například průběžné integrace sestavení ve službě Azure DevOps](/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které je třeba explicitně řídit čas, kdy dojde k obnovení.
>
> Tento příkaz také `dotnet restore` podporuje možnosti při předání v `--source`dlouhé podobě (například ). Možnosti krátkého `-s`formuláře, například , nejsou podporovány.
