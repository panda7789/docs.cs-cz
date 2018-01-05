---
title: "příkaz odkaz DotNet seznamu - .NET Core rozhraní příkazového řádku"
description: "Příkaz dotnet seznamu odkaz poskytuje vhodnou možnost do seznamu odkazy na projekt na projekt."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: a4ceadb6d070d7997e75b472624bbe2c1650396d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="f49ec-103">referenční seznam DotNet.</span><span class="sxs-lookup"><span data-stu-id="f49ec-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f49ec-104">Název</span><span class="sxs-lookup"><span data-stu-id="f49ec-104">Name</span></span>

<span data-ttu-id="f49ec-105">`dotnet list reference`-Obsahuje seznam odkazů projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="f49ec-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f49ec-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="f49ec-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="f49ec-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f49ec-107">Description</span></span>

<span data-ttu-id="f49ec-108">`dotnet list reference` Příkaz poskytuje vhodnou možnost do seznamu odkazy na projekt pro daný projekt.</span><span class="sxs-lookup"><span data-stu-id="f49ec-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="f49ec-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="f49ec-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="f49ec-110">Určuje soubor projektu pro výpis odkazy.</span><span class="sxs-lookup"><span data-stu-id="f49ec-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="f49ec-111">Pokud není zadáno, bude příkaz Hledat aktuální adresář pro soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="f49ec-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="f49ec-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f49ec-112">Options</span></span>

`-h|--help`

<span data-ttu-id="f49ec-113">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f49ec-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="f49ec-114">Příklady</span><span class="sxs-lookup"><span data-stu-id="f49ec-114">Examples</span></span>

<span data-ttu-id="f49ec-115">Seznam odkazy na projekt pro zadaného projektu:</span><span class="sxs-lookup"><span data-stu-id="f49ec-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="f49ec-116">Seznam odkazů projektu pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="f49ec-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`
