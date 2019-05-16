---
title: DotNet – přidat odkaz na – příkaz
description: Příkaz dotnet add příkaz odkaz poskytuje vhodnou možnost pro přidání odkazů typu projekt na projekt.
ms.date: 04/24/2019
ms.openlocfilehash: e90f95527d4f14c7851ccd8d30201daaaaefa2ae
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631942"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="a2f7f-103">DotNet – přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="a2f7f-103">dotnet-add reference</span></span>

<span data-ttu-id="a2f7f-104">**Tento článek se týká: ✓** .NET Core 1.x sady SDK a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="a2f7f-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="a2f7f-105">Name</span><span class="sxs-lookup"><span data-stu-id="a2f7f-105">Name</span></span>

<span data-ttu-id="a2f7f-106">`dotnet add reference` -Přidá odkazy typu projekt projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="a2f7f-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a2f7f-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="a2f7f-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="a2f7f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a2f7f-108">Description</span></span>

<span data-ttu-id="a2f7f-109">`dotnet add reference` Příkaz poskytuje vhodnou možnost přidat odkazy na projekt do projektu.</span><span class="sxs-lookup"><span data-stu-id="a2f7f-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="a2f7f-110">Po spuštění příkazu [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) prvky jsou přidány do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="a2f7f-110">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="a2f7f-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="a2f7f-111">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="a2f7f-112">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="a2f7f-112">Specifies the project file.</span></span> <span data-ttu-id="a2f7f-113">Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.</span><span class="sxs-lookup"><span data-stu-id="a2f7f-113">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="a2f7f-114">Chcete-li přidat odkazuje na projekt na projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="a2f7f-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="a2f7f-115">Zadejte jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="a2f7f-115">Specify one or more projects.</span></span> <span data-ttu-id="a2f7f-116">[Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systémech založené na systému Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="a2f7f-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="a2f7f-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a2f7f-117">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="a2f7f-118">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a2f7f-118">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a2f7f-119">Přidá odkazy na projekt jenom při cílení na konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a2f7f-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="a2f7f-120">Příklady</span><span class="sxs-lookup"><span data-stu-id="a2f7f-120">Examples</span></span>

* <span data-ttu-id="a2f7f-121">Přidáte odkaz na projekt:</span><span class="sxs-lookup"><span data-stu-id="a2f7f-121">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="a2f7f-122">Přidání více odkazů projektu na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="a2f7f-122">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="a2f7f-123">Přidání více odkazů projektu pomocí vzoru podpory zástupných znaků v systému Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="a2f7f-123">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
