---
title: Odebrat balíček příkaz DotNet
description: Příkaz dotnet odebrat balíček poskytuje pohodlné možnost pro odebrání odkazu na balíček NuGet do projektu.
ms.date: 05/29/2018
ms.openlocfilehash: 4cc8ac927b761547dc5e53be9abeba827bf1e1d9
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168725"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="5cbe9-103">DotNet odebrat balíček</span><span class="sxs-lookup"><span data-stu-id="5cbe9-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5cbe9-104">Název</span><span class="sxs-lookup"><span data-stu-id="5cbe9-104">Name</span></span>

<span data-ttu-id="5cbe9-105">`dotnet remove package` – Odebere odkaz na balíček ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="5cbe9-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5cbe9-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="5cbe9-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="5cbe9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5cbe9-107">Description</span></span>

<span data-ttu-id="5cbe9-108">`dotnet remove package` Příkaz poskytuje vhodnou možnost odebrat z projektu odkaz na balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="5cbe9-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="5cbe9-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="5cbe9-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="5cbe9-110">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="5cbe9-110">Specifies the project file.</span></span> <span data-ttu-id="5cbe9-111">Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.</span><span class="sxs-lookup"><span data-stu-id="5cbe9-111">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="5cbe9-112">Odkaz na balíček k odebrání.</span><span class="sxs-lookup"><span data-stu-id="5cbe9-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="5cbe9-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5cbe9-113">Options</span></span>

`-h|--help`

<span data-ttu-id="5cbe9-114">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="5cbe9-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="5cbe9-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="5cbe9-115">Examples</span></span>

<span data-ttu-id="5cbe9-116">Odebere `Newtonsoft.Json` balíček NuGet z projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="5cbe9-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`