---
title: Začínáme s F# pomocí nástrojů příkazového řádku
description: Zjistěte, jak vytvoření jednoduchého řešení vícenásobného projektu F# pomocí rozhraní příkazového řádku .NET Core pro všechny operační systémy (Windows, macOs nebo Linux).
ms.date: 03/26/2018
ms.openlocfilehash: bc9b223fcf133ffe8b19d5284dcbd3c14a426235
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152096"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="867f2-103">Začínáme s F# pomocí rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="867f2-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="867f2-104">Tento článek popisuje, jak můžete začít s F# pro všechny operační systémy (Windows, macOS nebo Linux) pomocí rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="867f2-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="867f2-105">Prochází přes vytváření řešení vícenásobného projektu knihovny tříd, která je volána pomocí konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="867f2-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="867f2-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="867f2-106">Prerequisites</span></span>

<span data-ttu-id="867f2-107">Pokud chcete začít, musíte nainstalovat nejnovější [.NET Core SDK](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="867f2-107">To begin, you must install the latest [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

<span data-ttu-id="867f2-108">Tento článek předpokládá, že znáte postup pomocí příkazového řádku a mít upřednostňovaném textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="867f2-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="867f2-109">Pokud už nepoužíváte, [Visual Studio Code](get-started-vscode.md) je skvělou možností jako textového editoru pro F#.</span><span class="sxs-lookup"><span data-stu-id="867f2-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="867f2-110">Vytvoření jednoduchého řešení vícenásobného projektu</span><span class="sxs-lookup"><span data-stu-id="867f2-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="867f2-111">Otevřete terminál nebo příkazový řádek a použít [dotnet nové](../../core/tools/dotnet-new.md) příkazu vytvořte nový soubor řešení `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="867f2-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```console
dotnet new sln -o FSNetCore
```

<span data-ttu-id="867f2-112">Následující adresářovou strukturu je vytvořen po spuštění předchozího příkazu:</span><span class="sxs-lookup"><span data-stu-id="867f2-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="867f2-113">Zápis knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="867f2-113">Write a class library</span></span>

<span data-ttu-id="867f2-114">Přejděte do adresáře *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="867f2-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="867f2-115">Použití `dotnet new` příkaz, vytvořte projekt knihovny tříd v **src** složku s názvem knihovny.</span><span class="sxs-lookup"><span data-stu-id="867f2-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```console
dotnet new classlib -lang F# -o src/Library
```

<span data-ttu-id="867f2-116">Následující adresářovou strukturu je vytvořen po spuštění předchozího příkazu:</span><span class="sxs-lookup"><span data-stu-id="867f2-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="867f2-117">Nahraďte obsah `Library.fs` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="867f2-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="867f2-118">Přidejte balíček Newtonsoft.Json NuGet do projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="867f2-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="867f2-119">Přidat `Library` projektu `FSNetCore` pomocí řešení [přidat příkaz dotnet sln](../../core/tools/dotnet-sln.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="867f2-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```console
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="867f2-120">Spustit `dotnet build` k sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="867f2-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="867f2-121">Nevyřešené závislosti se obnoví při sestavování.</span><span class="sxs-lookup"><span data-stu-id="867f2-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="867f2-122">Napíšeme konzolovou aplikaci, která využívá knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="867f2-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="867f2-123">Použití `dotnet new` příkaz, vytvořte konzolovou aplikaci v **src** složku s názvem aplikace.</span><span class="sxs-lookup"><span data-stu-id="867f2-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```console
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="867f2-124">Následující adresářovou strukturu je vytvořen po spuštění předchozího příkazu:</span><span class="sxs-lookup"><span data-stu-id="867f2-124">The following directory structure is produced after running the previous command:</span></span>

```console
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

<span data-ttu-id="867f2-125">Nahraďte obsah `Program.fs` souboru následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="867f2-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="867f2-126">Přidejte odkaz na `Library` projektu pomocí [se příkaz dotnet add odkaz](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="867f2-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="867f2-127">Přidat `App` projektu `FSNetCore` pomocí řešení `dotnet sln add` příkaz:</span><span class="sxs-lookup"><span data-stu-id="867f2-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```console
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="867f2-128">Obnovení závislostí NuGet `dotnet restore` a spusťte `dotnet build` k sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="867f2-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="867f2-129">Změňte adresář na `src/App` konzoly projektu a spusťte projekt pro předání `Hello World` jako argumenty:</span><span class="sxs-lookup"><span data-stu-id="867f2-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="867f2-130">Měly by se zobrazit následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="867f2-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="867f2-131">Další kroky</span><span class="sxs-lookup"><span data-stu-id="867f2-131">Next steps</span></span>

<span data-ttu-id="867f2-132">Dále, podívejte se [prohlídka F# ](../tour.md) získat další informace o různých F# funkce.</span><span class="sxs-lookup"><span data-stu-id="867f2-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
