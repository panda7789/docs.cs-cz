---
title: dotnet msbuild, příkaz
description: Příkaz dotnet msbuild poskytuje přístup k příkazovému řádku MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503679"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet msbuild`- Vytvoří projekt a všechny jeho závislosti.

## <a name="synopsis"></a>Synopse

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Popis

Příkaz `dotnet msbuild` umožňuje přístup k plně funkční MSBuild.

Příkaz má přesně stejné možnosti jako existující klient příkazového řádku MSBuild pouze pro projekty ve stylu sady SDK. Možnosti jsou všechny stejné. Další informace o dostupných možnostech naleznete v [odkazu na příkazový řádek MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

Příkaz [sestavení dotnet](dotnet-build.md) je `dotnet msbuild -restore -target:Build`ekvivalentní . [dotnet sestavení](dotnet-build.md) se běžně používá pro vytváření projektů, ale protože vždy `dotnet msbuild` spustí cíl sestavení, můžete použít, když nechcete sestavit projekt. Pokud máte například konkrétní cíl, který chcete spustit bez `dotnet msbuild` sestavení projektu, použijte a zadejte cíl.

## <a name="examples"></a>Příklady

- Sestavení projektu a jeho závislostí:

  ```dotnetcli
  dotnet msbuild
  ```

- Sestavení projektu a jeho závislostí pomocí konfigurace verze:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- Spusťte cíl publikování `osx.10.11-x64` a publikujte pro RID:

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- Podívejte se na celý projekt se všemi cíli zahrnutými do sady SDK:

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
