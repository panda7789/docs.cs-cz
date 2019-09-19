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
# <a name="dotnet-msbuild"></a><span data-ttu-id="8dff1-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="8dff1-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8dff1-104">Name</span><span class="sxs-lookup"><span data-stu-id="8dff1-104">Name</span></span>

<span data-ttu-id="8dff1-105">`dotnet msbuild`– Sestavení projektu a všech jeho závislostí.</span><span class="sxs-lookup"><span data-stu-id="8dff1-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8dff1-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="8dff1-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="8dff1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8dff1-107">Description</span></span>

<span data-ttu-id="8dff1-108">`dotnet msbuild` Příkaz umožňuje přístup k plně funkčnímu nástroji MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8dff1-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="8dff1-109">Příkaz má stejné možnosti jako stávající klient příkazového řádku MSBuild pouze pro projekt ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="8dff1-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style project only.</span></span> <span data-ttu-id="8dff1-110">Možnosti jsou všechny stejné.</span><span class="sxs-lookup"><span data-stu-id="8dff1-110">The options are all the same.</span></span> <span data-ttu-id="8dff1-111">Další informace o dostupných možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="8dff1-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="8dff1-112">Příkaz [dotnet Build](dotnet-build.md) je ekvivalentní k `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="8dff1-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="8dff1-113">`dotnet build`je často používán pro vytváření projektů, ale `dotnet msbuild` poskytuje větší kontrolu.</span><span class="sxs-lookup"><span data-stu-id="8dff1-113">`dotnet build` is more commonly used for building projects, but `dotnet msbuild` gives you more control.</span></span> <span data-ttu-id="8dff1-114">Například pokud máte konkrétní cíl, který chcete spustit (bez spuštění cíle sestavení), budete pravděpodobně chtít použít `dotnet msbuild`.</span><span class="sxs-lookup"><span data-stu-id="8dff1-114">For example, if you have a specific target you want to run (without running the build target), you probably want to use `dotnet msbuild`.</span></span>

## <a name="examples"></a><span data-ttu-id="8dff1-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="8dff1-115">Examples</span></span>

* <span data-ttu-id="8dff1-116">Sestavení projektu a jeho závislostí:</span><span class="sxs-lookup"><span data-stu-id="8dff1-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="8dff1-117">Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="8dff1-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* <span data-ttu-id="8dff1-118">Spusťte cíl publikování a publikování pro `osx.10.11-x64` identifikátor RID:</span><span class="sxs-lookup"><span data-stu-id="8dff1-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="8dff1-119">Zobrazit celý projekt se všemi cíli, které jsou součástí sady SDK:</span><span class="sxs-lookup"><span data-stu-id="8dff1-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -pp
  ```
