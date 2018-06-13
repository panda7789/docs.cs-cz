---
title: 'Začínáme s F # pomocí nástroje příkazového řádku'
description: 'Naučte se vytvářet jednoduché řešení vícenásobného projektu na F # pomocí rozhraní příkazového řádku .NET Core v jakémkoliv operačním systému (Windows, systému macOs nebo Linux).'
ms.date: 03/26/2018
ms.openlocfilehash: 35ec2313742a0b14c92f3de2662a16aff389b214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562034"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Začínáme s F # pomocí rozhraní příkazového řádku .NET Core

Tento článek popisuje, jak můžete začít používat v jakémkoliv operačním systému (Windows, systému macOS nebo Linux) pomocí rozhraní příkazového řádku .NET Core a F #. Projde vytváření řešení vícenásobného projektu s knihovnou tříd, která je volána konzolové aplikace.

## <a name="prerequisites"></a>Požadavky

Pokud chcete začít, musíte nainstalovat [.NET Core SDK 1.0 nebo novější](https://www.microsoft.com/net/download/). Není nutné odinstalovat předchozí verzi rozhraní .NET Core SDK, jako podporuje instalace vedle sebe.

Tento článek předpokládá, že znáte postup pomocí příkazového řádku a máte upřednostňované textový editor. Pokud už nepoužíváte, [Visual Studio Code](https://code.visualstudio.com) představuje skvělou možnost jako textový editor pro F #. Chcete-li získat Super funkcí, jako je technologie IntelliSense, lepší zvýraznění syntaxe a další, můžete stáhnout [Ionide rozšíření](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).

## <a name="build-a-simple-multi-project-solution"></a>Vytvoření jednoduché řešení vícenásobného projektu

Otevřete příkazový řádek nebo terminál a použít [dotnet nové](../../core/tools/dotnet-new.md) příkaz pro vytvoření nového souboru řešení s názvem `FSNetCore`:

```
dotnet new sln -o FSNetCore
```

Po spuštění předchozí příkaz vytváří následující adresářovou strukturu:

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Zápis knihovny tříd

Přejděte do adresáře *FSNetCore*.

Použití `dotnet new` příkaz, vytvořte v projektu knihovny tříd **src** složku s názvem knihovny.

```
dotnet new lib -lang F# -o src/Library
```

Po spuštění předchozí příkaz vytváří následující adresářovou strukturu:

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
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

Přidejte balíček Newtonsoft.Json NuGet do projektu knihovny.

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Přidat `Library` projektu do `FSNetCore` řešení pomocí [dotnet SLN – přidat](../../core/tools/dotnet-sln.md) příkaz:

```
dotnet sln add src/Library/Library.fsproj
```

Obnovit pomocí závislostí NuGet `dotnet restore` příkazu ([viz Poznámka](#dotnet-restore-note)) a spusťte `dotnet build` a tím projekt sestavit.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Zápis konzolovou aplikaci, která využívá knihovny tříd

Použití `dotnet new` příkaz, vytvořte konzolovou aplikaci v **src** složku s názvem aplikace.

```
dotnet new console -lang F# -o src/App
```

Po spuštění předchozí příkaz vytváří následující adresářovou strukturu:

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

Nahraďte obsah `Program.fs` soubor s následujícím kódem:

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

Přidat odkaz na `Library` projektu pomocí [dotnet přidat odkaz](../../core/tools/dotnet-add-reference.md).

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Přidat `App` projektu do `FSNetCore` řešení pomocí `dotnet sln add` příkaz:

```
dotnet sln add src/App/App.fsproj
```

Obnovte závislosti NuGet `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) a spusťte `dotnet build` a tím projekt sestavit.

Změnit adresář `src/App` konzole projektu a spusťte projekt předávání `Hello World` jako argumenty:

```
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