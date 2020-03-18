---
title: Vytvoření balíčku NuGet pomocí rozhraní CLI jádra .NET
description: Zjistěte, jak vytvořit balíček NuGet pomocí příkazu 'dotnet pack'.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920923"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a><span data-ttu-id="23786-103">Jak vytvořit balíček NuGet s rozhraním .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="23786-103">How to create a NuGet package with the .NET Core CLI</span></span>

> [!NOTE]
> <span data-ttu-id="23786-104">Následující text ukazuje ukázky příkazového řádku pomocí Unixu.</span><span class="sxs-lookup"><span data-stu-id="23786-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="23786-105">Příkaz, `dotnet pack` jak je zde uvedeno, funguje stejným způsobem v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="23786-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="23786-106">Očekává se, že knihovny .NET Standard a .NET Core budou distribuovány jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="23786-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="23786-107">To je ve skutečnosti, jak jsou distribuovány a spotřebovány všechny knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="23786-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="23786-108">To se nejsnadněji `dotnet pack` provádí pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="23786-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="23786-109">Představte si, že jste právě napsali úžasnou novou knihovnu, kterou chcete distribuovat přes NuGet.</span><span class="sxs-lookup"><span data-stu-id="23786-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="23786-110">Můžete vytvořit balíček NuGet s nástroji pro různé platformy k tomu přesně to!</span><span class="sxs-lookup"><span data-stu-id="23786-110">You can create a NuGet package with cross-platform tools to do exactly that!</span></span> <span data-ttu-id="23786-111">Následující příklad předpokládá knihovnu s názvem `netstandard1.0` **SuperAwesomeLibrary,** která cílí .</span><span class="sxs-lookup"><span data-stu-id="23786-111">The following example assumes a library called **SuperAwesomeLibrary** that targets `netstandard1.0`.</span></span>

<span data-ttu-id="23786-112">Pokud máte přenosné závislosti, to znamená projekt, který závisí na jiném balíčku, ujistěte se, že obnovit balíčky pro celé řešení s `dotnet restore` příkazem před vytvořením balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="23786-112">If you have transitive dependencies, that is, a project that depends on another package, make sure to restore packages for the entire solution with the `dotnet restore` command before you create a NuGet package.</span></span> <span data-ttu-id="23786-113">Pokud tak neučiníte, `dotnet pack` příkaz nebude fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="23786-113">Failing to do so will result in the `dotnet pack` command not working properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="23786-114">Po obnovení balíčků můžete přejít do adresáře, kde knihovna žije:</span><span class="sxs-lookup"><span data-stu-id="23786-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="23786-115">Pak je to jen jeden příkaz z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="23786-115">Then it's just a single command from the command line:</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="23786-116">Složka */bin/Debug* bude nyní vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="23786-116">Your */bin/Debug* folder will now look like this:</span></span>

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="23786-117">Tím se vytvoří balíček, který je možné ladit.</span><span class="sxs-lookup"><span data-stu-id="23786-117">This produces a package that is capable of being debugged.</span></span> <span data-ttu-id="23786-118">Pokud chcete vytvořit balíček NuGet s binárními soubory verze, `--configuration` stačí `-c`přidat (nebo `release` ) přepínač a použít jako argument.</span><span class="sxs-lookup"><span data-stu-id="23786-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```dotnetcli
dotnet pack --configuration release
```

<span data-ttu-id="23786-119">Složka */bin* bude nyní obsahovat složku *vydání* obsahující balíček NuGet s binárními soubory verzí:</span><span class="sxs-lookup"><span data-stu-id="23786-119">Your */bin* folder will now have a *release* folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="23786-120">A nyní máte potřebné soubory pro publikování balíčku NuGet!</span><span class="sxs-lookup"><span data-stu-id="23786-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="23786-121">Nepleťte si `dotnet pack` s`dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="23786-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="23786-122">Je důležité si uvědomit, že `dotnet publish` v žádném okamžiku je příkaz zapojen.</span><span class="sxs-lookup"><span data-stu-id="23786-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="23786-123">Příkaz `dotnet publish` je určen pro nasazení aplikací se všemi jejich závislostmi ve stejném balíčku – ne pro generování balíčku NuGet, který má být distribuován a spotřebován prostřednictvím NuGet.</span><span class="sxs-lookup"><span data-stu-id="23786-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="23786-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="23786-124">See also</span></span>

- [<span data-ttu-id="23786-125">Úvodní příručka: Vytvoření a publikování balíčku</span><span class="sxs-lookup"><span data-stu-id="23786-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
