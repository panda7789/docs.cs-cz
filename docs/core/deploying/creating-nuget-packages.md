---
title: Vytvoří balíček NuGet s nástroji .NET Core rozhraní příkazového řádku (CLI)
description: Zjistěte, jak vytvořit balíček NuGet pomocí příkazu "balíčku dotnet".
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: b86b2706968bf302a8421bcc8e12c32a97102e9e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632112"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="a6d22-103">Jak vytvořit balíček NuGet s nástroji .NET Core rozhraní příkazového řádku (CLI)</span><span class="sxs-lookup"><span data-stu-id="a6d22-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="a6d22-104">Následující obrázek znázorňuje ukázky příkazového řádku s použitím systému Unix.</span><span class="sxs-lookup"><span data-stu-id="a6d22-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="a6d22-105">`dotnet pack` Příkaz, jak je znázorněno zde funguje stejným způsobem jako na Windows.</span><span class="sxs-lookup"><span data-stu-id="a6d22-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="a6d22-106">Knihovny .NET standard a .NET Core se očekává distribuována jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="a6d22-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="a6d22-107">Toto je ve skutečnosti jak všech knihoven .NET Standard jsou distribuované a využívat.</span><span class="sxs-lookup"><span data-stu-id="a6d22-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="a6d22-108">Snadno to provádí pomocí `dotnet pack` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a6d22-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="a6d22-109">Představte si, že jste napsali úžasnou novou knihovnu, která chcete distribuovat přes NuGet.</span><span class="sxs-lookup"><span data-stu-id="a6d22-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="a6d22-110">Můžete vytvořit balíček NuGet pomocí nástrojů pro různé platformy k tomu přesně!</span><span class="sxs-lookup"><span data-stu-id="a6d22-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span> <span data-ttu-id="a6d22-111">V následujícím příkladu se předpokládá knihovnu s názvem **SuperAwesomeLibrary** cíle, které `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="a6d22-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="a6d22-112">Pokud máte přechodné závislosti; To znamená, že projekt, který závisí na jiném balíčku, budete muset Ujistěte se, že k obnovení balíčků pro celé řešení s `dotnet restore` příkaz před vytvořením balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="a6d22-112">If you have transitive dependencies; that is, a project which depends on another package, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span> <span data-ttu-id="a6d22-113">Pokud tak neučiníte způsobí `dotnet pack` příkaz nebude správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="a6d22-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="a6d22-114">Až se ujistíte, obnovení balíčků, můžete přejít k adresáři, kde se nachází knihovny:</span><span class="sxs-lookup"><span data-stu-id="a6d22-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="a6d22-115">Pak je pouze jediný příkaz z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="a6d22-115">Then it's just a single command from the command line:</span></span>

```console
dotnet pack
```

<span data-ttu-id="a6d22-116">Vaše `/bin/Debug` složky se teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="a6d22-116">Your `/bin/Debug` folder will now look like this:</span></span>

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="a6d22-117">Mějte na paměti, vznikne balíčku, který je schopen právě laděny.</span><span class="sxs-lookup"><span data-stu-id="a6d22-117">Note that this will produce a package which is capable of being debugged.</span></span> <span data-ttu-id="a6d22-118">Pokud chcete vytvořit balíček NuGet s binárními soubory verze, všechno, co potřebujete udělat je přidat `--configuration` (nebo `-c`) přepněte a použít `release` jako argument.</span><span class="sxs-lookup"><span data-stu-id="a6d22-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```console
dotnet pack --configuration release
```

<span data-ttu-id="a6d22-119">Vaše `/bin` složky budou mít `release` složku, která obsahuje váš balíček NuGet s binárními soubory verze:</span><span class="sxs-lookup"><span data-stu-id="a6d22-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="a6d22-120">A teď máte soubory potřebné k publikování balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="a6d22-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="a6d22-121">Nepleťte si `dotnet pack` s `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="a6d22-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="a6d22-122">Je důležité si uvědomit, že v žádném bodě `dotnet publish` příkaz nepodílí.</span><span class="sxs-lookup"><span data-stu-id="a6d22-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="a6d22-123">`dotnet publish` Příkaz slouží k nasazení aplikace se všemi jejich závislosti ve stejné sadě – ne pro generování balíčku NuGet k distribuci a spotřebované prostřednictvím balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="a6d22-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6d22-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6d22-124">See also</span></span>

- [<span data-ttu-id="a6d22-125">Rychlý start: Vytvoření a publikování balíčku</span><span class="sxs-lookup"><span data-stu-id="a6d22-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
