---
title: dotnet MSBuild – příkaz
description: Příkaz dotnet MSBuild poskytuje přístup k příkazovému řádku MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803178"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="c88ea-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="c88ea-103">dotnet msbuild</span></span>

<span data-ttu-id="c88ea-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="c88ea-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c88ea-105">Name</span><span class="sxs-lookup"><span data-stu-id="c88ea-105">Name</span></span>

<span data-ttu-id="c88ea-106">`dotnet msbuild`– Sestavení projektu a všech jeho závislostí.</span><span class="sxs-lookup"><span data-stu-id="c88ea-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span> <span data-ttu-id="c88ea-107">Poznámka: Pokud existuje více, může být nutné zadat soubor řešení nebo projektu.</span><span class="sxs-lookup"><span data-stu-id="c88ea-107">Note: A solution or project file may need to be specified if there are multiple.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c88ea-108">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="c88ea-108">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="c88ea-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c88ea-109">Description</span></span>

<span data-ttu-id="c88ea-110">`dotnet msbuild`Příkaz umožňuje přístup k plně funkčnímu nástroji MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c88ea-110">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="c88ea-111">Příkaz má stejné možnosti jako stávající klient příkazového řádku MSBuild jenom pro projekty ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="c88ea-111">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="c88ea-112">Možnosti jsou všechny stejné.</span><span class="sxs-lookup"><span data-stu-id="c88ea-112">The options are all the same.</span></span> <span data-ttu-id="c88ea-113">Další informace o dostupných možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="c88ea-113">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="c88ea-114">Příkaz [dotnet Build](dotnet-build.md) je ekvivalentní k `dotnet msbuild -restore` .</span><span class="sxs-lookup"><span data-stu-id="c88ea-114">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore`.</span></span> <span data-ttu-id="c88ea-115">Pokud nechcete sestavit projekt a máte konkrétní cíl, který chcete spustit, použijte `dotnet build` nebo `dotnet msbuild` a zadejte cíl.</span><span class="sxs-lookup"><span data-stu-id="c88ea-115">When you don't want to build the project and you have a specific target you want to run, use `dotnet build` or `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="c88ea-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="c88ea-116">Examples</span></span>

- <span data-ttu-id="c88ea-117">Sestavení projektu a jeho závislostí:</span><span class="sxs-lookup"><span data-stu-id="c88ea-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="c88ea-118">Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="c88ea-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="c88ea-119">Spusťte cíl publikování a publikování pro `osx.10.11-x64` identifikátor RID:</span><span class="sxs-lookup"><span data-stu-id="c88ea-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="c88ea-120">Zobrazit celý projekt se všemi cíli, které jsou součástí sady SDK:</span><span class="sxs-lookup"><span data-stu-id="c88ea-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  dotnet msbuild -preprocess:<fileName>.xml
  ```
