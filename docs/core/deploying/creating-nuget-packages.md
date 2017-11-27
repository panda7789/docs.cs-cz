---
title: "Vytvoření balíčku NuGet se pro různé platformy nástroje"
description: "Naučte se vytvořit balíček NuGet příkazem 'dotnet pack'."
keywords: "Rozhraní .NET, .NET core NuGet"
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2f0415c1-110b-433d-87c1-ae3d543a8844
ms.openlocfilehash: a5738a4f3755a959660db4be683677673af61ef9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a><span data-ttu-id="45737-104">Postup vytvoření balíčku NuGet se pro různé platformy nástroje</span><span class="sxs-lookup"><span data-stu-id="45737-104">How to Create a NuGet Package with Cross Platform Tools</span></span>

> [!NOTE]
> <span data-ttu-id="45737-105">Následující obrázek znázorňuje příkazového řádku vzorků použití systému Unix.</span><span class="sxs-lookup"><span data-stu-id="45737-105">The following shows command-line samples using Unix.</span></span>  <span data-ttu-id="45737-106">`dotnet pack` Příkaz, jak je vidět tady funguje stejným způsobem jako v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="45737-106">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="45737-107">Pro rozhraní .NET Core 1.0 knihovny budou distribuována jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="45737-107">For .NET Core 1.0, libraries are expected to be distributed as NuGet packages.</span></span>  <span data-ttu-id="45737-108">Toto je ve skutečnosti jak všech knihoven .NET Standard jsou distribuované a využívat.</span><span class="sxs-lookup"><span data-stu-id="45737-108">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span>  <span data-ttu-id="45737-109">Snadno to provádí pomocí `dotnet pack` příkaz.</span><span class="sxs-lookup"><span data-stu-id="45737-109">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="45737-110">Představte si, že jste napsali Super novou knihovnu, která chcete distribuovat přes NuGet.</span><span class="sxs-lookup"><span data-stu-id="45737-110">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span>  <span data-ttu-id="45737-111">Můžete vytvořit balíček NuGet se mezi nástrojů platformy provedete přesně to!</span><span class="sxs-lookup"><span data-stu-id="45737-111">You can create a NuGet package with cross platform tools to do exactly that!</span></span>  <span data-ttu-id="45737-112">Následující příklad předpokládá knihovnu volat **SuperAwesomeLibrary** které cíle `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="45737-112">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="45737-113">Pokud máte přenositelné závislosti; To znamená, projektu, což závisí na jiného projektu, budete muset nezapomeňte obnovení balíčků pro celé řešení pomocí `dotnet restore` příkazu před vytvořením balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="45737-113">If you have transitive dependencies; that is, a project which depends on another project, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span>  <span data-ttu-id="45737-114">Tak neučiníte bude mít za následek `dotnet pack` příkaz nebude správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="45737-114">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


<span data-ttu-id="45737-115">Po zajištění obnovení balíčků, můžete přejít k adresáři, kde je umístěn knihovny:</span><span class="sxs-lookup"><span data-stu-id="45737-115">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

`$ cd src/SuperAwesomeLibrary`

<span data-ttu-id="45737-116">Pak je jenom jeden příkaz z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="45737-116">Then it's just a single command from the command line:</span></span>
    
`$ dotnet pack`

<span data-ttu-id="45737-117">Vaše `/bin/Debug` složky bude nyní vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="45737-117">Your `/bin/Debug` folder will now look like this:</span></span>

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="45737-118">Všimněte si, že vznikne balíčku, který je schopen laděné.</span><span class="sxs-lookup"><span data-stu-id="45737-118">Note that this will produce a package which is capable of being debugged.</span></span>  <span data-ttu-id="45737-119">Pokud chcete vytvořit balíček NuGet s verzi binárních souborů, všechny musíte udělat je přidat `-c` / `--configuration` přepínače a používat `release` jako argument.</span><span class="sxs-lookup"><span data-stu-id="45737-119">If you want to build a NuGet package with release binaries, all you need to do is add the `-c`/`--configuration` switch and use `release` as the argument.</span></span>

`$ dotnet pack --configuration release`

<span data-ttu-id="45737-120">Vaše `/bin` složky teď bude mít `release` složku obsahující váš balíček NuGet s verzi binárních souborů:</span><span class="sxs-lookup"><span data-stu-id="45737-120">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="45737-121">A teď máte potřebné soubory pro publikování balíčku NuGet!</span><span class="sxs-lookup"><span data-stu-id="45737-121">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="45737-122">Nepleťte si `dotnet pack` s`dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="45737-122">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="45737-123">Je důležité si uvědomit, že v žádný bod se `dotnet publish` příkaz zahrnuta.</span><span class="sxs-lookup"><span data-stu-id="45737-123">It is important to note that at no point is the `dotnet publish` command involved.</span></span>  <span data-ttu-id="45737-124">`dotnet publish` Je určen pro nasazení aplikací s všechny závislé položky v sadě stejné - není pro generování balíčku NuGet pro distribuované a využívat prostřednictvím balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="45737-124">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -  not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>
