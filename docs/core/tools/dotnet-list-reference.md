---
title: příkaz DotNet seznamu odkaz
description: Příkaz dotnet seznamu odkaz nabízí pohodlný parametr pro seznam odkazů typu projekt na projekt.
ms.date: 12/03/2018
ms.openlocfilehash: d22ea27f8e8f6b94d763e44a6d8644f814663797
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169830"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="e9f1b-103">referenční seznam DotNet</span><span class="sxs-lookup"><span data-stu-id="e9f1b-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e9f1b-104">Název</span><span class="sxs-lookup"><span data-stu-id="e9f1b-104">Name</span></span>

<span data-ttu-id="e9f1b-105">`dotnet list reference` -Obsahuje seznam odkazů typu projekt na projekt.</span><span class="sxs-lookup"><span data-stu-id="e9f1b-105">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e9f1b-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="e9f1b-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="e9f1b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e9f1b-107">Description</span></span>

<span data-ttu-id="e9f1b-108">`dotnet list reference` Příkaz poskytuje vhodnou možnost do odkazů projektu seznamu pro daný projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="e9f1b-108">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="e9f1b-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="e9f1b-109">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="e9f1b-110">Určuje soubor projektu má použít pro zobrazení seznamu odkazů.</span><span class="sxs-lookup"><span data-stu-id="e9f1b-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="e9f1b-111">Pokud není zadán, příkaz vyhledá v aktuálním adresáři souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="e9f1b-111">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="e9f1b-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e9f1b-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="e9f1b-113">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="e9f1b-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="e9f1b-114">Příklady</span><span class="sxs-lookup"><span data-stu-id="e9f1b-114">Examples</span></span>

* <span data-ttu-id="e9f1b-115">Vypište odkazy na projekt pro zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="e9f1b-115">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="e9f1b-116">Seznam odkazů projektu pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="e9f1b-116">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```