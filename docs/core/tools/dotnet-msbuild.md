---
title: příkaz DotNet msbuild
description: Příkaz dotnet msbuild poskytuje přístup k příkazovému řádku nástroje MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: f025b5b92e57c7b804b9bdd59c8b4a4a806796da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648695"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="744ec-103">DotNet msbuild</span><span class="sxs-lookup"><span data-stu-id="744ec-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="744ec-104">Název</span><span class="sxs-lookup"><span data-stu-id="744ec-104">Name</span></span>

<span data-ttu-id="744ec-105">`dotnet msbuild` -Sestavení projektu a všechny jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="744ec-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="744ec-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="744ec-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="744ec-107">Popis</span><span class="sxs-lookup"><span data-stu-id="744ec-107">Description</span></span>

<span data-ttu-id="744ec-108">`dotnet msbuild` Příkaz umožňuje přístup k plně funkční nástroj MSBuild.</span><span class="sxs-lookup"><span data-stu-id="744ec-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="744ec-109">Příkaz má přesně stejné funkce jako existující klient příkazového řádku MSBuild pro SDK – vizuální styl pouze aplikace project.</span><span class="sxs-lookup"><span data-stu-id="744ec-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style project only.</span></span> <span data-ttu-id="744ec-110">Možnosti jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="744ec-110">The options are all the same.</span></span> <span data-ttu-id="744ec-111">Další informace o dostupných možnostech najdete v tématu [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="744ec-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="744ec-112">[Dotnet sestavení](dotnet-build.md) je ekvivalentní příkazu `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="744ec-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="744ec-113">`dotnet build` častěji se používá k sestavení projektů, ale `dotnet msbuild` vám dává větší kontrolu.</span><span class="sxs-lookup"><span data-stu-id="744ec-113">`dotnet build` is more commonly used for building projects, but `dotnet msbuild` gives you more control.</span></span> <span data-ttu-id="744ec-114">Například pokud máte konkrétní cíl, který chcete spustit (bez spuštění cíl sestavení), pravděpodobně chcete použít `dotnet msbuild`.</span><span class="sxs-lookup"><span data-stu-id="744ec-114">For example, if you have a specific target you want to run (without running the build target), you probably want to use `dotnet msbuild`.</span></span>

## <a name="examples"></a><span data-ttu-id="744ec-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="744ec-115">Examples</span></span>

* <span data-ttu-id="744ec-116">Sestavení projektu a jeho závislosti:</span><span class="sxs-lookup"><span data-stu-id="744ec-116">Build a project and its dependencies:</span></span>

  ```console
  dotnet msbuild
  ```

* <span data-ttu-id="744ec-117">Sestavení projektu a jeho závislosti pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="744ec-117">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet msbuild -p:Configuration=Release
  ```

* <span data-ttu-id="744ec-118">Spustit cíl publikování a publikování `osx.10.11-x64` identifikátorů RID:</span><span class="sxs-lookup"><span data-stu-id="744ec-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```console
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="744ec-119">Zobrazit celý projekt s všechny cíle, které jsou součástí sady SDK:</span><span class="sxs-lookup"><span data-stu-id="744ec-119">See the whole project with all targets included by the SDK:</span></span>

  ```console
  dotnet msbuild -pp
  ```