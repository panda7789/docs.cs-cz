---
title: DotNet odebrat balíček příkaz - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet odebrat balíček poskytuje vhodnou možnost odebrat odkaz na balíček NuGet do projektu.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: bdb66a24526b04e8300e654a991719bb607971b8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="2cff3-103">Odebrat balíček DotNet.</span><span class="sxs-lookup"><span data-stu-id="2cff3-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2cff3-104">Název</span><span class="sxs-lookup"><span data-stu-id="2cff3-104">Name</span></span>

<span data-ttu-id="2cff3-105">`dotnet remove package` – Odebere odkaz na balíček ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="2cff3-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2cff3-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="2cff3-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="2cff3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2cff3-107">Description</span></span>

<span data-ttu-id="2cff3-108">`dotnet remove package` Příkaz poskytuje vhodnou možnost odebrat odkaz balíčku NuGet z projektu.</span><span class="sxs-lookup"><span data-stu-id="2cff3-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="2cff3-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="2cff3-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="2cff3-110">Určuje soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="2cff3-110">Specifies the project file.</span></span> <span data-ttu-id="2cff3-111">Pokud není zadáno, bude příkaz hledání aktuální adresář pro jednu.</span><span class="sxs-lookup"><span data-stu-id="2cff3-111">If not specified, the command will search the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="2cff3-112">Odkaz na balíček odebrat.</span><span class="sxs-lookup"><span data-stu-id="2cff3-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="2cff3-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="2cff3-113">Options</span></span>

`-h|--help`

<span data-ttu-id="2cff3-114">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="2cff3-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="2cff3-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="2cff3-115">Examples</span></span>

<span data-ttu-id="2cff3-116">Odebere `Newtonsoft.Json` balíček NuGet z projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="2cff3-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`
