---
title: "Pomocí správy balíčků F # pro Azure."
description: "Ke správě závislosti F # Azure použijte stáhnout nebo Nuget"
keywords: "Visual f #, f #, funkční programování, .NET, .NET Core, Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dd32ef9c-5416-467e-9fa3-c9ee3bb08456
ms.openlocfilehash: 22dc94ea69e0dfb95e22da4bc64ce915398190d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="ac197-104">Balíček správy pro závislosti Azure F #</span><span class="sxs-lookup"><span data-stu-id="ac197-104">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="ac197-105">Získání balíčky pro vývoj pro Azure je snadný při použití Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="ac197-105">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="ac197-106">Dvě možnosti jsou [Stáhnout](https://fsprojects.github.io/Paket/) a [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="ac197-106">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="ac197-107">Pomocí stáhnout</span><span class="sxs-lookup"><span data-stu-id="ac197-107">Using Paket</span></span>

<span data-ttu-id="ac197-108">Pokud používáte [Stáhnout](https://fsprojects.github.io/Paket/) jako závislost nadřízeného, můžete použít `paket.exe` nástroje pro přidání Azure závislosti.</span><span class="sxs-lookup"><span data-stu-id="ac197-108">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="ac197-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ac197-109">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="ac197-110">Nebo, pokud používáte [Mono](http://www.mono-project.com/) pro vývoj pro různé platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="ac197-110">Or, if you're using [Mono](http://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="ac197-111">Bude přidáno `WindowsAzure.Storage` množina závislosti balíčků pro projekt v aktuálním adresáři, upravte `paket.dependencies` souboru a stáhněte si balíček.</span><span class="sxs-lookup"><span data-stu-id="ac197-111">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="ac197-112">Pokud jste dříve nastavili závislosti nebo práci s projektem kde závislosti již byly vytvořeny pomocí jiné vývojáře, můžete vyřešit a instalaci závislostí místně takto:</span><span class="sxs-lookup"><span data-stu-id="ac197-112">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="ac197-113">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="ac197-113">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="ac197-114">Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi takto:</span><span class="sxs-lookup"><span data-stu-id="ac197-114">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="ac197-115">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="ac197-115">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="ac197-116">Pomocí nástroje Nuget</span><span class="sxs-lookup"><span data-stu-id="ac197-116">Using Nuget</span></span>

<span data-ttu-id="ac197-117">Pokud používáte [NuGet](https://www.nuget.org/) jako závislost nadřízeného, můžete použít `nuget.exe` nástroje pro přidání Azure závislosti.</span><span class="sxs-lookup"><span data-stu-id="ac197-117">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="ac197-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ac197-118">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="ac197-119">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="ac197-119">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="ac197-120">Bude přidáno `WindowsAzure.Storage` množina závislosti balíčků pro projekt v aktuálním adresáři a stažení balíčku.</span><span class="sxs-lookup"><span data-stu-id="ac197-120">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="ac197-121">Pokud jste dříve nastavili závislosti nebo práci s projektem kde závislosti již byly vytvořeny pomocí jiné vývojáře, můžete vyřešit a instalaci závislostí místně takto:</span><span class="sxs-lookup"><span data-stu-id="ac197-121">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="ac197-122">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="ac197-122">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="ac197-123">Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi takto:</span><span class="sxs-lookup"><span data-stu-id="ac197-123">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="ac197-124">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="ac197-124">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="ac197-125">Odkazování na sestavení</span><span class="sxs-lookup"><span data-stu-id="ac197-125">Referencing Assemblies</span></span>

<span data-ttu-id="ac197-126">Chcete-li použít vlastních balíčků ve vašem skriptu F #, je třeba odkazovat sestavení součástí balíčků pomocí `#r` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="ac197-126">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="ac197-127">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ac197-127">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="ac197-128">Jak vidíte, budete muset zadat relativní cestu k knihovnu DLL a úplný název knihovny DLL, která nemusí být přesně stejný jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="ac197-128">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="ac197-129">Cesta bude obsahovat framework verze a případně číslo verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="ac197-129">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="ac197-130">Pokud chcete vyhledat všechny nainstalované sestavení, můžete použít přibližně takto na příkazovém řádku Windows:</span><span class="sxs-lookup"><span data-stu-id="ac197-130">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="ac197-131">Nebo v prostředí Unix něco podobné výjimky:</span><span class="sxs-lookup"><span data-stu-id="ac197-131">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="ac197-132">Tím získáte cesty na nainstalovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="ac197-132">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="ac197-133">Odtud můžete vybrat správnou cestu pro vaši verzi framework.</span><span class="sxs-lookup"><span data-stu-id="ac197-133">From there, you can select the correct path for your framework version.</span></span>
