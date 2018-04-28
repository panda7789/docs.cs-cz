---
title: příkaz odkaz DotNet remove - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet odebrat odkaz poskytuje vhodnou možnost odebrat odkazy na projekt na projekt.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 0b7fb2788ccc04b54bf02f0387141d501612c16d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="0d064-103">Odebrat odkaz DotNet.</span><span class="sxs-lookup"><span data-stu-id="0d064-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0d064-104">Název</span><span class="sxs-lookup"><span data-stu-id="0d064-104">Name</span></span>

<span data-ttu-id="0d064-105">`dotnet remove reference` – Odebere odkazy na projekt na projekt.</span><span class="sxs-lookup"><span data-stu-id="0d064-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0d064-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="0d064-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="0d064-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0d064-107">Description</span></span>

<span data-ttu-id="0d064-108">`dotnet remove reference` Příkaz poskytuje vhodnou možnost odebrat odkazy na projekt z projektu.</span><span class="sxs-lookup"><span data-stu-id="0d064-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="0d064-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="0d064-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="0d064-110">Cílový soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="0d064-110">Target project file.</span></span> <span data-ttu-id="0d064-111">Pokud není zadaný, hledá příkaz aktuální adresář pro jednu.</span><span class="sxs-lookup"><span data-stu-id="0d064-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="0d064-112">Projekt do projektu (P2P odkazy na odebrat.</span><span class="sxs-lookup"><span data-stu-id="0d064-112">Project to project (P2P references to remove.</span></span> <span data-ttu-id="0d064-113">Můžete určit jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="0d064-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="0d064-114">[Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux, na základě terminály.</span><span class="sxs-lookup"><span data-stu-id="0d064-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="0d064-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0d064-115">Options</span></span>

`-h|--help`

<span data-ttu-id="0d064-116">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0d064-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0d064-117">Odebere odkaz jenom při cílení na konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0d064-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="0d064-118">Příklady</span><span class="sxs-lookup"><span data-stu-id="0d064-118">Examples</span></span>

<span data-ttu-id="0d064-119">Odeberte odkaz na projekt z zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="0d064-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="0d064-120">Odebrání více odkazy na projekt na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="0d064-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="0d064-121">Odebrání více odkazů projektu pomocí vzoru glob na systému Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="0d064-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
