---
title: 'Začínáme s jazykem F # pomocí nástrojů příkazového řádku'
description: 'Informace o vytvoření jednoduchého řešení vícenásobného projektu v F # s použitím rozhraní příkazového řádku .NET Core pro všechny operační systémy (Windows, macOs nebo Linux).'
ms.date: 03/26/2018
ms.openlocfilehash: 8a82970f33c8bbe1b8cdd8fb6499b59b16d3cbf3
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "45673906"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Začínáme s jazykem F # pomocí rozhraní příkazového řádku .NET Core

Tento článek popisuje, jak můžete začít s jazykem F # pro všechny operační systémy (Windows, macOS nebo Linux) pomocí rozhraní příkazového řádku .NET Core. Prochází přes vytváření řešení vícenásobného projektu knihovny tříd, která je volána pomocí konzolové aplikace.

## <a name="prerequisites"></a>Požadavky

Pokud chcete začít, musíte nainstalovat nejnovější [.NET Core SDK](https://www.microsoft.com/net/download/).

Tento článek předpokládá, že znáte postup pomocí příkazového řádku a mít upřednostňovaném textovém editoru. Pokud už nepoužíváte, [Visual Studio Code](get-started-vscode.md) je skvělou možností jako textový editor jazyka F #.

## <a name="build-a-simple-multi-project-solution"></a>Vytvoření jednoduchého řešení vícenásobného projektu

Otevřete terminál nebo příkazový řádek a použít [dotnet nové](../../core/tools/dotnet-new.md) příkazu vytvořte nový soubor řešení `FSNetCore`:

```console
dotnet new sln -o FSNetCore
```

Následující adresářovou strukturu je vytvořen po spuštění předchozího příkazu:

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Zápis knihovny tříd

Přejděte do adresáře *FSNetCore*.

Použití `dotnet new` příkaz, vytvořte projekt knihovny tříd v **src** složku s názvem knihovny.

```console
dotnet new classlib -lang F# -o src/Library
```

Následující adresářovou strukturu je vytvořen po spuštění předchozího příkazu:

```console
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
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

Přidejte balíček Newtonsoft.Json NuGet do projektu knihovny.

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Přidat `Library` projektu `FSNetCore` pomocí řešení [přidat příkaz dotnet sln](../../core/tools/dotnet-sln.md) příkaz:

```console
dotnet sln add src/Library/Library.fsproj
```

Spustit `dotnet build` k sestavení projektu. Nevyřešené závislosti se obnoví při sestavování.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Napíšeme konzolovou aplikaci, která využívá knihovna tříd

Použití `dotnet new` příkaz, vytvořte konzolovou aplikaci v **src** složku s názvem aplikace.

```console
dotnet new console -lang F# -o src/App
```

Následující adresářovou strukturu je vytvořen po spuštění předchozího příkazu:

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

Nahraďte obsah `Program.fs` souboru následujícím kódem:

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

Přidejte odkaz na `Library` projektu pomocí [se příkaz dotnet add odkaz](../../core/tools/dotnet-add-reference.md).

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Přidat `App` projektu `FSNetCore` pomocí řešení `dotnet sln add` příkaz:

```console
dotnet sln add src/App/App.fsproj
```

Obnovení závislostí NuGet `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) a spusťte `dotnet build` k sestavení projektu.

Změňte adresář na `src/App` konzoly projektu a spusťte projekt pro předání `Hello World` jako argumenty:

```console
cd src/App
dotnet run Hello World
```

Zobrazí se následující výsledky:

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>Další kroky

V dalším kroku se podívejte [Tour F #](../tour.md) získat další informace o různých funkcí F #.
