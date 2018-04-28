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
# <a name="dotnet-msbuild"></a><span data-ttu-id="493eb-103">msbuild DotNet.</span><span class="sxs-lookup"><span data-stu-id="493eb-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="493eb-104">Název</span><span class="sxs-lookup"><span data-stu-id="493eb-104">Name</span></span>

<span data-ttu-id="493eb-105">`dotnet msbuild` -Sestavení projektu a všechny jeho závislé součásti.</span><span class="sxs-lookup"><span data-stu-id="493eb-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="493eb-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="493eb-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="493eb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="493eb-107">Description</span></span>

<span data-ttu-id="493eb-108">`dotnet msbuild` Příkaz umožňuje přístup k plně funkční MSBuild.</span><span class="sxs-lookup"><span data-stu-id="493eb-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="493eb-109">Příkaz má přesný stejné schopnosti jako existující klient nástroje MSBuild příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="493eb-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="493eb-110">Možnosti jsou všechny byly stejné.</span><span class="sxs-lookup"><span data-stu-id="493eb-110">The options are all the same.</span></span> <span data-ttu-id="493eb-111">Použití [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) získávat informace o dostupných možností.</span><span class="sxs-lookup"><span data-stu-id="493eb-111">Use the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) to obtain information on the available options.</span></span> 

## <a name="examples"></a><span data-ttu-id="493eb-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="493eb-112">Examples</span></span>

<span data-ttu-id="493eb-113">Sestavte projekt a jeho závislé součásti:</span><span class="sxs-lookup"><span data-stu-id="493eb-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="493eb-114">Sestavte projekt a jeho závislosti pomocí konfigurace verze:</span><span class="sxs-lookup"><span data-stu-id="493eb-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="493eb-115">Spusťte cíl publikování a publikování `osx.10.11-x64` identifikátorů RID:</span><span class="sxs-lookup"><span data-stu-id="493eb-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="493eb-116">V části celý projekt s všechny cíle zahrnuté SDK:</span><span class="sxs-lookup"><span data-stu-id="493eb-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`
