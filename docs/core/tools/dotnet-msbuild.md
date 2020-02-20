---
title: dotnet MSBuild – příkaz
description: Příkaz dotnet MSBuild poskytuje přístup k příkazovému řádku MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503679"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="9d921-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="9d921-103">dotnet msbuild</span></span>

<span data-ttu-id="9d921-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="9d921-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9d921-105">Název</span><span class="sxs-lookup"><span data-stu-id="9d921-105">Name</span></span>

<span data-ttu-id="9d921-106">`dotnet msbuild` – sestavení projektu a všech jeho závislostí.</span><span class="sxs-lookup"><span data-stu-id="9d921-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9d921-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="9d921-107">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="9d921-108">Popis</span><span class="sxs-lookup"><span data-stu-id="9d921-108">Description</span></span>

<span data-ttu-id="9d921-109">Příkaz `dotnet msbuild` umožňuje přístup k plně funkčnímu nástroji MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9d921-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="9d921-110">Příkaz má stejné možnosti jako stávající klient příkazového řádku MSBuild jenom pro projekty ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="9d921-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="9d921-111">Možnosti jsou všechny stejné.</span><span class="sxs-lookup"><span data-stu-id="9d921-111">The options are all the same.</span></span> <span data-ttu-id="9d921-112">Další informace o dostupných možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="9d921-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="9d921-113">Příkaz [dotnet Build](dotnet-build.md) je ekvivalentní `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="9d921-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="9d921-114">[sestavení dotnet](dotnet-build.md) je častěji použito pro sestavování projektů, ale vzhledem k tomu, že vždy spustí cíl sestavení, můžete použít `dotnet msbuild`, pokud nechcete sestavit projekt.</span><span class="sxs-lookup"><span data-stu-id="9d921-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="9d921-115">Například pokud máte konkrétní cíl, který chcete spustit bez sestavení projektu, použijte `dotnet msbuild` a zadejte cíl.</span><span class="sxs-lookup"><span data-stu-id="9d921-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="9d921-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="9d921-116">Examples</span></span>

- <span data-ttu-id="9d921-117">Sestavení projektu a jeho závislostí:</span><span class="sxs-lookup"><span data-stu-id="9d921-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="9d921-118">Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="9d921-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="9d921-119">Spusťte cíl publikování a publikování pro `osx.10.11-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="9d921-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="9d921-120">Zobrazit celý projekt se všemi cíli, které jsou součástí sady SDK:</span><span class="sxs-lookup"><span data-stu-id="9d921-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
