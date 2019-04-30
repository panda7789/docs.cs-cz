---
ms.openlocfilehash: 95fd83d517096eecb69e57f15c8c70f497a290b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646936"
---
> [!NOTE]
> Počínaje .NET Core 2.0 SDK, není nutné spustit [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) vzhledem k tomu, že je implicitně spouštět všechny příkazy, které vyžadují obnovení pravděpodobnější, jako například `dotnet new`, `dotnet build` a `dotnet run`.
> Je stále platný příkaz v některých scénářích, kde to explicitního obnovení dává smysl, jako například [sestavení kontinuální integrace ve službě Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) nebo v systémech sestavení, které je nutné explicitně určit čas, kdy dojde k obnovení.