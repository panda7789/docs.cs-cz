---
title: dotnet msbuild, příkaz
description: Příkaz dotnet msbuild poskytuje přístup k příkazovému řádku MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 88e85868e2d7de564b2e4c90ce6e78bde4cb350e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463625"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="1c2a3-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="1c2a3-103">dotnet msbuild</span></span>

<span data-ttu-id="1c2a3-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="1c2a3-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1c2a3-105">Název</span><span class="sxs-lookup"><span data-stu-id="1c2a3-105">Name</span></span>

<span data-ttu-id="1c2a3-106">`dotnet msbuild`- Vytvoří projekt a všechny jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="1c2a3-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1c2a3-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="1c2a3-107">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="1c2a3-108">Popis</span><span class="sxs-lookup"><span data-stu-id="1c2a3-108">Description</span></span>

<span data-ttu-id="1c2a3-109">Příkaz `dotnet msbuild` umožňuje přístup k plně funkční MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1c2a3-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="1c2a3-110">Příkaz má přesně stejné možnosti jako existující klient příkazového řádku MSBuild pouze pro projekty ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="1c2a3-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="1c2a3-111">Možnosti jsou všechny stejné.</span><span class="sxs-lookup"><span data-stu-id="1c2a3-111">The options are all the same.</span></span> <span data-ttu-id="1c2a3-112">Další informace o dostupných možnostech naleznete v [odkazu na příkazový řádek MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="1c2a3-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="1c2a3-113">Příkaz [sestavení dotnet](dotnet-build.md) je `dotnet msbuild -restore -target:Build`ekvivalentní .</span><span class="sxs-lookup"><span data-stu-id="1c2a3-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="1c2a3-114">[dotnet sestavení](dotnet-build.md) se běžně používá pro vytváření projektů, ale protože vždy `dotnet msbuild` spustí cíl sestavení, můžete použít, když nechcete sestavit projekt.</span><span class="sxs-lookup"><span data-stu-id="1c2a3-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="1c2a3-115">Pokud máte například konkrétní cíl, který chcete spustit bez `dotnet msbuild` sestavení projektu, použijte a zadejte cíl.</span><span class="sxs-lookup"><span data-stu-id="1c2a3-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="1c2a3-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="1c2a3-116">Examples</span></span>

- <span data-ttu-id="1c2a3-117">Sestavení projektu a jeho závislostí:</span><span class="sxs-lookup"><span data-stu-id="1c2a3-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="1c2a3-118">Sestavení projektu a jeho závislostí pomocí konfigurace verze:</span><span class="sxs-lookup"><span data-stu-id="1c2a3-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="1c2a3-119">Spusťte cíl publikování `osx.10.11-x64` a publikujte pro RID:</span><span class="sxs-lookup"><span data-stu-id="1c2a3-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="1c2a3-120">Podívejte se na celý projekt se všemi cíli zahrnutými do sady SDK:</span><span class="sxs-lookup"><span data-stu-id="1c2a3-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
