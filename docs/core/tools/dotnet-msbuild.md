---
title: příkaz msbuild DotNet - .NET Core rozhraní příkazového řádku
description: Příkaz msbuild dotnet poskytuje přístup k MSBuild příkazového řádku.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 58aac2a5314758b8711c0b014154022168fb671c
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696842"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="da897-103">msbuild DotNet.</span><span class="sxs-lookup"><span data-stu-id="da897-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="da897-104">Název</span><span class="sxs-lookup"><span data-stu-id="da897-104">Name</span></span>

<span data-ttu-id="da897-105">`dotnet msbuild` -Sestavení projektu a všechny jeho závislé součásti.</span><span class="sxs-lookup"><span data-stu-id="da897-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="da897-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="da897-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="da897-107">Popis</span><span class="sxs-lookup"><span data-stu-id="da897-107">Description</span></span>

<span data-ttu-id="da897-108">`dotnet msbuild` Příkaz umožňuje přístup k plně funkční MSBuild.</span><span class="sxs-lookup"><span data-stu-id="da897-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="da897-109">Příkaz má přesný stejné schopnosti jako existující klient nástroje MSBuild příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="da897-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="da897-110">Možnosti jsou všechny byly stejné.</span><span class="sxs-lookup"><span data-stu-id="da897-110">The options are all the same.</span></span> <span data-ttu-id="da897-111">Další informace o dostupných možnostech najdete v tématu [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="da897-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="examples"></a><span data-ttu-id="da897-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="da897-112">Examples</span></span>

<span data-ttu-id="da897-113">Sestavte projekt a jeho závislé součásti:</span><span class="sxs-lookup"><span data-stu-id="da897-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="da897-114">Sestavte projekt a jeho závislosti pomocí konfigurace verze:</span><span class="sxs-lookup"><span data-stu-id="da897-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="da897-115">Spusťte cíl publikování a publikování `osx.10.11-x64` identifikátorů RID:</span><span class="sxs-lookup"><span data-stu-id="da897-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="da897-116">V části celý projekt s všechny cíle zahrnuté SDK:</span><span class="sxs-lookup"><span data-stu-id="da897-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`
