---
title: dotnet MSBuild – příkaz
description: Příkaz dotnet MSBuild poskytuje přístup k příkazovému řádku MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: dae1e9f0ca355166d41c11fbafb80c7c9fb29748
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733197"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="b6033-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="b6033-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b6033-104">Název</span><span class="sxs-lookup"><span data-stu-id="b6033-104">Name</span></span>

<span data-ttu-id="b6033-105">`dotnet msbuild` – sestavení projektu a všech jeho závislostí.</span><span class="sxs-lookup"><span data-stu-id="b6033-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b6033-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="b6033-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="b6033-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b6033-107">Description</span></span>

<span data-ttu-id="b6033-108">Příkaz `dotnet msbuild` umožňuje přístup k plně funkčnímu nástroji MSBuild.</span><span class="sxs-lookup"><span data-stu-id="b6033-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="b6033-109">Příkaz má stejné možnosti jako stávající klient příkazového řádku MSBuild jenom pro projekty ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="b6033-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="b6033-110">Možnosti jsou všechny stejné.</span><span class="sxs-lookup"><span data-stu-id="b6033-110">The options are all the same.</span></span> <span data-ttu-id="b6033-111">Další informace o dostupných možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="b6033-111">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="b6033-112">Příkaz [dotnet Build](dotnet-build.md) je ekvivalentní `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="b6033-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="b6033-113">[sestavení dotnet](dotnet-build.md) je častěji použito pro sestavování projektů, ale vzhledem k tomu, že vždy spustí cíl sestavení, můžete použít `dotnet msbuild`, pokud nechcete sestavit projekt.</span><span class="sxs-lookup"><span data-stu-id="b6033-113">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="b6033-114">Například pokud máte konkrétní cíl, který chcete spustit bez sestavení projektu, použijte `dotnet msbuild` a zadejte cíl.</span><span class="sxs-lookup"><span data-stu-id="b6033-114">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="b6033-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="b6033-115">Examples</span></span>

* <span data-ttu-id="b6033-116">Sestavení projektu a jeho závislostí:</span><span class="sxs-lookup"><span data-stu-id="b6033-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="b6033-117">Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="b6033-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

* <span data-ttu-id="b6033-118">Spusťte cíl publikování a publikování pro `osx.10.11-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="b6033-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="b6033-119">Zobrazit celý projekt se všemi cíli, které jsou součástí sady SDK:</span><span class="sxs-lookup"><span data-stu-id="b6033-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
