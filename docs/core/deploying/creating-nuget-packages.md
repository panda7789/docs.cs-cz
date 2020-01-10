---
title: Vytvoření balíčku NuGet pomocí .NET Core CLI
description: Naučte se vytvořit balíček NuGet pomocí příkazu dotnet Pack.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: ddc19faa7547637036686146f8600f40713541a8
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740862"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="0d98c-103">Vytvoření balíčku NuGet pomocí nástrojů rozhraní příkazového řádku (CLI) .NET Core</span><span class="sxs-lookup"><span data-stu-id="0d98c-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="0d98c-104">Následující příklad ukazuje ukázky příkazového řádku v systému UNIX.</span><span class="sxs-lookup"><span data-stu-id="0d98c-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="0d98c-105">Příkaz `dotnet pack`, jak je znázorněno zde, funguje stejně jako v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0d98c-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="0d98c-106">Očekává se, že jsou knihovny .NET Standard a .NET Core distribuované jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="0d98c-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="0d98c-107">To je fakt, jak jsou distribuovány a spotřebovány všechny knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0d98c-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="0d98c-108">Tato možnost je nejsnáze hotová pomocí příkazu `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="0d98c-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="0d98c-109">Představte si, že jste právě napsali Super novou knihovnu, kterou byste chtěli distribuovat přes NuGet.</span><span class="sxs-lookup"><span data-stu-id="0d98c-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="0d98c-110">Můžete vytvořit balíček NuGet pomocí nástrojů pro různé platformy, aby to přesně odpovídalo!</span><span class="sxs-lookup"><span data-stu-id="0d98c-110">You can create a NuGet package with cross-platform tools to do exactly that!</span></span> <span data-ttu-id="0d98c-111">Následující příklad předpokládá knihovnu s názvem **SuperAwesomeLibrary** , která cílí na `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="0d98c-111">The following example assumes a library called **SuperAwesomeLibrary** that targets `netstandard1.0`.</span></span>

<span data-ttu-id="0d98c-112">Pokud máte přenosné závislosti, tedy projekt, který závisí na jiném balíčku, nezapomeňte obnovit balíčky pro celé řešení pomocí příkazu `dotnet restore` před vytvořením balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="0d98c-112">If you have transitive dependencies, that is, a project that depends on another package, make sure to restore packages for the entire solution with the `dotnet restore` command before you create a NuGet package.</span></span> <span data-ttu-id="0d98c-113">Pokud to neuděláte, dojde k tomu, že příkaz `dotnet pack` nefunguje správně.</span><span class="sxs-lookup"><span data-stu-id="0d98c-113">Failing to do so will result in the `dotnet pack` command not working properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="0d98c-114">Po obnovení balíčků můžete přejít do adresáře, kde je knihovna umístěná:</span><span class="sxs-lookup"><span data-stu-id="0d98c-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="0d98c-115">Pak se jedná jenom o jediný příkaz z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="0d98c-115">Then it's just a single command from the command line:</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="0d98c-116">Vaše složka */bin/Debug* bude nyní vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="0d98c-116">Your */bin/Debug* folder will now look like this:</span></span>

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="0d98c-117">Tím se vytvoří balíček, který je schopný ladit.</span><span class="sxs-lookup"><span data-stu-id="0d98c-117">This produces a package that is capable of being debugged.</span></span> <span data-ttu-id="0d98c-118">Pokud chcete vytvořit balíček NuGet s binárními soubory vydání, stačí přidat přepínač `--configuration` (nebo `-c`) a jako argument použít `release`.</span><span class="sxs-lookup"><span data-stu-id="0d98c-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```dotnetcli
dotnet pack --configuration release
```

<span data-ttu-id="0d98c-119">Složka */bin* nyní bude obsahovat složku pro *vydání* obsahující balíček NuGet s binárními soubory vydání:</span><span class="sxs-lookup"><span data-stu-id="0d98c-119">Your */bin* folder will now have a *release* folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="0d98c-120">A teď máte potřebné soubory pro publikování balíčku NuGet!</span><span class="sxs-lookup"><span data-stu-id="0d98c-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="0d98c-121">Nezaměňujte `dotnet pack` s `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="0d98c-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="0d98c-122">Je důležité si uvědomit, že v žádném okamžiku se jedná o `dotnet publish` příkaz.</span><span class="sxs-lookup"><span data-stu-id="0d98c-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="0d98c-123">Příkaz `dotnet publish` slouží k nasazení aplikací se všemi jejich závislostmi ve stejné sadě – ne pro vygenerování balíčku NuGet, který se má distribuovat a spotřebovat přes NuGet.</span><span class="sxs-lookup"><span data-stu-id="0d98c-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d98c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d98c-124">See also</span></span>

- [<span data-ttu-id="0d98c-125">Rychlý Start: vytvoření a publikování balíčku</span><span class="sxs-lookup"><span data-stu-id="0d98c-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
