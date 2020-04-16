---
title: dotnet odebrat balíček, příkaz
description: Dotnet remove package příkaz poskytuje vhodnou možnost odebrat odkaz na balíček NuGet na projekt.
ms.date: 02/14/2020
ms.openlocfilehash: fc74ac1364a0ed027b83dab270d382f238dc00e5
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463457"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="fa12b-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="fa12b-103">dotnet remove package</span></span>

<span data-ttu-id="fa12b-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="fa12b-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fa12b-105">Název</span><span class="sxs-lookup"><span data-stu-id="fa12b-105">Name</span></span>

<span data-ttu-id="fa12b-106">`dotnet remove package`- Odebere odkaz na balíček ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="fa12b-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fa12b-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="fa12b-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME>

dotnet remove package -h|--help
```

## <a name="description"></a><span data-ttu-id="fa12b-108">Popis</span><span class="sxs-lookup"><span data-stu-id="fa12b-108">Description</span></span>

<span data-ttu-id="fa12b-109">Příkaz `dotnet remove package` poskytuje vhodnou možnost odebrat odkaz na balíček NuGet z projektu.</span><span class="sxs-lookup"><span data-stu-id="fa12b-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="fa12b-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fa12b-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="fa12b-111">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="fa12b-111">Specifies the project file.</span></span> <span data-ttu-id="fa12b-112">Pokud není zadán, příkaz prohledá aktuální adresář pro jeden.</span><span class="sxs-lookup"><span data-stu-id="fa12b-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="fa12b-113">Odkaz na balíček odebrat.</span><span class="sxs-lookup"><span data-stu-id="fa12b-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="fa12b-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="fa12b-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="fa12b-115">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="fa12b-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="fa12b-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="fa12b-116">Examples</span></span>

- <span data-ttu-id="fa12b-117">Odebrat `Newtonsoft.Json` balíček NuGet z projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="fa12b-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
