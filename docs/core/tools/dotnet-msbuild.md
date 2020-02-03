---
title: dotnet MSBuild – příkaz
description: Příkaz dotnet MSBuild poskytuje přístup k příkazovému řádku MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: dae1e9f0ca355166d41c11fbafb80c7c9fb29748
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733197"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet msbuild` – sestavení projektu a všech jeho závislostí.

## <a name="synopsis"></a>Stručný obsah

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Popis

Příkaz `dotnet msbuild` umožňuje přístup k plně funkčnímu nástroji MSBuild.

Příkaz má stejné možnosti jako stávající klient příkazového řádku MSBuild jenom pro projekty ve stylu sady SDK. Možnosti jsou všechny stejné. Další informace o dostupných možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

Příkaz [dotnet Build](dotnet-build.md) je ekvivalentní `dotnet msbuild -restore -target:Build`. [sestavení dotnet](dotnet-build.md) je častěji použito pro sestavování projektů, ale vzhledem k tomu, že vždy spustí cíl sestavení, můžete použít `dotnet msbuild`, pokud nechcete sestavit projekt. Například pokud máte konkrétní cíl, který chcete spustit bez sestavení projektu, použijte `dotnet msbuild` a zadejte cíl.

## <a name="examples"></a>Příklady

* Sestavení projektu a jeho závislostí:

  ```dotnetcli
  dotnet msbuild
  ```

* Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

* Spusťte cíl publikování a publikování pro `osx.10.11-x64` RID:

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

* Zobrazit celý projekt se všemi cíli, které jsou součástí sady SDK:

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
