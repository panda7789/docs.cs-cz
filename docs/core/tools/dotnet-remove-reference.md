---
title: dotnet odebrat odkaz, příkaz
description: Dotnet remove reference příkaz poskytuje vhodnou možnost odebrat projekt na odkazy projektu.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503616"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="eab84-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="eab84-103">dotnet remove reference</span></span>

<span data-ttu-id="eab84-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="eab84-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="eab84-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="eab84-105">Name</span></span>

<span data-ttu-id="eab84-106">`dotnet remove reference`- Odebere odkazy mezi projekty.</span><span class="sxs-lookup"><span data-stu-id="eab84-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="eab84-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="eab84-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="eab84-108">Popis</span><span class="sxs-lookup"><span data-stu-id="eab84-108">Description</span></span>

<span data-ttu-id="eab84-109">Příkaz `dotnet remove reference` poskytuje vhodnou možnost odebrání odkazů na projekt z projektu.</span><span class="sxs-lookup"><span data-stu-id="eab84-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="eab84-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="eab84-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="eab84-111">Cílový soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="eab84-111">Target project file.</span></span> <span data-ttu-id="eab84-112">Pokud není zadán, příkaz prohledá aktuální adresář pro jeden.</span><span class="sxs-lookup"><span data-stu-id="eab84-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="eab84-113">Odkazy projektu na projekt (P2P) k odstranění.</span><span class="sxs-lookup"><span data-stu-id="eab84-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="eab84-114">Můžete zadat jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="eab84-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="eab84-115">Glob vzory jsou [podporovány](https://en.wikipedia.org/wiki/Glob_(programming)) na Unix / Linux založené terminály.</span><span class="sxs-lookup"><span data-stu-id="eab84-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="eab84-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="eab84-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="eab84-117">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="eab84-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="eab84-118">Odebere odkaz pouze při cílení na konkrétní [rámec](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="eab84-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="eab84-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="eab84-119">Examples</span></span>

- <span data-ttu-id="eab84-120">Odeberte odkaz na projekt ze zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="eab84-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="eab84-121">Odebrání více odkazů na projekt z projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="eab84-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="eab84-122">Odstraňte více odkazů na projekt pomocí glob vzoru na Unix /Linux:</span><span class="sxs-lookup"><span data-stu-id="eab84-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
