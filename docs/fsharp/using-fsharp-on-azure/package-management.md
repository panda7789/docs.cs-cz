---
title: Použití Správa balíčků s F# pro Azure
description: Správa F# závislostí Azure pomocí paket nebo NuGet
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 4aa32ace91f30d0e43b9c40067f5f0f456cc4069
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214223"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="f56f9-103">Správa balíčků pro závislosti Azure F#</span><span class="sxs-lookup"><span data-stu-id="f56f9-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="f56f9-104">Získání balíčků pro vývoj pro Azure je snadné, když použijete Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="f56f9-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="f56f9-105">Tyto dvě možnosti jsou [paket](https://fsprojects.github.io/Paket/) a [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="f56f9-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="f56f9-106">Použití paket</span><span class="sxs-lookup"><span data-stu-id="f56f9-106">Using Paket</span></span>

<span data-ttu-id="f56f9-107">Pokud jako správce závislostí používáte [paket](https://fsprojects.github.io/Paket/) , můžete použít `paket.exe` nástroj k přidání závislostí Azure.</span><span class="sxs-lookup"><span data-stu-id="f56f9-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="f56f9-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f56f9-108">For example:</span></span>

```console
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="f56f9-109">Nebo, pokud používáte [mono](https://www.mono-project.com/) pro vývoj pro různé platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="f56f9-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="f56f9-110">Tato akce přidá `WindowsAzure.Storage` do sady závislostí balíčku pro projekt v aktuálním adresáři, `paket.dependencies` upraví soubor a stáhne balíček.</span><span class="sxs-lookup"><span data-stu-id="f56f9-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="f56f9-111">Pokud jste dříve nastavili závislosti nebo pracujete s projektem, kde závislosti byly nastaveny jiným vývojářem, můžete závislosti v místním prostředí vyřešit a nainstalovat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f56f9-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> paket install
```

<span data-ttu-id="f56f9-112">Nebo pro vývoj mono:</span><span class="sxs-lookup"><span data-stu-id="f56f9-112">Or, for Mono development:</span></span>

```console
> mono paket.exe install
```

<span data-ttu-id="f56f9-113">Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi, například:</span><span class="sxs-lookup"><span data-stu-id="f56f9-113">You can update all your package dependencies to the latest version like this:</span></span>

```console
> paket update
```

<span data-ttu-id="f56f9-114">Nebo pro vývoj mono:</span><span class="sxs-lookup"><span data-stu-id="f56f9-114">Or, for Mono development:</span></span>

```console
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="f56f9-115">Použití NuGet</span><span class="sxs-lookup"><span data-stu-id="f56f9-115">Using Nuget</span></span>

<span data-ttu-id="f56f9-116">Pokud jako správce závislostí používáte [NuGet](https://www.nuget.org/) , můžete k přidání závislostí Azure `nuget.exe` použít tento nástroj.</span><span class="sxs-lookup"><span data-stu-id="f56f9-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="f56f9-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f56f9-117">For example:</span></span>

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="f56f9-118">Nebo pro vývoj mono:</span><span class="sxs-lookup"><span data-stu-id="f56f9-118">Or, for Mono development:</span></span>

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="f56f9-119">Tím se přidá `WindowsAzure.Storage` do sady závislostí balíčku pro projekt v aktuálním adresáři a stáhne se balíček.</span><span class="sxs-lookup"><span data-stu-id="f56f9-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="f56f9-120">Pokud jste dříve nastavili závislosti nebo pracujete s projektem, kde závislosti byly nastaveny jiným vývojářem, můžete závislosti v místním prostředí vyřešit a nainstalovat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f56f9-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> nuget restore
```

<span data-ttu-id="f56f9-121">Nebo pro vývoj mono:</span><span class="sxs-lookup"><span data-stu-id="f56f9-121">Or, for Mono development:</span></span>

```console
> mono nuget.exe restore
```

<span data-ttu-id="f56f9-122">Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi, například:</span><span class="sxs-lookup"><span data-stu-id="f56f9-122">You can update all your package dependencies to the latest version like this:</span></span>

```console
> nuget update
```

<span data-ttu-id="f56f9-123">Nebo pro vývoj mono:</span><span class="sxs-lookup"><span data-stu-id="f56f9-123">Or, for Mono development:</span></span>

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="f56f9-124">Odkazování na sestavení</span><span class="sxs-lookup"><span data-stu-id="f56f9-124">Referencing Assemblies</span></span>

<span data-ttu-id="f56f9-125">Aby bylo možné používat balíčky ve F# skriptu, je nutné odkazovat na sestavení zahrnutá v balíčcích pomocí `#r` direktivy.</span><span class="sxs-lookup"><span data-stu-id="f56f9-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="f56f9-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f56f9-126">For example:</span></span>

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="f56f9-127">Jak vidíte, budete muset zadat relativní cestu k souboru DLL a úplný název knihovny DLL, který nemusí být přesně stejný jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="f56f9-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="f56f9-128">Cesta bude obsahovat verzi rozhraní a případně číslo verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="f56f9-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="f56f9-129">Chcete-li najít všechna nainstalovaná sestavení, můžete použít něco podobného na příkazovém řádku systému Windows:</span><span class="sxs-lookup"><span data-stu-id="f56f9-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="f56f9-130">Nebo v prostředí UNIX něco podobného:</span><span class="sxs-lookup"><span data-stu-id="f56f9-130">Or in a Unix shell, something like this:</span></span>

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="f56f9-131">To vám poskytne cesty k nainstalovaným sestavením.</span><span class="sxs-lookup"><span data-stu-id="f56f9-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="f56f9-132">Odtud můžete vybrat správnou cestu k vaší verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f56f9-132">From there, you can select the correct path for your framework version.</span></span>
