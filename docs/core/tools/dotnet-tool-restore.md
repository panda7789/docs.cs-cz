---
title: dotnet nástroj obnovit, příkaz
description: Příkaz obnovení nástroje dotnet nainstaluje do počítače místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.
ms.date: 02/14/2020
ms.openlocfilehash: 0d1e67ec809ddd725721698cc741f9acc99e1ce7
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389617"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="ad517-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="ad517-103">dotnet tool restore</span></span>

<span data-ttu-id="ad517-104">**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="ad517-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ad517-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="ad517-105">Name</span></span>

<span data-ttu-id="ad517-106">`dotnet tool restore`- Nainstaluje do počítače místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="ad517-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ad517-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="ad517-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [--interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="ad517-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ad517-108">Description</span></span>

<span data-ttu-id="ad517-109">Příkaz `dotnet tool restore` vyhledá soubor manifestu nástroje, který je v oboru pro aktuální adresář, a nainstaluje nástroje, které jsou v něm uvedeny.</span><span class="sxs-lookup"><span data-stu-id="ad517-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="ad517-110">Informace o souborech manifestu naleznete [v tématu Instalace místního nástroje](global-tools.md#install-a-local-tool) a [Vyvolání místního nástroje](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="ad517-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="ad517-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ad517-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="ad517-112">Název/ID balíčku NuGet, který obsahuje nástroj .NET Core k instalaci.</span><span class="sxs-lookup"><span data-stu-id="ad517-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="ad517-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ad517-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="ad517-114">Soubor konfigurace NuGet (*nuget.config).*</span><span class="sxs-lookup"><span data-stu-id="ad517-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="ad517-115">Přidá další zdroj balíčku NuGet pro použití během instalace.</span><span class="sxs-lookup"><span data-stu-id="ad517-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="ad517-116">Cesta k souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="ad517-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="ad517-117">Zabránit obnovení více projektů paralelně.</span><span class="sxs-lookup"><span data-stu-id="ad517-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="ad517-118">Považovat selhání zdroje balíčku jako upozornění.</span><span class="sxs-lookup"><span data-stu-id="ad517-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="ad517-119">Neukládat do mezipaměti balíčky a požadavky http.</span><span class="sxs-lookup"><span data-stu-id="ad517-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="ad517-120">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="ad517-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="ad517-121">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="ad517-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="ad517-122">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="ad517-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ad517-123">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="ad517-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="ad517-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad517-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="ad517-125">Obnoví místní nástroje pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="ad517-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad517-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad517-126">See also</span></span>

- [<span data-ttu-id="ad517-127">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad517-127">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="ad517-128">Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="ad517-128">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
