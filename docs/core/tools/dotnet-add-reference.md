---
title: dotnet – příkaz Add Reference
description: Příkaz dotnet Add Reference poskytuje pohodlný způsob, jak přidat projekt do odkazů projektu.
ms.date: 02/14/2020
ms.openlocfilehash: b261e24ed6a9d5bd489d317d2663b1420b5c34ff
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158317"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="71b71-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="71b71-103">dotnet add reference</span></span>

<span data-ttu-id="71b71-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="71b71-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="71b71-105">Název</span><span class="sxs-lookup"><span data-stu-id="71b71-105">Name</span></span>

<span data-ttu-id="71b71-106">`dotnet add reference`– Přidá odkazy na projekt na projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="71b71-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="71b71-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="71b71-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     [--interactive] <PROJECT_REFERENCES>

dotnet add reference -h|--help
```

## <a name="description"></a><span data-ttu-id="71b71-108">Popis</span><span class="sxs-lookup"><span data-stu-id="71b71-108">Description</span></span>

<span data-ttu-id="71b71-109">`dotnet add reference` Příkaz nabízí pohodlný možnost Přidat odkazy na projekt do projektu.</span><span class="sxs-lookup"><span data-stu-id="71b71-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="71b71-110">Po spuštění příkazu se `<ProjectReference>` prvky přidají do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="71b71-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="71b71-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="71b71-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="71b71-112">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="71b71-112">Specifies the project file.</span></span> <span data-ttu-id="71b71-113">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="71b71-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="71b71-114">Odkazy na projekt (P2P), které se mají přidat.</span><span class="sxs-lookup"><span data-stu-id="71b71-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="71b71-115">Zadejte jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="71b71-115">Specify one or more projects.</span></span> <span data-ttu-id="71b71-116">[Glob vzory](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systémech UNIX/Linux.</span><span class="sxs-lookup"><span data-stu-id="71b71-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="71b71-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="71b71-117">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="71b71-118">Přidá odkazy projektu pouze v případě, že cílí na konkrétní [rozhraní](../../standard/frameworks.md) pomocí formátu TFM.</span><span class="sxs-lookup"><span data-stu-id="71b71-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md) using the TFM format.</span></span>

- **`-h|--help`**

  <span data-ttu-id="71b71-119">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="71b71-119">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="71b71-120">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele (obvykle se používá k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="71b71-120">Allows the command to stop and wait for user input or action (typically used to complete authentication).</span></span> <span data-ttu-id="71b71-121">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="71b71-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="71b71-122">Příklady</span><span class="sxs-lookup"><span data-stu-id="71b71-122">Examples</span></span>

- <span data-ttu-id="71b71-123">Přidat odkaz na projekt:</span><span class="sxs-lookup"><span data-stu-id="71b71-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="71b71-124">Přidat do projektu více odkazů na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="71b71-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="71b71-125">Přidání více odkazů na projekt pomocí vzoru expanze názvů na platformě Linux/UNIX:</span><span class="sxs-lookup"><span data-stu-id="71b71-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
