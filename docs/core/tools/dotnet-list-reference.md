---
title: dotnet – příkaz odkazu na seznam
description: Příkaz referenčního seznamu dotnet nabízí pohodlný možnost seznamu odkazů na projekt.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503714"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="7c035-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="7c035-103">dotnet list reference</span></span>

<span data-ttu-id="7c035-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="7c035-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7c035-105">Název</span><span class="sxs-lookup"><span data-stu-id="7c035-105">Name</span></span>

<span data-ttu-id="7c035-106">`dotnet list reference` – vypíše odkazy z projektu na projekt.</span><span class="sxs-lookup"><span data-stu-id="7c035-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7c035-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="7c035-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="7c035-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7c035-108">Description</span></span>

<span data-ttu-id="7c035-109">Příkaz `dotnet list reference` poskytuje pohodlný způsob pro výpis odkazů projektu pro daný projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="7c035-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="7c035-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7c035-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="7c035-111">Určuje soubor projektu nebo řešení, který se má použít pro výpis odkazů.</span><span class="sxs-lookup"><span data-stu-id="7c035-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="7c035-112">Pokud není zadán, příkaz vyhledá v aktuálním adresáři soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="7c035-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="7c035-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="7c035-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="7c035-114">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="7c035-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="7c035-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="7c035-115">Examples</span></span>

* <span data-ttu-id="7c035-116">Vypíše odkazy projektu pro zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="7c035-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="7c035-117">Vypíše odkazy na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="7c035-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
