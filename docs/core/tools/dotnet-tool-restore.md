---
title: dotnet – příkaz obnovení nástroje
description: Příkaz pro obnovení nástroje dotnet se nainstaluje na váš počítač. místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.
ms.date: 02/14/2020
ms.openlocfilehash: ceef3274ec9d337f8c51009d5a8c27e808b14035
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302669"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="02a3d-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="02a3d-103">dotnet tool restore</span></span>

<span data-ttu-id="02a3d-104">**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="02a3d-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="02a3d-105">Název</span><span class="sxs-lookup"><span data-stu-id="02a3d-105">Name</span></span>

<span data-ttu-id="02a3d-106">`dotnet tool restore`– Nainstaluje na váš počítač místní nástroje .NET Core, které jsou v oboru pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="02a3d-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="02a3d-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="02a3d-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a><span data-ttu-id="02a3d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="02a3d-108">Description</span></span>

<span data-ttu-id="02a3d-109">`dotnet tool restore`Příkaz najde soubor manifestu nástroje, který je v oboru pro aktuální adresář a nainstaluje nástroje, které jsou uvedeny v něm.</span><span class="sxs-lookup"><span data-stu-id="02a3d-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="02a3d-110">Informace o souborech manifestu najdete v tématech [instalace místního nástroje](global-tools.md#install-a-local-tool) a [vyvolání místního nástroje](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="02a3d-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="options"></a><span data-ttu-id="02a3d-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="02a3d-111">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="02a3d-112">Soubor konfigurace NuGet (*nuget.config*), který se má použít.</span><span class="sxs-lookup"><span data-stu-id="02a3d-112">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="02a3d-113">Přidá další zdroj balíčku NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="02a3d-113">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="02a3d-114">Cesta k souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="02a3d-114">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="02a3d-115">Zabránit v paralelním obnovení více projektů.</span><span class="sxs-lookup"><span data-stu-id="02a3d-115">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="02a3d-116">Považovat selhání zdroje balíčku za upozornění.</span><span class="sxs-lookup"><span data-stu-id="02a3d-116">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="02a3d-117">Neukládat balíčky a požadavky HTTP do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="02a3d-117">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="02a3d-118">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="02a3d-118">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="02a3d-119">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="02a3d-119">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="02a3d-120">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="02a3d-120">Sets the verbosity level of the command.</span></span> <span data-ttu-id="02a3d-121">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="02a3d-121">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="02a3d-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="02a3d-122">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="02a3d-123">Obnoví místní nástroje pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="02a3d-123">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="02a3d-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02a3d-124">See also</span></span>

- [<span data-ttu-id="02a3d-125">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="02a3d-125">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="02a3d-126">Kurz: instalace a použití místního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="02a3d-126">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
