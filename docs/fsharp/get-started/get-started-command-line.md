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
# <a name="get-started-with-f-with-the-net-core-cli"></a>Začněte s F# .NET Core CLI

Tento článek popisuje, jak můžete začít s F# jakýmkoli operačním systémem (Windows, MacOS nebo Linux) pomocí .NET Core CLI. Prochází sestavením řešení s více projekty pomocí knihovny tříd, která je volána konzolovou aplikací.

## <a name="prerequisites"></a>Požadavky

Chcete-li začít, je nutné nainstalovat nejnovější [.NET Core SDK](https://dotnet.microsoft.com/download).

V tomto článku se předpokládá, že znáte způsob používání příkazového řádku a máte preferovaný textový editor. Pokud ho ještě nepoužíváte, [Visual Studio Code](get-started-vscode.md) je skvělé možnosti jako textový editor pro F#.

## <a name="build-a-simple-multi-project-solution"></a>Sestavení jednoduchého řešení pro více projektů

Otevřete příkazový řádek nebo terminál a pomocí příkazu [dotnet New](../../core/tools/dotnet-new.md) vytvořte nový soubor řešení s názvem `FSNetCore`:

```console
dotnet new sln -o FSNetCore
```

Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Zápis knihovny tříd

Změňte adresáře na *FSNetCore*.

Použijte příkaz, vytvořte projekt knihovny tříd ve složce src s názvem Library. `dotnet new`

```console
dotnet new classlib -lang F# -o src/Library
```

Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:

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

Do projektu knihovny přidejte balíček NuGet Newtonsoft. JSON.

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Přidejte projekt do řešení pomocí příkazu [dotnet sln Add:](../../core/tools/dotnet-sln.md) `FSNetCore` `Library`

```console
dotnet sln add src/Library/Library.fsproj
```

Spusťte `dotnet build` pro sestavení projektu. Nevyřešené závislosti budou obnoveny při sestavování.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Zapsat konzolovou aplikaci, která využívá knihovnu tříd

Použijte příkaz a vytvořte konzolovou aplikaci ve složce src s názvem App. `dotnet new`

```console
dotnet new console -lang F# -o src/App
```

Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:

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

Obsah `Program.fs` souboru nahraďte následujícím kódem:

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

Přidejte odkaz na `Library` projekt pomocí příkazu [dotnet Add Reference](../../core/tools/dotnet-add-reference.md).

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Přidejte projekt do řešení pomocí `dotnet sln add`příkazu: `FSNetCore` `App`

```console
dotnet sln add src/App/App.fsproj
```

Obnovte závislosti `dotnet restore` NuGet a spusťte příkaz `dotnet build` pro sestavení projektu.

Změňte adresář na `src/App` projekt konzoly a spusťte předaný `Hello World` projekt jako argumenty:

```console
cd src/App
dotnet run Hello World
```

Měly by se zobrazit následující výsledky:

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>Další kroky

Dále si Projděte [ukázku F# ](../tour.md) a získejte další informace o různých F# funkcích.
