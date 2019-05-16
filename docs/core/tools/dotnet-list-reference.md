---
title: příkaz DotNet seznamu odkaz
description: Příkaz dotnet seznamu odkaz nabízí pohodlný parametr pro seznam odkazů typu projekt na projekt.
ms.date: 12/03/2018
ms.openlocfilehash: c0b88c4a0af4469d7ddc9e0a9368bb1b2d9d20b6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632411"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="601c4-103">referenční seznam DotNet</span><span class="sxs-lookup"><span data-stu-id="601c4-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="601c4-104">Name</span><span class="sxs-lookup"><span data-stu-id="601c4-104">Name</span></span>

<span data-ttu-id="601c4-105">`dotnet list reference` -Obsahuje seznam odkazů typu projekt na projekt.</span><span class="sxs-lookup"><span data-stu-id="601c4-105">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="601c4-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="601c4-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="601c4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="601c4-107">Description</span></span>

<span data-ttu-id="601c4-108">`dotnet list reference` Příkaz poskytuje vhodnou možnost do odkazů projektu seznamu pro daný projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="601c4-108">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="601c4-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="601c4-109">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="601c4-110">Určuje soubor projektu má použít pro zobrazení seznamu odkazů.</span><span class="sxs-lookup"><span data-stu-id="601c4-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="601c4-111">Pokud není zadán, příkaz vyhledá v aktuálním adresáři souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="601c4-111">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="601c4-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="601c4-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="601c4-113">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="601c4-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="601c4-114">Příklady</span><span class="sxs-lookup"><span data-stu-id="601c4-114">Examples</span></span>

* <span data-ttu-id="601c4-115">Vypište odkazy na projekt pro zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="601c4-115">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="601c4-116">Seznam odkazů projektu pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="601c4-116">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```
