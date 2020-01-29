---
title: dotnet – příkaz odkazu na seznam
description: Příkaz referenčního seznamu dotnet nabízí pohodlný možnost seznamu odkazů na projekt.
ms.date: 06/26/2019
ms.openlocfilehash: 496cbcd8fa4d921e30b363904ad0273bd5ebacd5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733220"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="d5700-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="d5700-103">dotnet list reference</span></span>

<span data-ttu-id="d5700-104">**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="d5700-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="d5700-105">Name</span><span class="sxs-lookup"><span data-stu-id="d5700-105">Name</span></span>

<span data-ttu-id="d5700-106">`dotnet list reference` – vypíše odkazy z projektu na projekt.</span><span class="sxs-lookup"><span data-stu-id="d5700-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d5700-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="d5700-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="d5700-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d5700-108">Description</span></span>

<span data-ttu-id="d5700-109">Příkaz `dotnet list reference` poskytuje pohodlný způsob pro výpis odkazů projektu pro daný projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="d5700-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="d5700-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="d5700-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="d5700-111">Určuje soubor projektu nebo řešení, který se má použít pro výpis odkazů.</span><span class="sxs-lookup"><span data-stu-id="d5700-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="d5700-112">Pokud není zadán, příkaz vyhledá v aktuálním adresáři soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="d5700-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="d5700-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d5700-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="d5700-114">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="d5700-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="d5700-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="d5700-115">Examples</span></span>

* <span data-ttu-id="d5700-116">Vypíše odkazy projektu pro zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="d5700-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="d5700-117">Vypíše odkazy na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="d5700-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
