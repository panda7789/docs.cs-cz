---
title: Dotnet list reference příkaz
description: Příkaz odkazu na seznam dotnet poskytuje vhodnou možnost vypsat odkazy na projekty.
ms.date: 02/14/2020
ms.openlocfilehash: c0ea46298123e69ae527870e50d204d8fcf5cc85
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463648"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="87fb2-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="87fb2-103">dotnet list reference</span></span>

<span data-ttu-id="87fb2-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="87fb2-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="87fb2-105">Název</span><span class="sxs-lookup"><span data-stu-id="87fb2-105">Name</span></span>

<span data-ttu-id="87fb2-106">`dotnet list reference`- Uvádí odkazy mezi projekty.</span><span class="sxs-lookup"><span data-stu-id="87fb2-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="87fb2-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="87fb2-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] reference

dotnet list -h|--help
```

## <a name="description"></a><span data-ttu-id="87fb2-108">Popis</span><span class="sxs-lookup"><span data-stu-id="87fb2-108">Description</span></span>

<span data-ttu-id="87fb2-109">Příkaz `dotnet list reference` poskytuje vhodnou možnost vypsat odkazy na projekt pro daný projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="87fb2-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="87fb2-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="87fb2-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="87fb2-111">Určuje soubor projektu nebo řešení, který má být používán pro výpis odkazů.</span><span class="sxs-lookup"><span data-stu-id="87fb2-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="87fb2-112">Pokud není zadán, příkaz prohledá aktuální adresář pro soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="87fb2-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="87fb2-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="87fb2-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="87fb2-114">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="87fb2-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="87fb2-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="87fb2-115">Examples</span></span>

* <span data-ttu-id="87fb2-116">Seznam odkazů na projekt pro zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="87fb2-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="87fb2-117">Seznam odkazů na projekt pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="87fb2-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
