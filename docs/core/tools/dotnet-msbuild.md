---
title: dotnet msbuild, příkaz
description: Příkaz dotnet msbuild poskytuje přístup k příkazovému řádku MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 88e85868e2d7de564b2e4c90ce6e78bde4cb350e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463625"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Název

`dotnet msbuild`- Vytvoří projekt a všechny jeho závislosti.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

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
