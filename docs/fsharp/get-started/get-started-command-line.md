---
title: "Začínáme s F # pomocí nástroje příkazového řádku"
description: "Další informace o použití F # pomocí rozhraní příkazového řádku a platformy .NET Core."
keywords: "Visual f #, f #, funkční programování, .NET, .NET Core"
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: a23d4861ce599f20f37ecd0564a0187e7b9b739f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Začínáme s F # pomocí rozhraní příkazového řádku .NET Core

Tento článek popisuje, jak začít s použitím F # na .NET Core. Protože budou přenášeny prostřednictvím vytváření řešení vícenásobného projektu s knihovnou tříd, která je volána konzolové aplikace.

## <a name="prerequisites"></a>Požadavky

Pokud chcete začít, musíte nainstalovat [.NET Core SDK 1.0 nebo novější](https://dot.net/core). Není nutné odinstalovat předchozí verzi rozhraní .NET Core SDK, jako podporuje instalace vedle sebe.

Tento článek předpokládá, že znáte postup pomocí příkazového řádku a máte upřednostňované textový editor. Pokud už nepoužíváte, [Visual Studio Code](https://code.visualstudio.com) představuje skvělou možnost jako textový editor pro F #. Chcete-li získat Super funkcí, jako je technologie IntelliSense, lepší zvýraznění syntaxe a další, můžete stáhnout [Ionide rozšíření](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).

## <a name="building-a-simple-multi-project-solution"></a>Sestavování Simple řešení vícenásobného projektu

Otevřete příkazový řádek nebo terminál a použít `dotnet new` příkaz pro vytvoření nového souboru řešení s názvem `FSNetCore`:

```
dotnet new sln -o FSNetCore
```

V důsledku dokončení příkazu vytváří následující adresářovou strukturu:

```
FSNetCore
    ├── FSNetCore.sln
```

Přejděte do adresáře *FSNetCore* a začít přidávat projekty ke složce řešení.
 
### <a name="writing-a-class-library"></a>Zápis knihovny tříd

Použití `dotnet new` příkaz, vytvoření projektu knihovny tříd v **src** složku s názvem knihovny. 

```bash
dotnet new lib -lang F# -o src/Library 
```

V důsledku dokončení příkazu vytváří následující adresářovou strukturu:

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Nahraďte obsah `Library.fs` následujícím kódem:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

Přidejte balíček Newtonsoft.Json NuGet do projektu knihovny.

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Přidat `Library` projektu do `FSNetCore` řešení pomocí `dotnet sln add` příkaz:

```bash
dotnet sln add src/Library/Library.fsproj
```

Obnovte závislosti NuGet `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) a spusťte `dotnet build` a tím projekt sestavit.

### <a name="writing-a-console-application-which-consumes-the-class-library"></a>Zápis konzolové aplikace, která využívá knihovny tříd

Použití `dotnet new` příkaz, vytvořte konzolovou aplikaci v **src** složku s názvem aplikace. 

```bash
dotnet new console -lang F# -o src/App 
```

V důsledku dokončení příkazu vytváří následující adresářovou strukturu:

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

Změna `Program.fs` na:

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

Přidat odkaz na `Library` projektu pomocí `dotnet add reference`.

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Přidat `App` projektu do `FSNetCore` řešení pomocí `dotnet sln add` příkaz:

```bash
dotnet sln add src/App/App.fsproj
```

Obnovte závislosti NuGet `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) a spusťte `dotnet build` a tím projekt sestavit.

Změnit adresář `src/App` konzole projektu a spusťte projekt předávání `Hello World` jako argumenty.

```bash
cd src/App
dotnet run Hello World
``` 

Byste měli vidět následující výsledky:

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]