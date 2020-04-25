---
title: dotnet – příkaz Remove reference
description: Příkaz dotnet Remove Reference poskytuje pohodlný způsob, jak odebrat projekt odkazům na projekt.
ms.date: 02/14/2020
ms.openlocfilehash: a45153376d7d6eb764c1d2c6b473d04a273a2de1
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158330"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="9d1b8-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="9d1b8-103">dotnet remove reference</span></span>

<span data-ttu-id="9d1b8-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="9d1b8-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9d1b8-105">Název</span><span class="sxs-lookup"><span data-stu-id="9d1b8-105">Name</span></span>

<span data-ttu-id="9d1b8-106">`dotnet remove reference`– Odebere odkazy z projektu na projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="9d1b8-106">`dotnet remove reference` - Removes project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9d1b8-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="9d1b8-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     <PROJECT_REFERENCES>

dotnet remove reference -h|--help
```

## <a name="description"></a><span data-ttu-id="9d1b8-108">Popis</span><span class="sxs-lookup"><span data-stu-id="9d1b8-108">Description</span></span>

<span data-ttu-id="9d1b8-109">`dotnet remove reference` Příkaz nabízí pohodlný možnost odebrání odkazů na projekt z projektu.</span><span class="sxs-lookup"><span data-stu-id="9d1b8-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="9d1b8-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9d1b8-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="9d1b8-111">Cílový soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="9d1b8-111">Target project file.</span></span> <span data-ttu-id="9d1b8-112">Pokud není zadán, příkaz vyhledá v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="9d1b8-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="9d1b8-113">Odkazy z projektu na projekt (P2P), které se mají odebrat.</span><span class="sxs-lookup"><span data-stu-id="9d1b8-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="9d1b8-114">Můžete určit jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="9d1b8-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="9d1b8-115">[Glob vzory](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v terminálech založených na systému UNIX/Linux.</span><span class="sxs-lookup"><span data-stu-id="9d1b8-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="9d1b8-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="9d1b8-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="9d1b8-117">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="9d1b8-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9d1b8-118">Odebere referenci pouze v případě, že cílí na konkrétní [rozhraní](../../standard/frameworks.md) pomocí formátu TFM.</span><span class="sxs-lookup"><span data-stu-id="9d1b8-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md) using the TFM format.</span></span>

## <a name="examples"></a><span data-ttu-id="9d1b8-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="9d1b8-119">Examples</span></span>

- <span data-ttu-id="9d1b8-120">Odebrat odkaz na projekt ze zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="9d1b8-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="9d1b8-121">Odebrat více odkazů na projekt z projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="9d1b8-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="9d1b8-122">Odebrání více odkazů na projekt pomocí vzoru glob v systému UNIX/Linux:</span><span class="sxs-lookup"><span data-stu-id="9d1b8-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
