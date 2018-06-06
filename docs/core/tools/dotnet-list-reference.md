---
title: příkaz odkaz DotNet seznamu - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet seznamu odkaz poskytuje vhodnou možnost do seznamu odkazy na projekt na projekt.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 821e6d276af44bf984c8ac1b42b4e954dbe69556
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697180"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="b7688-103">referenční seznam DotNet.</span><span class="sxs-lookup"><span data-stu-id="b7688-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b7688-104">Název</span><span class="sxs-lookup"><span data-stu-id="b7688-104">Name</span></span>

<span data-ttu-id="b7688-105">`dotnet list reference` -Obsahuje seznam odkazů projektu projektu.</span><span class="sxs-lookup"><span data-stu-id="b7688-105">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b7688-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="b7688-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="b7688-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b7688-107">Description</span></span>

<span data-ttu-id="b7688-108">`dotnet list reference` Příkaz poskytuje vhodnou možnost do seznamu odkazy na projekt pro daný projekt.</span><span class="sxs-lookup"><span data-stu-id="b7688-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="b7688-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="b7688-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="b7688-110">Určuje soubor projektu pro výpis odkazy.</span><span class="sxs-lookup"><span data-stu-id="b7688-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="b7688-111">Pokud není zadaný, hledá příkaz aktuální adresář pro soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="b7688-111">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="b7688-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b7688-112">Options</span></span>

`-h|--help`

<span data-ttu-id="b7688-113">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="b7688-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="b7688-114">Příklady</span><span class="sxs-lookup"><span data-stu-id="b7688-114">Examples</span></span>

<span data-ttu-id="b7688-115">Seznam odkazy na projekt pro zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="b7688-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="b7688-116">Seznam odkazů projektu pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="b7688-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`