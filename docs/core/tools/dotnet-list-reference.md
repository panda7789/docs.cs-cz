---
title: příkaz odkaz DotNet seznamu - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet seznamu odkaz poskytuje vhodnou možnost do seznamu odkazy na projekt na projekt.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 946d3d523443fbe673b95dba95dbca327fde1699
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="1bfc7-103">referenční seznam DotNet.</span><span class="sxs-lookup"><span data-stu-id="1bfc7-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1bfc7-104">Název</span><span class="sxs-lookup"><span data-stu-id="1bfc7-104">Name</span></span>

<span data-ttu-id="1bfc7-105">`dotnet list reference` -Obsahuje seznam odkazů projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="1bfc7-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1bfc7-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="1bfc7-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="1bfc7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1bfc7-107">Description</span></span>

<span data-ttu-id="1bfc7-108">`dotnet list reference` Příkaz poskytuje vhodnou možnost do seznamu odkazy na projekt pro daný projekt.</span><span class="sxs-lookup"><span data-stu-id="1bfc7-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="1bfc7-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="1bfc7-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="1bfc7-110">Určuje soubor projektu pro výpis odkazy.</span><span class="sxs-lookup"><span data-stu-id="1bfc7-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="1bfc7-111">Pokud není zadáno, bude příkaz Hledat aktuální adresář pro soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="1bfc7-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="1bfc7-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="1bfc7-112">Options</span></span>

`-h|--help`

<span data-ttu-id="1bfc7-113">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="1bfc7-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="1bfc7-114">Příklady</span><span class="sxs-lookup"><span data-stu-id="1bfc7-114">Examples</span></span>

<span data-ttu-id="1bfc7-115">Seznam odkazy na projekt pro zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="1bfc7-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="1bfc7-116">Seznam odkazů projektu pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="1bfc7-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`
