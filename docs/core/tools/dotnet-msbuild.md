---
title: dotnet MSBuild – příkaz
description: Příkaz dotnet MSBuild poskytuje přístup k příkazovému řádku MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: b83f1272cdd4c5fcdb6b1e34aef7692e9acc01cd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117698"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet msbuild`– Sestavení projektu a všech jeho závislostí.

## <a name="synopsis"></a>Stručný obsah

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Popis

`dotnet msbuild` Příkaz umožňuje přístup k plně funkčnímu nástroji MSBuild.

Příkaz má stejné možnosti jako stávající klient příkazového řádku MSBuild pouze pro projekt ve stylu sady SDK. Možnosti jsou všechny stejné. Další informace o dostupných možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

Příkaz [dotnet Build](dotnet-build.md) je ekvivalentní k `dotnet msbuild -restore -target:Build`. `dotnet build`je často používán pro vytváření projektů, ale `dotnet msbuild` poskytuje větší kontrolu. Například pokud máte konkrétní cíl, který chcete spustit (bez spuštění cíle sestavení), budete pravděpodobně chtít použít `dotnet msbuild`.

## <a name="examples"></a>Příklady

* Sestavení projektu a jeho závislostí:

  ```dotnetcli
  dotnet msbuild
  ```

* Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* Spusťte cíl publikování a publikování pro `osx.10.11-x64` identifikátor RID:

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* Zobrazit celý projekt se všemi cíli, které jsou součástí sady SDK:

  ```dotnetcli
  dotnet msbuild -pp
  ```
