---
title: příkaz msbuild DotNet - .NET Core rozhraní příkazového řádku
description: Příkaz msbuild dotnet poskytuje přístup k MSBuild příkazového řádku.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 58aac2a5314758b8711c0b014154022168fb671c
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696842"
---
# <a name="dotnet-msbuild"></a>msbuild DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet msbuild` -Sestavení projektu a všechny jeho závislé součásti.

## <a name="synopsis"></a>Stručný obsah

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Popis

`dotnet msbuild` Příkaz umožňuje přístup k plně funkční MSBuild.

Příkaz má přesný stejné schopnosti jako existující klient nástroje MSBuild příkazového řádku. Možnosti jsou všechny byly stejné. Další informace o dostupných možnostech najdete v tématu [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

## <a name="examples"></a>Příklady

Sestavte projekt a jeho závislé součásti:

`dotnet msbuild`

Sestavte projekt a jeho závislosti pomocí konfigurace verze:

`dotnet msbuild /p:Configuration=Release`

Spusťte cíl publikování a publikování `osx.10.11-x64` identifikátorů RID:

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

V části celý projekt s všechny cíle zahrnuté SDK:

`dotnet msbuild /pp`
