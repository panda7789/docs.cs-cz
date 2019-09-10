---
title: Začínáme s F# nástroji příkazového řádku
description: Naučte se vytvářet jednoduché řešení Multi-Project na F# používání .NET Core CLI v jakémkoli operačním systému (Windows, MacOS nebo Linux).
ms.date: 03/26/2018
ms.openlocfilehash: 1376b6b5384f380c06a96cdc568ad108de8a6e5f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855825"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="3adcc-103">Začněte s F# .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="3adcc-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="3adcc-104">Tento článek popisuje, jak můžete začít s F# jakýmkoli operačním systémem (Windows, MacOS nebo Linux) pomocí .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="3adcc-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="3adcc-105">Prochází sestavením řešení s více projekty pomocí knihovny tříd, která je volána konzolovou aplikací.</span><span class="sxs-lookup"><span data-stu-id="3adcc-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3adcc-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3adcc-106">Prerequisites</span></span>

<span data-ttu-id="3adcc-107">Chcete-li začít, je nutné nainstalovat nejnovější [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="3adcc-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="3adcc-108">V tomto článku se předpokládá, že znáte způsob používání příkazového řádku a máte preferovaný textový editor.</span><span class="sxs-lookup"><span data-stu-id="3adcc-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="3adcc-109">Pokud ho ještě nepoužíváte, [Visual Studio Code](get-started-vscode.md) je skvělé možnosti jako textový editor pro F#.</span><span class="sxs-lookup"><span data-stu-id="3adcc-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="3adcc-110">Sestavení jednoduchého řešení pro více projektů</span><span class="sxs-lookup"><span data-stu-id="3adcc-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="3adcc-111">Otevřete příkazový řádek nebo terminál a pomocí příkazu [dotnet New](../../core/tools/dotnet-new.md) vytvořte nový soubor řešení s názvem `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="3adcc-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```console
dotnet new sln -o FSNetCore
```

<span data-ttu-id="3adcc-112">Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:</span><span class="sxs-lookup"><span data-stu-id="3adcc-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="3adcc-113">Zápis knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="3adcc-113">Write a class library</span></span>

<span data-ttu-id="3adcc-114">Změňte adresáře na *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="3adcc-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="3adcc-115">Použijte příkaz, vytvořte projekt knihovny tříd ve složce src s názvem Library. `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="3adcc-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```console
dotnet new classlib -lang F# -o src/Library
```

<span data-ttu-id="3adcc-116">Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:</span><span class="sxs-lookup"><span data-stu-id="3adcc-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="3adcc-117">Nahraďte obsah `Library.fs` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="3adcc-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="3adcc-118">Do projektu knihovny přidejte balíček NuGet Newtonsoft. JSON.</span><span class="sxs-lookup"><span data-stu-id="3adcc-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="3adcc-119">Přidejte projekt do řešení pomocí příkazu [dotnet sln Add:](../../core/tools/dotnet-sln.md) `FSNetCore` `Library`</span><span class="sxs-lookup"><span data-stu-id="3adcc-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```console
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="3adcc-120">Spusťte `dotnet build` pro sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="3adcc-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="3adcc-121">Nevyřešené závislosti budou obnoveny při sestavování.</span><span class="sxs-lookup"><span data-stu-id="3adcc-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="3adcc-122">Zapsat konzolovou aplikaci, která využívá knihovnu tříd</span><span class="sxs-lookup"><span data-stu-id="3adcc-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="3adcc-123">Použijte příkaz a vytvořte konzolovou aplikaci ve složce src s názvem App. `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="3adcc-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```console
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="3adcc-124">Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:</span><span class="sxs-lookup"><span data-stu-id="3adcc-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="3adcc-125">Obsah `Program.fs` souboru nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="3adcc-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="3adcc-126">Přidejte odkaz na `Library` projekt pomocí příkazu [dotnet Add Reference](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="3adcc-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="3adcc-127">Přidejte projekt do řešení pomocí `dotnet sln add`příkazu: `FSNetCore` `App`</span><span class="sxs-lookup"><span data-stu-id="3adcc-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```console
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="3adcc-128">Obnovte závislosti `dotnet restore` NuGet a spusťte příkaz `dotnet build` pro sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="3adcc-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="3adcc-129">Změňte adresář na `src/App` projekt konzoly a spusťte předaný `Hello World` projekt jako argumenty:</span><span class="sxs-lookup"><span data-stu-id="3adcc-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="3adcc-130">Měly by se zobrazit následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="3adcc-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="3adcc-131">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3adcc-131">Next steps</span></span>

<span data-ttu-id="3adcc-132">Dále si Projděte [ukázku F# ](../tour.md) a získejte další informace o různých F# funkcích.</span><span class="sxs-lookup"><span data-stu-id="3adcc-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
