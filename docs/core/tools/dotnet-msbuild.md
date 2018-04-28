---
title: příkaz msbuild DotNet - .NET Core rozhraní příkazového řádku
description: Příkaz msbuild dotnet poskytuje přístup k MSBuild příkazového řádku.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 9e6f8b3063b4cd2a3a36cae8839d6f83e0466e03
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-msbuild"></a>msbuild DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet msbuild` -Sestavení projektu a všechny jeho závislé součásti.

## <a name="synopsis"></a>Stručný obsah

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Popis

`dotnet msbuild` Příkaz umožňuje přístup k plně funkční MSBuild.

Příkaz má přesný stejné schopnosti jako existující klient nástroje MSBuild příkazového řádku. Možnosti jsou všechny byly stejné. Použití [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) získávat informace o dostupných možností. 

## <a name="examples"></a>Příklady

Sestavte projekt a jeho závislé součásti:

`dotnet msbuild`

Sestavte projekt a jeho závislosti pomocí konfigurace verze:

`dotnet msbuild /p:Configuration=Release`

Spusťte cíl publikování a publikování `osx.10.11-x64` identifikátorů RID:

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

V části celý projekt s všechny cíle zahrnuté SDK:

`dotnet msbuild /pp`
