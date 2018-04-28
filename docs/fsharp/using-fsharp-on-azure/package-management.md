---
title: 'Pomocí správy balíčků F # pro Azure.'
description: 'Ke správě závislosti F # Azure použijte stáhnout nebo Nuget'
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: da6938c6ee29292571f4269c68a9148c13738422
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="dbfd8-103">Balíček správy pro závislosti Azure F #</span><span class="sxs-lookup"><span data-stu-id="dbfd8-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="dbfd8-104">Získání balíčky pro vývoj pro Azure je snadný při použití Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="dbfd8-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="dbfd8-105">Dvě možnosti jsou [Stáhnout](https://fsprojects.github.io/Paket/) a [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="dbfd8-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="dbfd8-106">Pomocí stáhnout</span><span class="sxs-lookup"><span data-stu-id="dbfd8-106">Using Paket</span></span>

<span data-ttu-id="dbfd8-107">Pokud používáte [Stáhnout](https://fsprojects.github.io/Paket/) jako závislost nadřízeného, můžete použít `paket.exe` nástroje pro přidání Azure závislosti.</span><span class="sxs-lookup"><span data-stu-id="dbfd8-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="dbfd8-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-108">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="dbfd8-109">Nebo, pokud používáte [Mono](https://www.mono-project.com/) pro vývoj pro různé platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="dbfd8-110">Bude přidáno `WindowsAzure.Storage` množina závislosti balíčků pro projekt v aktuálním adresáři, upravte `paket.dependencies` souboru a stáhněte si balíček.</span><span class="sxs-lookup"><span data-stu-id="dbfd8-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="dbfd8-111">Pokud jste dříve nastavili závislosti nebo práci s projektem kde závislosti již byly vytvořeny pomocí jiné vývojáře, můžete vyřešit a instalaci závislostí místně takto:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="dbfd8-112">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-112">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="dbfd8-113">Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi takto:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-113">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="dbfd8-114">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-114">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="dbfd8-115">Pomocí nástroje Nuget</span><span class="sxs-lookup"><span data-stu-id="dbfd8-115">Using Nuget</span></span>

<span data-ttu-id="dbfd8-116">Pokud používáte [NuGet](https://www.nuget.org/) jako závislost nadřízeného, můžete použít `nuget.exe` nástroje pro přidání Azure závislosti.</span><span class="sxs-lookup"><span data-stu-id="dbfd8-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="dbfd8-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-117">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="dbfd8-118">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-118">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="dbfd8-119">Bude přidáno `WindowsAzure.Storage` množina závislosti balíčků pro projekt v aktuálním adresáři a stažení balíčku.</span><span class="sxs-lookup"><span data-stu-id="dbfd8-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="dbfd8-120">Pokud jste dříve nastavili závislosti nebo práci s projektem kde závislosti již byly vytvořeny pomocí jiné vývojáře, můžete vyřešit a instalaci závislostí místně takto:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="dbfd8-121">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-121">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="dbfd8-122">Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi takto:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-122">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="dbfd8-123">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-123">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="dbfd8-124">Odkazování na sestavení</span><span class="sxs-lookup"><span data-stu-id="dbfd8-124">Referencing Assemblies</span></span>

<span data-ttu-id="dbfd8-125">Chcete-li použít vlastních balíčků ve vašem skriptu F #, je třeba odkazovat sestavení součástí balíčků pomocí `#r` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="dbfd8-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="dbfd8-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-126">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="dbfd8-127">Jak vidíte, budete muset zadat relativní cestu k knihovnu DLL a úplný název knihovny DLL, která nemusí být přesně stejný jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="dbfd8-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="dbfd8-128">Cesta bude obsahovat framework verze a případně číslo verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="dbfd8-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="dbfd8-129">Pokud chcete vyhledat všechny nainstalované sestavení, můžete použít přibližně takto na příkazovém řádku Windows:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="dbfd8-130">Nebo v prostředí Unix něco podobné výjimky:</span><span class="sxs-lookup"><span data-stu-id="dbfd8-130">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="dbfd8-131">Tím získáte cesty na nainstalovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="dbfd8-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="dbfd8-132">Odtud můžete vybrat správnou cestu pro vaši verzi framework.</span><span class="sxs-lookup"><span data-stu-id="dbfd8-132">From there, you can select the correct path for your framework version.</span></span>
