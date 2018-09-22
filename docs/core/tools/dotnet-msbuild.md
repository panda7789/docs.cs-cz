---
title: příkaz DotNet msbuild – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet msbuild poskytuje přístup k příkazovému řádku nástroje MSBuild.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 76165590478b0e76d19d546c87e012da4716b6db
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46578893"
---
# <a name="dotnet-msbuild"></a>DotNet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet msbuild` -Sestavení projektu a všechny jeho závislosti.

## <a name="synopsis"></a>Souhrn

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Popis

`dotnet msbuild` Příkaz umožňuje přístup k plně funkční nástroj MSBuild.

Příkaz má přesně stejné funkce jako existující klient příkazového řádku MSBuild. Možnosti jsou stejné. Další informace o dostupných možnostech najdete v tématu [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference).

## <a name="examples"></a>Příklady

Sestavení projektu a jeho závislosti:

`dotnet msbuild`

Sestavení projektu a jeho závislosti pomocí konfigurace vydané verze:

`dotnet msbuild -p:Configuration=Release`

Spustit cíl publikování a publikování `osx.10.11-x64` identifikátorů RID:

`dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64`

Zobrazit celý projekt s všechny cíle, které jsou součástí sady SDK:

`dotnet msbuild -pp`
