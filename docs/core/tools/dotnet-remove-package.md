---
title: Odebrat balíček příkaz DotNet
description: Příkaz dotnet odebrat balíček poskytuje pohodlné možnost pro odebrání odkazu na balíček NuGet do projektu.
ms.date: 05/29/2018
ms.openlocfilehash: cbdeacff78ef20c9a73010e10a771a724b23792e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632438"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="50b45-103">DotNet odebrat balíček</span><span class="sxs-lookup"><span data-stu-id="50b45-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="50b45-104">Name</span><span class="sxs-lookup"><span data-stu-id="50b45-104">Name</span></span>

<span data-ttu-id="50b45-105">`dotnet remove package` – Odebere odkaz na balíček ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="50b45-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="50b45-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="50b45-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="50b45-107">Popis</span><span class="sxs-lookup"><span data-stu-id="50b45-107">Description</span></span>

<span data-ttu-id="50b45-108">`dotnet remove package` Příkaz poskytuje vhodnou možnost odebrat z projektu odkaz na balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="50b45-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="50b45-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="50b45-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="50b45-110">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="50b45-110">Specifies the project file.</span></span> <span data-ttu-id="50b45-111">Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.</span><span class="sxs-lookup"><span data-stu-id="50b45-111">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="50b45-112">Odkaz na balíček k odebrání.</span><span class="sxs-lookup"><span data-stu-id="50b45-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="50b45-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="50b45-113">Options</span></span>

`-h|--help`

<span data-ttu-id="50b45-114">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="50b45-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="50b45-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="50b45-115">Examples</span></span>

<span data-ttu-id="50b45-116">Odebere `Newtonsoft.Json` balíček NuGet z projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="50b45-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`
