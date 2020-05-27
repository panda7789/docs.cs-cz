---
title: dotnet – příkaz odkazu na seznam
description: Příkaz referenčního seznamu dotnet nabízí pohodlný možnost seznamu odkazů na projekt.
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802755"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="70293-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="70293-103">dotnet list reference</span></span>

<span data-ttu-id="70293-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="70293-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="70293-105">Name</span><span class="sxs-lookup"><span data-stu-id="70293-105">Name</span></span>

<span data-ttu-id="70293-106">`dotnet list reference`-Obsahuje odkazy z projektu na projekt.</span><span class="sxs-lookup"><span data-stu-id="70293-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="70293-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="70293-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a><span data-ttu-id="70293-108">Popis</span><span class="sxs-lookup"><span data-stu-id="70293-108">Description</span></span>

<span data-ttu-id="70293-109">`dotnet list reference`Příkaz nabízí pohodlný možnost zobrazit odkazy projektu pro daný projekt.</span><span class="sxs-lookup"><span data-stu-id="70293-109">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="70293-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="70293-110">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="70293-111">Soubor projektu, na kterém má být provozován.</span><span class="sxs-lookup"><span data-stu-id="70293-111">The project file to operate on.</span></span> <span data-ttu-id="70293-112">Pokud soubor není zadán, příkaz bude hledat v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="70293-112">If a file is not specified, the command will search the current directory for one.</span></span>

## <a name="options"></a><span data-ttu-id="70293-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="70293-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="70293-114">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="70293-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="70293-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="70293-115">Examples</span></span>

* <span data-ttu-id="70293-116">Vypíše odkazy projektu pro zadaný projekt:</span><span class="sxs-lookup"><span data-stu-id="70293-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="70293-117">Vypíše odkazy na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="70293-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
