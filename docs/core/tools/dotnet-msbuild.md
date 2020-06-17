---
title: dotnet MSBuild – příkaz
description: Příkaz dotnet MSBuild poskytuje přístup k příkazovému řádku MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803178"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

## <a name="name"></a>Name

`dotnet msbuild`– Sestavení projektu a všech jeho závislostí. Poznámka: Pokud existuje více, může být nutné zadat soubor řešení nebo projektu.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a>Popis

`dotnet msbuild`Příkaz umožňuje přístup k plně funkčnímu nástroji MSBuild.

Příkaz má stejné možnosti jako stávající klient příkazového řádku MSBuild jenom pro projekty ve stylu sady SDK. Možnosti jsou všechny stejné. Další informace o dostupných možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

Příkaz [dotnet Build](dotnet-build.md) je ekvivalentní k `dotnet msbuild -restore` . Pokud nechcete sestavit projekt a máte konkrétní cíl, který chcete spustit, použijte `dotnet build` nebo `dotnet msbuild` a zadejte cíl.

## <a name="examples"></a>Příklady

- Sestavení projektu a jeho závislostí:

  ```dotnetcli
  dotnet msbuild
  ```

- Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- Spusťte cíl publikování a publikování pro `osx.10.11-x64` identifikátor RID:

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- Zobrazit celý projekt se všemi cíli, které jsou součástí sady SDK:

  ```dotnetcli
  dotnet msbuild -preprocess
  dotnet msbuild -preprocess:<fileName>.xml
  ```
