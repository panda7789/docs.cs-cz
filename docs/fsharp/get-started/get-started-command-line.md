---
title: Začínáme s F# nástroji příkazového řádku
description: Naučte se vytvářet jednoduché řešení Multi-Project na F# používání .NET Core CLI v jakémkoli operačním systému (Windows, MacOS nebo Linux).
ms.date: 03/26/2018
ms.openlocfilehash: 6f67314f49150e20b18734f21f24daa3ce856922
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504141"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="9501a-103">Začněte s F# .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="9501a-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="9501a-104">Tento článek popisuje, jak můžete začít s F# jakýmkoli operačním systémem (Windows, MacOS nebo Linux) pomocí .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="9501a-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="9501a-105">Prochází sestavením řešení s více projekty pomocí knihovny tříd, která je volána konzolovou aplikací.</span><span class="sxs-lookup"><span data-stu-id="9501a-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9501a-106">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="9501a-106">Prerequisites</span></span>

<span data-ttu-id="9501a-107">Chcete-li začít, je nutné nainstalovat nejnovější [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="9501a-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="9501a-108">V tomto článku se předpokládá, že znáte způsob používání příkazového řádku a máte preferovaný textový editor.</span><span class="sxs-lookup"><span data-stu-id="9501a-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="9501a-109">Pokud ho ještě nepoužíváte, [Visual Studio Code](get-started-vscode.md) je skvělé možnosti jako textový editor pro F#.</span><span class="sxs-lookup"><span data-stu-id="9501a-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="9501a-110">Sestavení jednoduchého řešení pro více projektů</span><span class="sxs-lookup"><span data-stu-id="9501a-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="9501a-111">Otevřete příkazový řádek nebo terminál a pomocí příkazu [dotnet New](../../core/tools/dotnet-new.md) vytvořte nový soubor řešení s názvem `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="9501a-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```dotnetcli
dotnet new sln -o FSNetCore
```

<span data-ttu-id="9501a-112">Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:</span><span class="sxs-lookup"><span data-stu-id="9501a-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="9501a-113">Zápis knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="9501a-113">Write a class library</span></span>

<span data-ttu-id="9501a-114">Změňte adresáře na *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="9501a-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="9501a-115">Použijte příkaz `dotnet new`, vytvořte projekt knihovny tříd ve složce **Src** s názvem Library.</span><span class="sxs-lookup"><span data-stu-id="9501a-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

<span data-ttu-id="9501a-116">Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:</span><span class="sxs-lookup"><span data-stu-id="9501a-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="9501a-117">Obsah `Library.fs` nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="9501a-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="9501a-118">Do projektu knihovny přidejte balíček NuGet Newtonsoft. JSON.</span><span class="sxs-lookup"><span data-stu-id="9501a-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="9501a-119">Přidejte `Library` projekt do řešení `FSNetCore` pomocí příkazu [dotnet sln Add](../../core/tools/dotnet-sln.md) :</span><span class="sxs-lookup"><span data-stu-id="9501a-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="9501a-120">Spusťte `dotnet build` pro sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="9501a-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="9501a-121">Nevyřešené závislosti budou obnoveny při sestavování.</span><span class="sxs-lookup"><span data-stu-id="9501a-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="9501a-122">Zapsat konzolovou aplikaci, která využívá knihovnu tříd</span><span class="sxs-lookup"><span data-stu-id="9501a-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="9501a-123">Použijte příkaz `dotnet new` a vytvořte konzolovou aplikaci ve složce **Src** s názvem App.</span><span class="sxs-lookup"><span data-stu-id="9501a-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

<span data-ttu-id="9501a-124">Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:</span><span class="sxs-lookup"><span data-stu-id="9501a-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="9501a-125">Obsah souboru `Program.fs` nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="9501a-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="9501a-126">Přidejte odkaz na projekt `Library` pomocí příkazu [dotnet Add Reference](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="9501a-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="9501a-127">Přidejte `App` projekt do řešení `FSNetCore` pomocí příkazu `dotnet sln add`:</span><span class="sxs-lookup"><span data-stu-id="9501a-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```dotnetcli
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="9501a-128">Obnovte závislosti NuGet `dotnet restore` a spusťte `dotnet build` a sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="9501a-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="9501a-129">Změňte adresář na projekt konzoly `src/App` a spusťte `Hello World` projektu jako argumenty:</span><span class="sxs-lookup"><span data-stu-id="9501a-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```dotnetcli
cd src/App
dotnet run Hello World
```

<span data-ttu-id="9501a-130">Měly by se zobrazit následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="9501a-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="9501a-131">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9501a-131">Next steps</span></span>

<span data-ttu-id="9501a-132">Dále si Projděte [ukázku F# ](../tour.md) a získejte další informace o různých F# funkcích.</span><span class="sxs-lookup"><span data-stu-id="9501a-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
