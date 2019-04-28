---
title: DotNet – přidat odkaz na – příkaz
description: Příkaz dotnet add příkaz odkaz poskytuje vhodnou možnost pro přidání odkazů typu projekt na projekt.
ms.date: 12/04/2018
ms.openlocfilehash: 8df9fa3c9469f74b27a9cb8120936f03532b016c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665257"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="01a9e-103">DotNet – přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="01a9e-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="01a9e-104">Název</span><span class="sxs-lookup"><span data-stu-id="01a9e-104">Name</span></span>

<span data-ttu-id="01a9e-105">`dotnet add reference` -Přidá odkazy typu projekt projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="01a9e-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="01a9e-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="01a9e-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="01a9e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="01a9e-107">Description</span></span>

<span data-ttu-id="01a9e-108">`dotnet add reference` Příkaz poskytuje vhodnou možnost přidat odkazy na projekt do projektu.</span><span class="sxs-lookup"><span data-stu-id="01a9e-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="01a9e-109">Po spuštění příkazu [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) prvky jsou přidány do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="01a9e-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="01a9e-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="01a9e-110">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="01a9e-111">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="01a9e-111">Specifies the project file.</span></span> <span data-ttu-id="01a9e-112">Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.</span><span class="sxs-lookup"><span data-stu-id="01a9e-112">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="01a9e-113">Chcete-li přidat odkazuje na projekt na projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="01a9e-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="01a9e-114">Zadejte jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="01a9e-114">Specify one or more projects.</span></span> <span data-ttu-id="01a9e-115">[Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systémech založené na systému Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="01a9e-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="01a9e-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="01a9e-116">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="01a9e-117">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="01a9e-117">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="01a9e-118">Přidá odkazy na projekt jenom při cílení na konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="01a9e-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="01a9e-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="01a9e-119">Examples</span></span>

* <span data-ttu-id="01a9e-120">Přidáte odkaz na projekt:</span><span class="sxs-lookup"><span data-stu-id="01a9e-120">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="01a9e-121">Přidání více odkazů projektu na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="01a9e-121">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="01a9e-122">Přidání více odkazů projektu pomocí vzoru podpory zástupných znaků v systému Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="01a9e-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```