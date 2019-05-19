---
title: Pomocí správy balíčků s F# pro Azure
description: Umožňuje spravovat stáhnout nebo Nuget F# Azure závislosti
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: b180024e2276a2fd7786f35cb922b1aa1d91f0ad
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880022"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="69ab9-103">Správa balíčků pro závislosti Azure F#</span><span class="sxs-lookup"><span data-stu-id="69ab9-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="69ab9-104">Získání balíčky pro vývoj pro Azure je jednoduché, když pomocí Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="69ab9-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="69ab9-105">Jsou dvě možnosti [Stáhnout](https://fsprojects.github.io/Paket/) a [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="69ab9-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="69ab9-106">Použití stáhnout</span><span class="sxs-lookup"><span data-stu-id="69ab9-106">Using Paket</span></span>

<span data-ttu-id="69ab9-107">Pokud používáte [Stáhnout](https://fsprojects.github.io/Paket/) jako správce závislostí můžete použít `paket.exe` nástroj Přidat závislosti Azure.</span><span class="sxs-lookup"><span data-stu-id="69ab9-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="69ab9-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="69ab9-108">For example:</span></span>

```
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="69ab9-109">Nebo v případě, že používáte [Mono](https://www.mono-project.com/) pro vývoj pro různé platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="69ab9-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="69ab9-110">Tato možnost přidá `WindowsAzure.Storage` sady závislosti balíčků pro projekt v aktuálním adresáři, chcete-li upravit `paket.dependencies` souboru a stáhněte balíček.</span><span class="sxs-lookup"><span data-stu-id="69ab9-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="69ab9-111">Pokud jste dříve nastavili závislosti nebo jsou práci s projektem, ve kterém byly nastaveny závislosti jiný vývojář, můžete vyřešit a nainstalujte závislosti místně takto:</span><span class="sxs-lookup"><span data-stu-id="69ab9-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```
> paket install
```

<span data-ttu-id="69ab9-112">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="69ab9-112">Or, for Mono development:</span></span>

```
> mono paket.exe install
```

<span data-ttu-id="69ab9-113">Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi takto:</span><span class="sxs-lookup"><span data-stu-id="69ab9-113">You can update all your package dependencies to the latest version like this:</span></span>

```
> paket update
```

<span data-ttu-id="69ab9-114">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="69ab9-114">Or, for Mono development:</span></span>

```
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="69ab9-115">Pomocí nástroje Nuget</span><span class="sxs-lookup"><span data-stu-id="69ab9-115">Using Nuget</span></span>

<span data-ttu-id="69ab9-116">Pokud používáte [NuGet](https://www.nuget.org/) jako správce závislostí můžete použít `nuget.exe` nástroj Přidat závislosti Azure.</span><span class="sxs-lookup"><span data-stu-id="69ab9-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="69ab9-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="69ab9-117">For example:</span></span>

```
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="69ab9-118">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="69ab9-118">Or, for Mono development:</span></span>

```
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="69ab9-119">Tato možnost přidá `WindowsAzure.Storage` do sady závislosti balíčků pro projekt v aktuálním adresáři a stažení balíčku.</span><span class="sxs-lookup"><span data-stu-id="69ab9-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="69ab9-120">Pokud jste dříve nastavili závislosti nebo jsou práci s projektem, ve kterém byly nastaveny závislosti jiný vývojář, můžete vyřešit a nainstalujte závislosti místně takto:</span><span class="sxs-lookup"><span data-stu-id="69ab9-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```
> nuget restore
```

<span data-ttu-id="69ab9-121">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="69ab9-121">Or, for Mono development:</span></span>

```
> mono nuget.exe restore
```

<span data-ttu-id="69ab9-122">Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi takto:</span><span class="sxs-lookup"><span data-stu-id="69ab9-122">You can update all your package dependencies to the latest version like this:</span></span>

```
> nuget update
```

<span data-ttu-id="69ab9-123">Nebo pro Mono vývoj:</span><span class="sxs-lookup"><span data-stu-id="69ab9-123">Or, for Mono development:</span></span>

```
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="69ab9-124">Odkazování na sestavení</span><span class="sxs-lookup"><span data-stu-id="69ab9-124">Referencing Assemblies</span></span>

<span data-ttu-id="69ab9-125">Chcete-li použít své balíčky do vašeho F# skriptu, musíte odkazovat sestavení součástí balíčků pomocí `#r` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="69ab9-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="69ab9-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="69ab9-126">For example:</span></span>

```
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="69ab9-127">Jak je vidět, bude nutné zadat relativní cestu knihovny DLL a úplný název knihovny DLL, která nemusí být přesně stejný jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="69ab9-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="69ab9-128">Verze rozhraní framework a případně číslo verze balíčku, bude obsahovat cestu.</span><span class="sxs-lookup"><span data-stu-id="69ab9-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="69ab9-129">Najít nainstalovaná sestavení, můžete použít asi takhle nějak. na příkazovém řádku Windows:</span><span class="sxs-lookup"><span data-stu-id="69ab9-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="69ab9-130">Nebo v prostředí systému Unix, přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="69ab9-130">Or in a Unix shell, something like this:</span></span>

```
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="69ab9-131">Tím získáte cesty k nainstalovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="69ab9-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="69ab9-132">Odtud můžete vybrat správnou cestu pro vaši verzi rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="69ab9-132">From there, you can select the correct path for your framework version.</span></span>
