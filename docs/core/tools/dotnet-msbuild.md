---
title: příkaz DotNet msbuild – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet msbuild poskytuje přístup k příkazovému řádku nástroje MSBuild.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 76165590478b0e76d19d546c87e012da4716b6db
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583706"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="0b55b-103">DotNet msbuild</span><span class="sxs-lookup"><span data-stu-id="0b55b-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0b55b-104">Název</span><span class="sxs-lookup"><span data-stu-id="0b55b-104">Name</span></span>

<span data-ttu-id="0b55b-105">`dotnet msbuild` -Sestavení projektu a všechny jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="0b55b-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0b55b-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="0b55b-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="0b55b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0b55b-107">Description</span></span>

<span data-ttu-id="0b55b-108">`dotnet msbuild` Příkaz umožňuje přístup k plně funkční nástroj MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0b55b-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="0b55b-109">Příkaz má přesně stejné funkce jako existující klient příkazového řádku MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0b55b-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="0b55b-110">Možnosti jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="0b55b-110">The options are all the same.</span></span> <span data-ttu-id="0b55b-111">Další informace o dostupných možnostech najdete v tématu [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="0b55b-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="examples"></a><span data-ttu-id="0b55b-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="0b55b-112">Examples</span></span>

<span data-ttu-id="0b55b-113">Sestavení projektu a jeho závislosti:</span><span class="sxs-lookup"><span data-stu-id="0b55b-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="0b55b-114">Sestavení projektu a jeho závislosti pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="0b55b-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild -p:Configuration=Release`

<span data-ttu-id="0b55b-115">Spustit cíl publikování a publikování `osx.10.11-x64` identifikátorů RID:</span><span class="sxs-lookup"><span data-stu-id="0b55b-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="0b55b-116">Zobrazit celý projekt s všechny cíle, které jsou součástí sady SDK:</span><span class="sxs-lookup"><span data-stu-id="0b55b-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild -pp`
