---
title: dotnet – příkaz odkazu na seznam
description: Příkaz referenčního seznamu dotnet nabízí pohodlný možnost seznamu odkazů na projekt.
ms.date: 06/26/2019
ms.openlocfilehash: b4b82ca1e7aeb2b73d9f99aff1c97452b2166770
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117674"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="40c44-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="40c44-103">dotnet list reference</span></span>

<span data-ttu-id="40c44-104">**Toto téma se týká: ✓** .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="40c44-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="40c44-105">Name</span><span class="sxs-lookup"><span data-stu-id="40c44-105">Name</span></span>

<span data-ttu-id="40c44-106">`dotnet list reference`-Obsahuje odkazy z projektu na projekt.</span><span class="sxs-lookup"><span data-stu-id="40c44-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="40c44-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="40c44-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="40c44-108">Popis</span><span class="sxs-lookup"><span data-stu-id="40c44-108">Description</span></span>

<span data-ttu-id="40c44-109">`dotnet list reference` Příkaz nabízí pohodlný možnost zobrazit odkazy projektu pro daný projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="40c44-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="40c44-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="40c44-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="40c44-111">Určuje soubor projektu nebo řešení, který se má použít pro výpis odkazů.</span><span class="sxs-lookup"><span data-stu-id="40c44-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="40c44-112">Pokud není zadán, příkaz vyhledá v aktuálním adresáři soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="40c44-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="40c44-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="40c44-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="40c44-114">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="40c44-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="40c44-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="40c44-115">Examples</span></span>

* <span data-ttu-id="40c44-116">Vypíše odkazy projektu pro zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="40c44-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="40c44-117">Vypíše odkazy na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="40c44-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
