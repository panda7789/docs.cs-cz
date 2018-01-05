---
title: "příkaz msbuild DotNet - .NET Core rozhraní příkazového řádku"
description: "Příkaz msbuild dotnet poskytuje přístup k MSBuild příkazového řádku."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 682b49d44c0fb8242eeb3cb8bf4d158f73b4b9a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-msbuild"></a>msbuild DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet msbuild`-Sestavení projektu a všechny jeho závislé součásti.

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
