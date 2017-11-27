---
title: "příkaz odkaz DotNet remove - .NET Core rozhraní příkazového řádku"
description: "Příkaz dotnet odebrat odkaz poskytuje vhodnou možnost odebrat odkazy na projekt na projekt."
keywords: "příkaz DotNet-remove, rozhraní příkazového řádku, rozhraní příkazového řádku, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 7cb84c2dc7fc4d16b00bd6459132390ab80131f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="521e7-104">Odebrat odkaz DotNet.</span><span class="sxs-lookup"><span data-stu-id="521e7-104">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="521e7-105">Název</span><span class="sxs-lookup"><span data-stu-id="521e7-105">Name</span></span>

<span data-ttu-id="521e7-106">`dotnet remove reference`– Odebere odkazy na projekt na projekt.</span><span class="sxs-lookup"><span data-stu-id="521e7-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="521e7-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="521e7-107">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="521e7-108">Popis</span><span class="sxs-lookup"><span data-stu-id="521e7-108">Description</span></span>

<span data-ttu-id="521e7-109">`dotnet remove reference` Příkaz poskytuje vhodnou možnost odebrat odkazy na projekt z projektu.</span><span class="sxs-lookup"><span data-stu-id="521e7-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="521e7-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="521e7-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="521e7-111">Cílový soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="521e7-111">Target project file.</span></span> <span data-ttu-id="521e7-112">Pokud není zadaný, hledá příkaz aktuální adresář pro jednu.</span><span class="sxs-lookup"><span data-stu-id="521e7-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="521e7-113">Projekt do projektu (P2P odkazy na odebrat.</span><span class="sxs-lookup"><span data-stu-id="521e7-113">Project to project (P2P references to remove.</span></span> <span data-ttu-id="521e7-114">Můžete určit jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="521e7-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="521e7-115">[Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux, na základě terminály.</span><span class="sxs-lookup"><span data-stu-id="521e7-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="521e7-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="521e7-116">Options</span></span>

`-h|--help`

<span data-ttu-id="521e7-117">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="521e7-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="521e7-118">Odebere odkaz jenom při cílení na konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="521e7-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="521e7-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="521e7-119">Examples</span></span>

<span data-ttu-id="521e7-120">Odeberte odkaz na projekt z zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="521e7-120">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="521e7-121">Odebrání více odkazy na projekt na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="521e7-121">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="521e7-122">Odebrání více odkazů projektu pomocí vzoru glob na systému Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="521e7-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
