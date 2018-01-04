---
title: "Začínáme s F # pomocí nástroje příkazového řádku"
description: "Další informace o použití F # na všechny operačního systému (Windows, systému MacOS, Linux) pomocí rozhraní příkazového řádku a platformy .NET Core."
keywords: "Visual f #, f #, funkční programování, .NET, .NET Core"
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: 4820a8a306bd478429b497a8b7c70ff170c1c655
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="c7a70-104">Začínáme s F # pomocí rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="c7a70-104">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="c7a70-105">Tento článek popisuje, jak můžete začít používat pomocí F # pomocí rozhraní příkazového řádku .NET Core na všechny operačního systému (Windows, systému macOS nebo Linux).</span><span class="sxs-lookup"><span data-stu-id="c7a70-105">This article covers how you can get started on any OS (Windows, macOS, or Linux) by using F# with the .NET Core CLI.</span></span> <span data-ttu-id="c7a70-106">Protože budou přenášeny prostřednictvím vytváření řešení vícenásobného projektu s knihovnou tříd, která je volána konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7a70-106">It will go through building a multi-project solution with a Class Library that is called by a Console Application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7a70-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7a70-107">Prerequisites</span></span>

<span data-ttu-id="c7a70-108">Pokud chcete začít, musíte nainstalovat [.NET Core SDK 1.0 nebo novější](https://dot.net/core).</span><span class="sxs-lookup"><span data-stu-id="c7a70-108">To begin, you must install the [.NET Core SDK 1.0 or later](https://dot.net/core).</span></span> <span data-ttu-id="c7a70-109">Není nutné odinstalovat předchozí verzi rozhraní .NET Core SDK, jako podporuje instalace vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="c7a70-109">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="c7a70-110">Tento článek předpokládá, že znáte postup pomocí příkazového řádku a máte upřednostňované textový editor.</span><span class="sxs-lookup"><span data-stu-id="c7a70-110">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="c7a70-111">Pokud už nepoužíváte, [Visual Studio Code](https://code.visualstudio.com) představuje skvělou možnost jako textový editor pro F #.</span><span class="sxs-lookup"><span data-stu-id="c7a70-111">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="c7a70-112">Chcete-li získat Super funkcí, jako je technologie IntelliSense, lepší zvýraznění syntaxe a další, můžete stáhnout [Ionide rozšíření](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="c7a70-112">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="building-a-simple-multi-project-solution"></a><span data-ttu-id="c7a70-113">Sestavování Simple řešení vícenásobného projektu</span><span class="sxs-lookup"><span data-stu-id="c7a70-113">Building a Simple Multi-project Solution</span></span>

<span data-ttu-id="c7a70-114">Otevřete příkazový řádek nebo terminál a použít `dotnet new` příkaz pro vytvoření nového souboru řešení s názvem `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="c7a70-114">Open a command prompt/terminal and use the `dotnet new` command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="c7a70-115">V důsledku dokončení příkazu vytváří následující adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="c7a70-115">The folowing directory structure is produced as a result of the command completing:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

<span data-ttu-id="c7a70-116">Přejděte do adresáře *FSNetCore* a začít přidávat projekty ke složce řešení.</span><span class="sxs-lookup"><span data-stu-id="c7a70-116">Change directories to *FSNetCore* and start adding projects to the solution folder.</span></span>
 
### <a name="writing-a-class-library"></a><span data-ttu-id="c7a70-117">Zápis knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="c7a70-117">Writing a Class library</span></span>

<span data-ttu-id="c7a70-118">Použití `dotnet new` příkaz, vytvoření projektu knihovny tříd v **src** složku s názvem knihovny.</span><span class="sxs-lookup"><span data-stu-id="c7a70-118">Use the `dotnet new` command, create a Class Library project in the **src** folder named Library.</span></span> 

```bash
dotnet new lib -lang F# -o src/Library 
```

<span data-ttu-id="c7a70-119">V důsledku dokončení příkazu vytváří následující adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="c7a70-119">The following directory structure is produced as a result of the command completing:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="c7a70-120">Nahraďte obsah `Library.fs` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="c7a70-120">Replace the contents of `Library.fs` with the following:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="c7a70-121">Přidejte balíček Newtonsoft.Json NuGet do projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="c7a70-121">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="c7a70-122">Přidat `Library` projektu do `FSNetCore` řešení pomocí `dotnet sln add` příkaz:</span><span class="sxs-lookup"><span data-stu-id="c7a70-122">Add the `Library` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="c7a70-123">Obnovte závislosti NuGet `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) a spusťte `dotnet build` a tím projekt sestavit.</span><span class="sxs-lookup"><span data-stu-id="c7a70-123">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="writing-a-console-application-which-consumes-the-class-library"></a><span data-ttu-id="c7a70-124">Zápis konzolové aplikace, která využívá knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="c7a70-124">Writing a Console Application which Consumes the Class Library</span></span>

<span data-ttu-id="c7a70-125">Použití `dotnet new` příkaz, vytvořte konzolovou aplikaci v **src** složku s názvem aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7a70-125">Use the `dotnet new` command, create a Console app in the **src** folder named App.</span></span> 

```bash
dotnet new console -lang F# -o src/App 
```

<span data-ttu-id="c7a70-126">V důsledku dokončení příkazu vytváří následující adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="c7a70-126">The following directory structure is produced as a result of the command completing:</span></span>

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

<span data-ttu-id="c7a70-127">Změna `Program.fs` na:</span><span class="sxs-lookup"><span data-stu-id="c7a70-127">Change `Program.fs` to:</span></span>

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

<span data-ttu-id="c7a70-128">Přidat odkaz na `Library` projektu pomocí `dotnet add reference`.</span><span class="sxs-lookup"><span data-stu-id="c7a70-128">Add a reference to the `Library` project using `dotnet add reference`.</span></span>

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="c7a70-129">Přidat `App` projektu do `FSNetCore` řešení pomocí `dotnet sln add` příkaz:</span><span class="sxs-lookup"><span data-stu-id="c7a70-129">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="c7a70-130">Obnovte závislosti NuGet `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) a spusťte `dotnet build` a tím projekt sestavit.</span><span class="sxs-lookup"><span data-stu-id="c7a70-130">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="c7a70-131">Změnit adresář `src/App` konzole projektu a spusťte projekt předávání `Hello World` jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="c7a70-131">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments.</span></span>

```bash
cd src/App
dotnet run Hello World
``` 

<span data-ttu-id="c7a70-132">Byste měli vidět následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="c7a70-132">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
