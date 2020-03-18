---
title: dotnet přidat odkaz, příkaz
description: Dotnet add reference příkaz poskytuje vhodnou možnost přidat projekt do odkazů projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 84ea25e94efc8d84aebfeccf62c30a64551c5019
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503797"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="13be6-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="13be6-103">dotnet add reference</span></span>

<span data-ttu-id="13be6-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="13be6-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="13be6-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="13be6-105">Name</span></span>

<span data-ttu-id="13be6-106">`dotnet add reference`- Přidá odkazy projekt-projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="13be6-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="13be6-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="13be6-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a><span data-ttu-id="13be6-108">Popis</span><span class="sxs-lookup"><span data-stu-id="13be6-108">Description</span></span>

<span data-ttu-id="13be6-109">Příkaz `dotnet add reference` poskytuje vhodnou možnost přidání odkazů na projekt do projektu.</span><span class="sxs-lookup"><span data-stu-id="13be6-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="13be6-110">Po spuštění příkazu `<ProjectReference>` jsou prvky přidány do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="13be6-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="13be6-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="13be6-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="13be6-112">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="13be6-112">Specifies the project file.</span></span> <span data-ttu-id="13be6-113">Pokud není zadán, příkaz prohledá aktuální adresář pro jeden.</span><span class="sxs-lookup"><span data-stu-id="13be6-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="13be6-114">Odkazy projektu na projekt (P2P), které chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="13be6-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="13be6-115">Zadejte jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="13be6-115">Specify one or more projects.</span></span> <span data-ttu-id="13be6-116">Glob vzory jsou [podporovány](https://en.wikipedia.org/wiki/Glob_(programming)) na Unix / Linux-založené systémy.</span><span class="sxs-lookup"><span data-stu-id="13be6-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="13be6-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="13be6-117">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="13be6-118">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="13be6-118">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="13be6-119">Přidá odkazy na projekt pouze v případě, že cílí na konkrétní [rámec](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="13be6-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`--interactive`**

  <span data-ttu-id="13be6-120">Umožňuje příkazu zastavit a čekat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="13be6-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="13be6-121">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="13be6-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="13be6-122">Příklady</span><span class="sxs-lookup"><span data-stu-id="13be6-122">Examples</span></span>

- <span data-ttu-id="13be6-123">Přidejte odkaz na projekt:</span><span class="sxs-lookup"><span data-stu-id="13be6-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="13be6-124">Přidejte do projektu více odkazů na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="13be6-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="13be6-125">Přidejte více odkazů na projekt pomocí globbingového vzoru na Linuxu/Unixu:</span><span class="sxs-lookup"><span data-stu-id="13be6-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
