---
title: příkaz DotNet odebrat odkaz
description: Příkaz dotnet odebrat odkaz poskytuje pohodlné možnost pro odebrání odkazů typu projekt na projekt.
ms.date: 05/29/2018
ms.openlocfilehash: bfac4721743babcf48fd8e86a50c8df136e1bfce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648591"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="e3bee-103">DotNet odebrat odkaz</span><span class="sxs-lookup"><span data-stu-id="e3bee-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e3bee-104">Název</span><span class="sxs-lookup"><span data-stu-id="e3bee-104">Name</span></span>

<span data-ttu-id="e3bee-105">`dotnet remove reference` – Odebere odkazy typu projekt projekt.</span><span class="sxs-lookup"><span data-stu-id="e3bee-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e3bee-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="e3bee-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="e3bee-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e3bee-107">Description</span></span>

<span data-ttu-id="e3bee-108">`dotnet remove reference` Příkaz poskytuje vhodnou možnost odebrat odkazy na projekt z projektu.</span><span class="sxs-lookup"><span data-stu-id="e3bee-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="e3bee-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="e3bee-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="e3bee-110">Cílový soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="e3bee-110">Target project file.</span></span> <span data-ttu-id="e3bee-111">Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.</span><span class="sxs-lookup"><span data-stu-id="e3bee-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="e3bee-112">Chcete-li odebrat odkazuje na projekt na projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="e3bee-112">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="e3bee-113">Můžete určit jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="e3bee-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="e3bee-114">[Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux na základě terminály.</span><span class="sxs-lookup"><span data-stu-id="e3bee-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="e3bee-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e3bee-115">Options</span></span>

`-h|--help`

<span data-ttu-id="e3bee-116">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="e3bee-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e3bee-117">Odebere odkaz pouze v případě cílení na konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e3bee-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="e3bee-118">Příklady</span><span class="sxs-lookup"><span data-stu-id="e3bee-118">Examples</span></span>

<span data-ttu-id="e3bee-119">Odebrání odkazu na projekt ze zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="e3bee-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="e3bee-120">Odeberte odkazy na více projektu z projektu v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="e3bee-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="e3bee-121">Odeberte odkazy na více projektů pomocí vzoru pro glob v systému Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="e3bee-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
