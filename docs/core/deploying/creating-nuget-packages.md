---
title: Vytvoření balíčku NuGet pomocí nástrojů pro různé platformy
description: Zjistěte, jak vytvořit balíček NuGet pomocí příkazu "balíčku dotnet".
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 0be8d302568bc08d2c3dacfdf5738eff4b97d4b2
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2018
ms.locfileid: "48848098"
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a><span data-ttu-id="52a27-103">Vytvoření balíčku NuGet pomocí nástrojů pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="52a27-103">How to Create a NuGet Package with Cross Platform Tools</span></span>

> [!NOTE]
> <span data-ttu-id="52a27-104">Následující obrázek znázorňuje ukázky příkazového řádku s použitím systému Unix.</span><span class="sxs-lookup"><span data-stu-id="52a27-104">The following shows command-line samples using Unix.</span></span>  <span data-ttu-id="52a27-105">`dotnet pack` Příkaz, jak je znázorněno zde funguje stejným způsobem jako na Windows.</span><span class="sxs-lookup"><span data-stu-id="52a27-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="52a27-106">Pro .NET Core 1.0 se očekává distribuována jako balíčky NuGet knihoven.</span><span class="sxs-lookup"><span data-stu-id="52a27-106">For .NET Core 1.0, libraries are expected to be distributed as NuGet packages.</span></span>  <span data-ttu-id="52a27-107">Toto je ve skutečnosti jak všech knihoven .NET Standard jsou distribuované a využívat.</span><span class="sxs-lookup"><span data-stu-id="52a27-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span>  <span data-ttu-id="52a27-108">Snadno to provádí pomocí `dotnet pack` příkazu.</span><span class="sxs-lookup"><span data-stu-id="52a27-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="52a27-109">Představte si, že jste napsali úžasnou novou knihovnu, která chcete distribuovat přes NuGet.</span><span class="sxs-lookup"><span data-stu-id="52a27-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span>  <span data-ttu-id="52a27-110">Můžete vytvořit balíček NuGet pomocí nástrojů pro různé platformy k tomu přesně!</span><span class="sxs-lookup"><span data-stu-id="52a27-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span>  <span data-ttu-id="52a27-111">V následujícím příkladu se předpokládá knihovnu s názvem **SuperAwesomeLibrary** cíle, které `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="52a27-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="52a27-112">Pokud máte přechodné závislosti; To znamená, že projekt, který závisí na jiném balíčku, budete muset Ujistěte se, že k obnovení balíčků pro celé řešení s `dotnet restore` příkaz před vytvořením balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="52a27-112">If you have transitive dependencies; that is, a project which depends on another package, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span>  <span data-ttu-id="52a27-113">Pokud tak neučiníte způsobí `dotnet pack` příkaz nebude správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="52a27-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


<span data-ttu-id="52a27-114">Až se ujistíte, obnovení balíčků, můžete přejít k adresáři, kde se nachází knihovny:</span><span class="sxs-lookup"><span data-stu-id="52a27-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

`$ cd src/SuperAwesomeLibrary`

<span data-ttu-id="52a27-115">Pak je pouze jediný příkaz z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="52a27-115">Then it's just a single command from the command line:</span></span>
    
`$ dotnet pack`

<span data-ttu-id="52a27-116">Vaše `/bin/Debug` složky se teď měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="52a27-116">Your `/bin/Debug` folder will now look like this:</span></span>

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="52a27-117">Mějte na paměti, vznikne balíčku, který je schopen právě laděny.</span><span class="sxs-lookup"><span data-stu-id="52a27-117">Note that this will produce a package which is capable of being debugged.</span></span>  <span data-ttu-id="52a27-118">Pokud chcete vytvořit balíček NuGet s binárními soubory verze, všechno, co potřebujete udělat je přidat `-c` / `--configuration` přepnutí a použít `release` jako argument.</span><span class="sxs-lookup"><span data-stu-id="52a27-118">If you want to build a NuGet package with release binaries, all you need to do is add the `-c`/`--configuration` switch and use `release` as the argument.</span></span>

`$ dotnet pack --configuration release`

<span data-ttu-id="52a27-119">Vaše `/bin` složky budou mít `release` složku, která obsahuje váš balíček NuGet s binárními soubory verze:</span><span class="sxs-lookup"><span data-stu-id="52a27-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="52a27-120">A teď máte soubory potřebné k publikování balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="52a27-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="52a27-121">Nepleťte si `dotnet pack` s `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="52a27-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="52a27-122">Je důležité si uvědomit, že v žádném bodě `dotnet publish` příkaz nepodílí.</span><span class="sxs-lookup"><span data-stu-id="52a27-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span>  <span data-ttu-id="52a27-123">`dotnet publish` Příkaz slouží k nasazení aplikace se všemi jejich závislosti ve stejné sadě – ne pro generování balíčku NuGet k distribuci a spotřebované prostřednictvím balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="52a27-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -  not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>
