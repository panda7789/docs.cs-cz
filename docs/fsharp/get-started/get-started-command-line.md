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
# <a name="get-started-with-f-with-the-net-core-cli"></a>Začněte s F # s .NET Core CLI

Tento článek popisuje, jak můžete začít s F # v jakémkoli operačním systému (Windows, macOS nebo Linux) s .NET Core CLI. Prochází sestavením řešení s více projekty pomocí knihovny tříd, která je volána konzolovou aplikací.

## <a name="prerequisites"></a>Předpoklady

Chcete-li začít, je nutné nainstalovat nejnovější [.NET Core SDK](https://dotnet.microsoft.com/download).

V tomto článku se předpokládá, že znáte způsob používání příkazového řádku a máte preferovaný textový editor. Pokud ho ještě nepoužíváte, [Visual Studio Code](get-started-vscode.md) je skvělé možnost jako textový editor pro F #.

## <a name="build-a-simple-multi-project-solution"></a>Sestavení jednoduchého řešení pro více projektů

Otevřete příkazový řádek nebo terminál a pomocí příkazu [dotnet New](../../core/tools/dotnet-new.md) vytvořte nový soubor řešení s názvem `FSNetCore` :

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

Použijte `dotnet new` příkaz, vytvořte projekt knihovny tříd ve složce **Src** s názvem Library.

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

Nahraďte obsah `Library.fs` následujícím kódem:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    let json = JsonConvert.SerializeObject(value)
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value json
```

Přidejte Newtonsoft.Jsdo balíčku NuGet do projektu knihovny.

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Přidejte `Library` projekt do `FSNetCore` řešení pomocí příkazu [dotnet sln Add](../../core/tools/dotnet-sln.md) :

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

Spusťte `dotnet build` pro sestavení projektu. Nevyřešené závislosti budou obnoveny při sestavování.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Zapsat konzolovou aplikaci, která využívá knihovnu tříd

Použijte `dotnet new` příkaz a vytvořte konzolovou aplikaci ve složce **Src** s názvem App.

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

    for arg in argv do
        let value = getJsonNetJson arg
        printfn "%s" value

    0 // return an integer exit code
```

Přidejte odkaz na `Library` projekt pomocí příkazu [dotnet Add Reference](../../core/tools/dotnet-add-reference.md).

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Přidejte `App` projekt do `FSNetCore` řešení pomocí `dotnet sln add` příkazu:

```dotnetcli
dotnet sln add src/App/App.fsproj
```

Obnovte závislosti NuGet `dotnet restore` a spusťte příkaz `dotnet build` pro sestavení projektu.

Změňte adresář na `src/App` Projekt konzoly a spusťte předaný projekt `Hello World` jako argumenty:

```dotnetcli
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

Dále si Projděte [ukázku f #](../tour.md) a získejte další informace o různých funkcích F #.
