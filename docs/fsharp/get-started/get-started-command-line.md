---
title: 'Začínáme s F # pomocí nástroje příkazového řádku'
description: 'Naučte se vytvářet jednoduché řešení vícenásobného projektu na F # pomocí rozhraní příkazového řádku .NET Core v jakémkoliv operačním systému (Windows, systému macOs nebo Linux).'
author: cartermp
ms.author: phcart
ms.date: 03/26/2018
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 767385be605d863644db563a2e86a41ca80527c4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="7b758-103">Začínáme s F # pomocí rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="7b758-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="7b758-104">Tento článek popisuje, jak můžete začít používat v jakémkoliv operačním systému (Windows, systému macOS nebo Linux) pomocí rozhraní příkazového řádku .NET Core a F #.</span><span class="sxs-lookup"><span data-stu-id="7b758-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="7b758-105">Projde vytváření řešení vícenásobného projektu s knihovnou tříd, která je volána konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b758-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7b758-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b758-106">Prerequisites</span></span>

<span data-ttu-id="7b758-107">Pokud chcete začít, musíte nainstalovat [.NET Core SDK 1.0 nebo novější](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="7b758-107">To begin, you must install the [.NET Core SDK 1.0 or later](https://www.microsoft.com/net/download/).</span></span> <span data-ttu-id="7b758-108">Není nutné odinstalovat předchozí verzi rozhraní .NET Core SDK, jako podporuje instalace vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="7b758-108">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="7b758-109">Tento článek předpokládá, že znáte postup pomocí příkazového řádku a máte upřednostňované textový editor.</span><span class="sxs-lookup"><span data-stu-id="7b758-109">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="7b758-110">Pokud už nepoužíváte, [Visual Studio Code](https://code.visualstudio.com) představuje skvělou možnost jako textový editor pro F #.</span><span class="sxs-lookup"><span data-stu-id="7b758-110">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="7b758-111">Chcete-li získat Super funkcí, jako je technologie IntelliSense, lepší zvýraznění syntaxe a další, můžete stáhnout [Ionide rozšíření](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="7b758-111">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="7b758-112">Vytvoření jednoduché řešení vícenásobného projektu</span><span class="sxs-lookup"><span data-stu-id="7b758-112">Build a simple multi-project solution</span></span>

<span data-ttu-id="7b758-113">Otevřete příkazový řádek nebo terminál a použít [dotnet nové](../../core/tools/dotnet-new.md) příkaz pro vytvoření nového souboru řešení s názvem `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="7b758-113">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="7b758-114">Po spuštění předchozí příkaz vytváří následující adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="7b758-114">The following directory structure is produced after running the previous command:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="7b758-115">Zápis knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="7b758-115">Write a class library</span></span>

<span data-ttu-id="7b758-116">Přejděte do adresáře *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="7b758-116">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="7b758-117">Použití `dotnet new` příkaz, vytvořte v projektu knihovny tříd **src** složku s názvem knihovny.</span><span class="sxs-lookup"><span data-stu-id="7b758-117">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```
dotnet new lib -lang F# -o src/Library
```

<span data-ttu-id="7b758-118">Po spuštění předchozí příkaz vytváří následující adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="7b758-118">The following directory structure is produced after running the previous command:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="7b758-119">Nahraďte obsah `Library.fs` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="7b758-119">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="7b758-120">Přidejte balíček Newtonsoft.Json NuGet do projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="7b758-120">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="7b758-121">Přidat `Library` projektu do `FSNetCore` řešení pomocí [dotnet SLN – přidat](../../core/tools/dotnet-sln.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="7b758-121">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="7b758-122">Obnovit pomocí závislostí NuGet `dotnet restore` příkazu ([viz Poznámka](#dotnet-restore-note)) a spusťte `dotnet build` a tím projekt sestavit.</span><span class="sxs-lookup"><span data-stu-id="7b758-122">Restore the NuGet dependencies using the `dotnet restore` command ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="7b758-123">Zápis konzolovou aplikaci, která využívá knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="7b758-123">Write a console application that consumes the class library</span></span>

<span data-ttu-id="7b758-124">Použití `dotnet new` příkaz, vytvořte konzolovou aplikaci v **src** složku s názvem aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b758-124">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="7b758-125">Po spuštění předchozí příkaz vytváří následující adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="7b758-125">The following directory structure is produced after running the previous command:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="7b758-126">Nahraďte obsah `Program.fs` soubor s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="7b758-126">Replace the contents of the `Program.fs` file with the following code:</span></span>

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    argv
    |> Array.map getJsonNetJson
    |> Array.iter (printfn "%s")

    0 // return an integer exit code
```

<span data-ttu-id="7b758-127">Přidat odkaz na `Library` projektu pomocí [dotnet přidat odkaz](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="7b758-127">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="7b758-128">Přidat `App` projektu do `FSNetCore` řešení pomocí `dotnet sln add` příkaz:</span><span class="sxs-lookup"><span data-stu-id="7b758-128">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="7b758-129">Obnovte závislosti NuGet `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) a spusťte `dotnet build` a tím projekt sestavit.</span><span class="sxs-lookup"><span data-stu-id="7b758-129">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="7b758-130">Změnit adresář `src/App` konzole projektu a spusťte projekt předávání `Hello World` jako argumenty:</span><span class="sxs-lookup"><span data-stu-id="7b758-130">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```
cd src/App
dotnet run Hello World
```

<span data-ttu-id="7b758-131">Byste měli vidět následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="7b758-131">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]