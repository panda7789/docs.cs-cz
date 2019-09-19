---
title: Vytvoření balíčku NuGet pomocí nástrojů rozhraní příkazového řádku (CLI) .NET Core
description: Naučte se vytvořit balíček NuGet pomocí příkazu dotnet Pack.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: d36a6ee7d524933577928daa9993fba8ce62f6c7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116699"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="2ae60-103">Vytvoření balíčku NuGet pomocí nástrojů rozhraní příkazového řádku (CLI) .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ae60-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="2ae60-104">Následující příklad ukazuje ukázky příkazového řádku v systému UNIX.</span><span class="sxs-lookup"><span data-stu-id="2ae60-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="2ae60-105">`dotnet pack` Příkaz, jak je znázorněno zde, funguje stejně jako v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2ae60-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="2ae60-106">Očekává se, že jsou knihovny .NET Standard a .NET Core distribuované jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="2ae60-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="2ae60-107">To je fakt, jak jsou distribuovány a spotřebovány všechny knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2ae60-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="2ae60-108">To je nejsnáze hotové `dotnet pack` pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="2ae60-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="2ae60-109">Představte si, že jste právě napsali Super novou knihovnu, kterou byste chtěli distribuovat přes NuGet.</span><span class="sxs-lookup"><span data-stu-id="2ae60-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="2ae60-110">Můžete vytvořit balíček NuGet s nástroji pro různé platformy, abyste ho mohli přesně dělat.</span><span class="sxs-lookup"><span data-stu-id="2ae60-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span> <span data-ttu-id="2ae60-111">Následující příklad předpokládá, že knihovna s názvem **SuperAwesomeLibrary** , `netstandard1.0`která cílí na.</span><span class="sxs-lookup"><span data-stu-id="2ae60-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="2ae60-112">Pokud máte přenosné závislosti; To znamená, že projekt, který závisí na jiném balíčku, budete muset před vytvořením balíčku NuGet ověřit balíčky pro celé řešení pomocí `dotnet restore` příkazu.</span><span class="sxs-lookup"><span data-stu-id="2ae60-112">If you have transitive dependencies; that is, a project which depends on another package, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span> <span data-ttu-id="2ae60-113">Pokud to neuděláte, nebudou mít `dotnet pack` příkaz správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="2ae60-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="2ae60-114">Po obnovení balíčků můžete přejít do adresáře, kde je knihovna umístěná:</span><span class="sxs-lookup"><span data-stu-id="2ae60-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="2ae60-115">Pak se jedná jenom o jediný příkaz z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="2ae60-115">Then it's just a single command from the command line:</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="2ae60-116">Vaše `/bin/Debug` složka bude nyní vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="2ae60-116">Your `/bin/Debug` folder will now look like this:</span></span>

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="2ae60-117">Všimněte si, že se tím vytvoří balíček, který je schopný ladit.</span><span class="sxs-lookup"><span data-stu-id="2ae60-117">Note that this will produce a package which is capable of being debugged.</span></span> <span data-ttu-id="2ae60-118">Pokud chcete vytvořit balíček NuGet s binárními soubory vydání, stačí přidat `--configuration` přepínač (nebo `-c`) a použít `release` ho jako argument.</span><span class="sxs-lookup"><span data-stu-id="2ae60-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```dotnetcli
dotnet pack --configuration release
```

<span data-ttu-id="2ae60-119">Vaše `/bin` složka teď bude `release` obsahovat složku obsahující balíček NuGet s binárními soubory vydání:</span><span class="sxs-lookup"><span data-stu-id="2ae60-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="2ae60-120">A teď máte potřebné soubory pro publikování balíčku NuGet!</span><span class="sxs-lookup"><span data-stu-id="2ae60-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="2ae60-121">Nepleťte `dotnet pack` si s`dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="2ae60-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="2ae60-122">Je důležité si uvědomit, že v žádném okamžiku není `dotnet publish` zahrnutý příkaz.</span><span class="sxs-lookup"><span data-stu-id="2ae60-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="2ae60-123">`dotnet publish` Příkaz slouží k nasazení aplikací se všemi jejich závislostmi ve stejné sadě, a ne pro vygenerování balíčku NuGet, který se má distribuovat a spotřebovat přes NuGet.</span><span class="sxs-lookup"><span data-stu-id="2ae60-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ae60-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ae60-124">See also</span></span>

- [<span data-ttu-id="2ae60-125">Rychlý start: Vytvoření a publikování balíčku</span><span class="sxs-lookup"><span data-stu-id="2ae60-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
