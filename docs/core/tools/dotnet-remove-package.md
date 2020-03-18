---
title: dotnet odebrat balíček, příkaz
description: Dotnet remove package příkaz poskytuje vhodnou možnost odebrat odkaz na balíček NuGet na projekt.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503629"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="71951-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="71951-103">dotnet remove package</span></span>

<span data-ttu-id="71951-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="71951-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="71951-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="71951-105">Name</span></span>

<span data-ttu-id="71951-106">`dotnet remove package`- Odebere odkaz na balíček ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="71951-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="71951-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="71951-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="71951-108">Popis</span><span class="sxs-lookup"><span data-stu-id="71951-108">Description</span></span>

<span data-ttu-id="71951-109">Příkaz `dotnet remove package` poskytuje vhodnou možnost odebrat odkaz na balíček NuGet z projektu.</span><span class="sxs-lookup"><span data-stu-id="71951-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="71951-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="71951-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="71951-111">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="71951-111">Specifies the project file.</span></span> <span data-ttu-id="71951-112">Pokud není zadán, příkaz prohledá aktuální adresář pro jeden.</span><span class="sxs-lookup"><span data-stu-id="71951-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="71951-113">Odkaz na balíček odebrat.</span><span class="sxs-lookup"><span data-stu-id="71951-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="71951-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="71951-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="71951-115">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="71951-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="71951-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="71951-116">Examples</span></span>

- <span data-ttu-id="71951-117">Odebrat `Newtonsoft.Json` balíček NuGet z projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="71951-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
