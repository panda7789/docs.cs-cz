---
title: Začínáme s F# nástroji příkazového řádku
description: Naučte se vytvářet jednoduché řešení Multi-Project na F# používání .NET Core CLI v jakémkoli operačním systému (Windows, MacOS nebo Linux).
ms.date: 03/26/2018
ms.openlocfilehash: aa3ed84660a951eeafc11a00ea3831f587b6d876
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559484"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Začněte s F# .NET Core CLI

Tento článek popisuje, jak můžete začít s F# jakýmkoli operačním systémem (Windows, MacOS nebo Linux) pomocí .NET Core CLI. Prochází sestavením řešení s více projekty pomocí knihovny tříd, která je volána konzolovou aplikací.

## <a name="prerequisites"></a>Požadavky

Chcete-li začít, je nutné nainstalovat nejnovější [.NET Core SDK](https://dotnet.microsoft.com/download).

V tomto článku se předpokládá, že znáte způsob používání příkazového řádku a máte preferovaný textový editor. Pokud ho ještě nepoužíváte, [Visual Studio Code](get-started-vscode.md) je skvělé možnosti jako textový editor pro F#.

## <a name="build-a-simple-multi-project-solution"></a>Sestavení jednoduchého řešení pro více projektů

Otevřete příkazový řádek nebo terminál a pomocí příkazu [dotnet New](../../core/tools/dotnet-new.md) vytvořte nový soubor řešení s názvem `FSNetCore`:

```dotnetcli
dotnet new sln -o FSNetCore
```

Po spuštění předchozího příkazu se vytvoří následující adresářová struktura:

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Zápis knihovny tříd

Změňte adresáře na *FSNetCore*.

Použijte příkaz `dotnet new`, vytvořte projekt knihovny tříd ve složce **Src** s názvem Library.

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
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

Obsah `Library.fs` nahraďte následujícím kódem:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

Do projektu knihovny přidejte balíček NuGet Newtonsoft. JSON.

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Přidejte `Library` projekt do řešení `FSNetCore` pomocí příkazu [dotnet sln Add](../../core/tools/dotnet-sln.md) :

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

Spusťte `dotnet build` pro sestavení projektu. Nevyřešené závislosti budou obnoveny při sestavování.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Zapsat konzolovou aplikaci, která využívá knihovnu tříd

Použijte příkaz `dotnet new` a vytvořte konzolovou aplikaci ve složce **Src** s názvem App.

```dotnetcli
dotnet new console -lang "F#" -o src/App
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

Obsah souboru `Program.fs` nahraďte následujícím kódem:

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

Přidejte odkaz na projekt `Library` pomocí příkazu [dotnet Add Reference](../../core/tools/dotnet-add-reference.md).

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Přidejte `App` projekt do řešení `FSNetCore` pomocí příkazu `dotnet sln add`:

```dotnetcli
dotnet sln add src/App/App.fsproj
```

Obnovte závislosti NuGet `dotnet restore` a spusťte `dotnet build` a sestavte projekt.

Změňte adresář na projekt konzoly `src/App` a spusťte `Hello World` projektu jako argumenty:

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
