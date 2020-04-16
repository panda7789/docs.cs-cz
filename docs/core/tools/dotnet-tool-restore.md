---
title: dotnet nástroj obnovit, příkaz
description: Příkaz obnovení nástroje dotnet nainstaluje do počítače místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.
ms.date: 02/14/2020
ms.openlocfilehash: a518c2d45bbe9522bddfed4bbef61b30f1ad634b
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463331"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="f43b5-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="f43b5-103">dotnet tool restore</span></span>

<span data-ttu-id="f43b5-104">**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="f43b5-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f43b5-105">Název</span><span class="sxs-lookup"><span data-stu-id="f43b5-105">Name</span></span>

<span data-ttu-id="f43b5-106">`dotnet tool restore`- Nainstaluje do počítače místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="f43b5-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f43b5-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="f43b5-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a><span data-ttu-id="f43b5-108">Popis</span><span class="sxs-lookup"><span data-stu-id="f43b5-108">Description</span></span>

<span data-ttu-id="f43b5-109">Příkaz `dotnet tool restore` vyhledá soubor manifestu nástroje, který je v oboru pro aktuální adresář, a nainstaluje nástroje, které jsou v něm uvedeny.</span><span class="sxs-lookup"><span data-stu-id="f43b5-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="f43b5-110">Informace o souborech manifestu naleznete [v tématu Instalace místního nástroje](global-tools.md#install-a-local-tool) a [Vyvolání místního nástroje](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="f43b5-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="f43b5-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f43b5-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="f43b5-112">Název/ID balíčku NuGet, který obsahuje nástroj .NET Core k instalaci.</span><span class="sxs-lookup"><span data-stu-id="f43b5-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="f43b5-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f43b5-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="f43b5-114">Soubor konfigurace NuGet (*nuget.config).*</span><span class="sxs-lookup"><span data-stu-id="f43b5-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="f43b5-115">Přidá další zdroj balíčku NuGet pro použití během instalace.</span><span class="sxs-lookup"><span data-stu-id="f43b5-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="f43b5-116">Cesta k souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="f43b5-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="f43b5-117">Zabránit obnovení více projektů paralelně.</span><span class="sxs-lookup"><span data-stu-id="f43b5-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="f43b5-118">Považovat selhání zdroje balíčku jako upozornění.</span><span class="sxs-lookup"><span data-stu-id="f43b5-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="f43b5-119">Neukládat do mezipaměti balíčky a požadavky http.</span><span class="sxs-lookup"><span data-stu-id="f43b5-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="f43b5-120">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="f43b5-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="f43b5-121">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f43b5-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f43b5-122">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f43b5-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f43b5-123">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="f43b5-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="f43b5-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="f43b5-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="f43b5-125">Obnoví místní nástroje pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="f43b5-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="f43b5-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f43b5-126">See also</span></span>

- [<span data-ttu-id="f43b5-127">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="f43b5-127">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="f43b5-128">Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="f43b5-128">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
