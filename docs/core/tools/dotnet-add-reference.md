---
title: DotNet – přidat odkaz na – příkaz
description: Příkaz dotnet add příkaz odkaz poskytuje vhodnou možnost pro přidání odkazů typu projekt na projekt.
ms.date: 04/24/2019
ms.openlocfilehash: f33a379534dca88133babbb5ca78bca614e441c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755190"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="913a7-103">DotNet – přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="913a7-103">dotnet-add reference</span></span>

<span data-ttu-id="913a7-104">**Tento článek se týká: ✓** .NET Core 1.x sady SDK a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="913a7-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="913a7-105">Name</span><span class="sxs-lookup"><span data-stu-id="913a7-105">Name</span></span>

<span data-ttu-id="913a7-106">`dotnet add reference` -Přidá odkazy typu projekt projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="913a7-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="913a7-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="913a7-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="913a7-108">Popis</span><span class="sxs-lookup"><span data-stu-id="913a7-108">Description</span></span>

<span data-ttu-id="913a7-109">`dotnet add reference` Příkaz poskytuje vhodnou možnost přidat odkazy na projekt do projektu.</span><span class="sxs-lookup"><span data-stu-id="913a7-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="913a7-110">Po spuštění příkazu [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) prvky jsou přidány do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="913a7-110">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="913a7-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="913a7-111">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="913a7-112">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="913a7-112">Specifies the project file.</span></span> <span data-ttu-id="913a7-113">Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.</span><span class="sxs-lookup"><span data-stu-id="913a7-113">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="913a7-114">Chcete-li přidat odkazuje na projekt na projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="913a7-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="913a7-115">Zadejte jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="913a7-115">Specify one or more projects.</span></span> <span data-ttu-id="913a7-116">[Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systémech založené na systému Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="913a7-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="913a7-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="913a7-117">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="913a7-118">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="913a7-118">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="913a7-119">Přidá odkazy na projekt jenom při cílení na konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="913a7-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="913a7-120">Příklady</span><span class="sxs-lookup"><span data-stu-id="913a7-120">Examples</span></span>

* <span data-ttu-id="913a7-121">Přidáte odkaz na projekt:</span><span class="sxs-lookup"><span data-stu-id="913a7-121">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="913a7-122">Přidání více odkazů projektu na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="913a7-122">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="913a7-123">Přidání více odkazů projektu pomocí vzoru podpory zástupných znaků v systému Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="913a7-123">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```