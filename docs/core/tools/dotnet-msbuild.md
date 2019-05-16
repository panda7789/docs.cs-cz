---
title: příkaz DotNet msbuild
description: Příkaz dotnet msbuild poskytuje přístup k příkazovému řádku nástroje MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: 983fae6f4ecf875da0b155a668009984b5df50de
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632030"
---
# <a name="dotnet-msbuild"></a>DotNet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet msbuild` -Sestavení projektu a všechny jeho závislosti.

## <a name="synopsis"></a>Souhrn

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Popis

`dotnet msbuild` Příkaz umožňuje přístup k plně funkční nástroj MSBuild.

Příkaz má přesně stejné funkce jako existující klient příkazového řádku MSBuild pro SDK – vizuální styl pouze aplikace project. Možnosti jsou stejné. Další informace o dostupných možnostech najdete v tématu [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference).

[Dotnet sestavení](dotnet-build.md) je ekvivalentní příkazu `dotnet msbuild -restore -target:Build`. `dotnet build` častěji se používá k sestavení projektů, ale `dotnet msbuild` vám dává větší kontrolu. Například pokud máte konkrétní cíl, který chcete spustit (bez spuštění cíl sestavení), pravděpodobně chcete použít `dotnet msbuild`.

## <a name="examples"></a>Příklady

* Sestavení projektu a jeho závislosti:

  ```console
  dotnet msbuild
  ```

* Sestavení projektu a jeho závislosti pomocí konfigurace vydané verze:

  ```console
  dotnet msbuild -p:Configuration=Release
  ```

* Spustit cíl publikování a publikování `osx.10.11-x64` identifikátorů RID:

  ```console
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* Zobrazit celý projekt s všechny cíle, které jsou součástí sady SDK:

  ```console
  dotnet msbuild -pp
  ```
