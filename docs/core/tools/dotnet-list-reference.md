---
title: příkaz DotNet seznamu odkaz
description: Příkaz dotnet seznamu odkaz nabízí pohodlný parametr pro seznam odkazů typu projekt na projekt.
ms.date: 06/26/2019
ms.openlocfilehash: 1f87ff89997cdaa6d0095a4db9f28a2e7cb7e6a9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421833"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="a9d09-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="a9d09-103">dotnet list reference</span></span>

<span data-ttu-id="a9d09-104">**Toto téma platí pro: ✓** .NET Core 1.x sady SDK a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="a9d09-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="a9d09-105">Name</span><span class="sxs-lookup"><span data-stu-id="a9d09-105">Name</span></span>

<span data-ttu-id="a9d09-106">`dotnet list reference` -Obsahuje seznam odkazů typu projekt na projekt.</span><span class="sxs-lookup"><span data-stu-id="a9d09-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a9d09-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="a9d09-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="a9d09-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a9d09-108">Description</span></span>

<span data-ttu-id="a9d09-109">`dotnet list reference` Příkaz poskytuje vhodnou možnost do odkazů projektu seznamu pro daný projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="a9d09-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="a9d09-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="a9d09-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="a9d09-111">Určuje soubor projektu nebo řešení má použít pro zobrazení seznamu odkazů.</span><span class="sxs-lookup"><span data-stu-id="a9d09-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="a9d09-112">Pokud není zadán, příkaz vyhledá v aktuálním adresáři souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="a9d09-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="a9d09-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a9d09-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="a9d09-114">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a9d09-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="a9d09-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="a9d09-115">Examples</span></span>

* <span data-ttu-id="a9d09-116">Vypište odkazy na projekt pro zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="a9d09-116">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="a9d09-117">Seznam odkazů projektu pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="a9d09-117">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```
