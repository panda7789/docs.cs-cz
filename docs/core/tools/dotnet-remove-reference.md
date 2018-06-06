---
title: příkaz odkaz DotNet remove - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet odebrat odkaz poskytuje vhodnou možnost odebrat odkazy na projekt na projekt.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: b281b255be7f49a99a6b4928c340cd4fb085f085
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696228"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="f118e-103">Odebrat odkaz DotNet.</span><span class="sxs-lookup"><span data-stu-id="f118e-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f118e-104">Název</span><span class="sxs-lookup"><span data-stu-id="f118e-104">Name</span></span>

<span data-ttu-id="f118e-105">`dotnet remove reference` – Odebere odkazy na projekt na projekt.</span><span class="sxs-lookup"><span data-stu-id="f118e-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f118e-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="f118e-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="f118e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f118e-107">Description</span></span>

<span data-ttu-id="f118e-108">`dotnet remove reference` Příkaz poskytuje vhodnou možnost odebrat odkazy na projekt z projektu.</span><span class="sxs-lookup"><span data-stu-id="f118e-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="f118e-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="f118e-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="f118e-110">Cílový soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="f118e-110">Target project file.</span></span> <span data-ttu-id="f118e-111">Pokud není zadaný, hledá příkaz aktuální adresář pro jednu.</span><span class="sxs-lookup"><span data-stu-id="f118e-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="f118e-112">Chcete-li odebrat odkazuje na projekt na projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="f118e-112">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="f118e-113">Můžete určit jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="f118e-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="f118e-114">[Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux, na základě terminály.</span><span class="sxs-lookup"><span data-stu-id="f118e-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="f118e-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f118e-115">Options</span></span>

`-h|--help`

<span data-ttu-id="f118e-116">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f118e-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="f118e-117">Odebere odkaz jenom při cílení na konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f118e-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="f118e-118">Příklady</span><span class="sxs-lookup"><span data-stu-id="f118e-118">Examples</span></span>

<span data-ttu-id="f118e-119">Odeberte odkaz na projekt z zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="f118e-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="f118e-120">Odebrání více odkazy na projekt na projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="f118e-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="f118e-121">Odebrání více odkazů projektu pomocí vzoru glob na systému Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="f118e-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
