---
title: dotnet – příkaz obnovení nástroje
description: Příkaz pro obnovení nástroje dotnet se nainstaluje na váš počítač. místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.
ms.date: 02/14/2020
ms.openlocfilehash: 2900d431987661a9232ceed10d9a424093f8be45
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543906"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="85834-103">obnovení nástroje dotnet</span><span class="sxs-lookup"><span data-stu-id="85834-103">dotnet tool restore</span></span>

<span data-ttu-id="85834-104">**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="85834-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="85834-105">Název</span><span class="sxs-lookup"><span data-stu-id="85834-105">Name</span></span>

<span data-ttu-id="85834-106">`dotnet tool restore` – nainstaluje na váš počítač místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="85834-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="85834-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="85834-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME> [--configfile] [--add-source] [tool-manifest] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [-interactive] [-v|--verbosity]
dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="85834-108">Popis</span><span class="sxs-lookup"><span data-stu-id="85834-108">Description</span></span>

<span data-ttu-id="85834-109">Příkaz `dotnet tool restore` najde soubor manifestu nástroje, který je v oboru pro aktuální adresář a nainstaluje nástroje, které jsou uvedeny v něm.</span><span class="sxs-lookup"><span data-stu-id="85834-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="85834-110">Informace o souborech manifestu najdete v tématech [instalace místního nástroje](global-tools.md#install-a-local-tool) a [vyvolání místního nástroje](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="85834-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="85834-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="85834-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="85834-112">Název nebo ID balíčku NuGet, který obsahuje nástroj .NET Core, který se má nainstalovat</span><span class="sxs-lookup"><span data-stu-id="85834-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="85834-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="85834-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="85834-114">Soubor konfigurace NuGet (*NuGet. config*), který se má použít.</span><span class="sxs-lookup"><span data-stu-id="85834-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="85834-115">Přidá další zdroj balíčku NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="85834-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="85834-116">Cesta k souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="85834-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="85834-117">Zabránit v paralelním obnovení více projektů.</span><span class="sxs-lookup"><span data-stu-id="85834-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="85834-118">Považovat selhání zdroje balíčku za upozornění.</span><span class="sxs-lookup"><span data-stu-id="85834-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="85834-119">Neukládat balíčky a požadavky HTTP do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="85834-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="85834-120">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="85834-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="85834-121">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="85834-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="85834-122">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="85834-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="85834-123">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="85834-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="85834-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="85834-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="85834-125">Obnoví místní nástroje pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="85834-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="85834-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85834-126">See also</span></span>

- [<span data-ttu-id="85834-127">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="85834-127">.NET Core tools</span></span>](global-tools.md)
