---
title: 'Začínáme s F # pomocí nástrojů příkazového řádku'
description: 'Naučte se vytvářet jednoduché řešení Multi-Project na F # pomocí .NET Core CLI v jakémkoli operačním systému (Windows, macOS nebo Linux).'
ms.date: 08/15/2020
ms.openlocfilehash: e652b66337a3122de8e6bd4d62d86fb6082b759d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811987"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="8daa0-103">Začněte s F # s .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="8daa0-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="8daa0-104">Tento článek popisuje, jak můžete začít s F # v jakémkoli operačním systému (Windows, macOS nebo Linux) s .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="8daa0-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="8daa0-105">Prochází sestavením řešení s více projekty pomocí knihovny tříd, která je volána konzolovou aplikací.</span><span class="sxs-lookup"><span data-stu-id="8daa0-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8daa0-106">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="8daa0-106">Prerequisites</span></span>

<span data-ttu-id="8daa0-107">Chcete-li začít, je nutné nainstalovat nejnovější [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="8daa0-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="8daa0-108">V tomto článku se předpokládá, že znáte způsob používání příkazového řádku a máte preferovaný textový editor.</span><span class="sxs-lookup"><span data-stu-id="8daa0-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="8daa0-109">Pokud ho ještě nepoužíváte, [Visual Studio Code](get-started-vscode.md) je skvělé možnost jako textový editor pro F #.</span><span class="sxs-lookup"><span data-stu-id="8daa0-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="8daa0-110">Sestavení jednoduchého řešení pro více projektů</span><span class="sxs-lookup"><span data-stu-id="8daa0-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="8daa0-111">Otevřete příkazový řádek nebo terminál a pomocí příkazu [dotnet New](../../core/tools/dotnet-new.md) vytvořte nový soubor řešení s názvem `FSNetCore` :</span><span class="sxs-lookup"><span data-stu-id="8daa0-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```dotnetcli
dotnet new sln -o FSNetCore
```

<span data-ttu-id="8daa0-112">Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:</span><span class="sxs-lookup"><span data-stu-id="8daa0-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="8daa0-113">Zápis knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="8daa0-113">Write a class library</span></span>

<span data-ttu-id="8daa0-114">Změňte adresáře na *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="8daa0-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="8daa0-115">Použijte `dotnet new` příkaz, vytvořte projekt knihovny tříd ve složce **Src** s názvem Library.</span><span class="sxs-lookup"><span data-stu-id="8daa0-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

<span data-ttu-id="8daa0-116">Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:</span><span class="sxs-lookup"><span data-stu-id="8daa0-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="8daa0-117">Nahraďte obsah `Library.fs` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8daa0-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    let json = JsonConvert.SerializeObject(value)
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value json
```

<span data-ttu-id="8daa0-118">Přidejte Newtonsoft.Jsdo balíčku NuGet do projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="8daa0-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="8daa0-119">Přidejte `Library` projekt do `FSNetCore` řešení pomocí příkazu [dotnet sln Add](../../core/tools/dotnet-sln.md) :</span><span class="sxs-lookup"><span data-stu-id="8daa0-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="8daa0-120">Spusťte `dotnet build` pro sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="8daa0-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="8daa0-121">Nevyřešené závislosti budou obnoveny při sestavování.</span><span class="sxs-lookup"><span data-stu-id="8daa0-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="8daa0-122">Zapsat konzolovou aplikaci, která využívá knihovnu tříd</span><span class="sxs-lookup"><span data-stu-id="8daa0-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="8daa0-123">Použijte `dotnet new` příkaz a vytvořte konzolovou aplikaci ve složce **Src** s názvem App.</span><span class="sxs-lookup"><span data-stu-id="8daa0-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

<span data-ttu-id="8daa0-124">Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:</span><span class="sxs-lookup"><span data-stu-id="8daa0-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="8daa0-125">Obsah souboru `Program.fs` nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8daa0-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    for arg in argv do
        let value = getJsonNetJson arg
        printfn "%s" value

    0 // return an integer exit code
```

<span data-ttu-id="8daa0-126">Přidejte odkaz na `Library` projekt pomocí příkazu [dotnet Add Reference](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="8daa0-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="8daa0-127">Přidejte `App` projekt do `FSNetCore` řešení pomocí `dotnet sln add` příkazu:</span><span class="sxs-lookup"><span data-stu-id="8daa0-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```dotnetcli
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="8daa0-128">Obnovte závislosti NuGet `dotnet restore` a spusťte příkaz `dotnet build` pro sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="8daa0-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="8daa0-129">Změňte adresář na `src/App` Projekt konzoly a spusťte předaný projekt `Hello World` jako argumenty:</span><span class="sxs-lookup"><span data-stu-id="8daa0-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```dotnetcli
cd src/App
dotnet run Hello World
```

<span data-ttu-id="8daa0-130">Měly by se zobrazit následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="8daa0-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="8daa0-131">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8daa0-131">Next steps</span></span>

<span data-ttu-id="8daa0-132">Dále si Projděte [ukázku f #](../tour.md) a získejte další informace o různých funkcích F #.</span><span class="sxs-lookup"><span data-stu-id="8daa0-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
