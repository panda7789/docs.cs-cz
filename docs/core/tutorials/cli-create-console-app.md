---
title: Začínáme s .NET Core s využitím rozhraní příkazového řádku
description: Podrobný kurz ukazující, jak začít s .NET Core v systému Windows, Linux nebo macOS pomocí .NET Core CLI.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 6e1c7881aa415ea54307d80214001a2f0fe5b4a6
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920469"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>Začínáme s .NET Core s využitím .NET Core CLI

V tomto článku se dozvíte, jak začít s vývojem aplikací .NET Core, které fungují na Windows, Linux a macOS, pomocí .NET Core CLI.

Pokud .NET Core CLI neznáte, přečtěte si [přehled .NET Core CLI](../tools/index.md).

## <a name="prerequisites"></a>Požadavky

- [.NET Core SDK 3,1](https://dotnet.microsoft.com/download) nebo novější verze.
- Textový editor nebo Editor kódu dle vašeho výběru.

## <a name="hello-console-app"></a>Hello, konzolová aplikace!

[Vzorový kód můžete zobrazit nebo stáhnout](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z úložiště GitHub/Samples GitHub. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otevřete příkazový řádek a vytvořte složku s názvem *Hello*. Přejděte do složky, kterou jste vytvořili, a zadejte následující:

```dotnetcli
dotnet new console
dotnet run
```

Podívejme se na stručný návod:

01. `dotnet new console`

    [dotnet New](../tools/dotnet-new.md) vytvoří aktuální soubor projektu *Hello. csproj* se závislostmi nezbytnými k vytvoření konzolové aplikace. Vytvoří také základní soubor *program.cs*, který obsahuje vstupní bod pro aplikaci.
    
    *Hello. csproj*:
    
    [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]
    
    Soubor projektu určuje vše potřebné k obnovení závislostí a sestavování programu.
    
    - Element `<OutputType>` určuje, že vytváříme spustitelný soubor, a to i v jiných slovech konzolové aplikace.
    - Element `<TargetFramework>` určuje, jakou implementaci .NET cílíme. V pokročilém scénáři můžete zadat více cílových rozhraní a sestavit je pro všechny v rámci jedné operace. V tomto kurzu se podíváme na vytváření jenom pro .NET Core 3,1.
    
    *Program.cs*:
    
    [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]
    
    Program se spustí `using System`, což znamená "přenést vše do oboru názvů `System` do rozsahu pro tento soubor". Obor názvů `System` obsahuje třídu `Console`.
    
    Pak definujeme obor názvů s názvem `Hello`. Můžete to změnit na cokoli, co potřebujete. Třída s názvem `Program` je definována v rámci tohoto oboru názvů s metodou `Main`, která přebírá pole řetězců s názvem `args`. Toto pole obsahuje seznam argumentů předaných při spuštění programu. V takovém případě se toto pole nepoužívá a program jednoduše zapisuje text "Hello World!". do konzoly. Později provedeme změny kódu, který tento argument využije.
    
    `dotnet new` volá implicitně [dotnet Restore](../tools/dotnet-restore.md) . `dotnet restore` volání [NuGet](https://www.nuget.org/) (Správce balíčků .NET) pro obnovení stromu závislostí. NuGet analyzuje soubor *Hello. csproj* , stáhne závislosti definované v souboru (nebo je z mezipaměti v počítači převede) a zapíše soubor *obj/Project. assets. JSON* , který je nezbytný pro zkompilování a spuštění ukázky.

02. `dotnet run`

    [dotnet spustit](../tools/dotnet-run.md) volá [sestavení dotnet](../tools/dotnet-build.md) , aby bylo zajištěno, že cíle sestavení byly sestaveny, a poté volá `dotnet <assembly.dll>` pro spuštění cílové aplikace.
    
    ```console
    dotnet run

    Hello World!
    ```
    
    Alternativně můžete také spustit `dotnet build` pro zkompilování kódu bez spuštění konzolových aplikací sestavení. Výsledkem je kompilovaná aplikace, jako soubor DLL, na základě názvu projektu. V tomto případě se vytvoří soubor s názvem *Hello. dll*. Tuto aplikaci můžete spustit s `dotnet bin\Debug\netcoreapp3.1\Hello.dll` ve Windows (použijte `/` pro systémy jiné než Windows).
    
    ```console
    dotnet bin\Debug\netcoreapp3.1\Hello.dll

    Hello World!
    ```
    
    Když je aplikace zkompilována, byl společně s `Hello.dll`vytvořen spustitelný soubor specifický pro operační systém. V systému Windows to bude `Hello.exe`. v systému Linux nebo macOS by to bylo `hello`. S výše uvedeným příkladem je soubor pojmenován pomocí `Hello.exe` nebo `Hello`. Tento spustitelný soubor můžete spustit přímo.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Úprava programu

Pojďme program trochu změnit. Fibonacci čísla jsou zábavné, takže je přidáváme a také k použití argumentu pro přání uživatele, který aplikaci spouští.

01. Obsah souboru *program.cs* nahraďte následujícím kódem:

    [!code-csharp[Fibonacci](~/samples/core/console-apps/fibonacci-msbuild/Program.cs)]

02. Spusťte [sestavení dotnet](../tools/dotnet-build.md) pro zkompilování změn.

03. Spusťte program předáním parametru do aplikace. Když použijete příkaz `dotnet` ke spuštění aplikace, přidejte `--` na konec. Cokoli napravo od `--` bude do aplikace předán jako parametr. V následujícím příkladu je hodnota `John` předána do aplikace.

    ```console
    $ dotnet run -- John
    Hello John!
    Fibonacci Numbers 1-15:
    1: 0
    2: 1
    3: 1
    4: 2
    5: 3
    6: 5
    7: 8
    8: 13
    9: 21
    10: 34
    11: 55
    12: 89
    13: 144
    14: 233
    15: 377
    ```

A je to! *Program.cs* můžete upravit jakýmkoli způsobem.

## <a name="working-with-multiple-files"></a>Práce s více soubory

Jednotlivé soubory jsou pro jednoduché jednorázové programy přesné, ale pokud sestavíte komplexnější aplikaci, pravděpodobně budete mít v projektu více souborů kódu. Pojďme si vytvořit z předchozího příkladu Fibonacci ukládáním do mezipaměti některé hodnoty Fibonacci a přidat některé rekurzivní funkce.

01. Přidejte nový soubor do adresáře *Hello* s názvem *FibonacciGenerator.cs* s následujícím kódem:

    [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

02. Změňte metodu `Main` v souboru *program.cs* pro vytvoření instance nové třídy a zavolejte její metodu jako v následujícím příkladu:

    [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

03. Spusťte [sestavení dotnet](../tools/dotnet-build.md) pro zkompilování změn.

04. Spusťte aplikaci spuštěním příkazu [dotnet](../tools/dotnet-run.md). Následující příklad ukazuje výstup programu:

    ```console
    $ dotnet run
    0
    1
    1
    2
    3
    5
    8
    13
    21
    34
    55
    89
    144
    233
    377
    ```

## <a name="publish-your-app"></a>Publikování aplikace

Až budete připraveni k distribuci vaší aplikace, pomocí příkazu [dotnet Publish](../tools/dotnet-publish.md) vygenerujte složku pro _publikování_ v _přihrádce\\ladění\\netcoreapp 3.1\\publikovat\\_ (použijte `/` pro systémy jiné než Windows). Obsah složky pro _publikování_ můžete distribuovat na jiné platformy, pokud už máte nainstalovanou modul dotnet runtime.

```console
dotnet publish
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

Výše uvedený výstup se může lišit v závislosti na vaší aktuální složce a operačním systému, výstup by měl být podobný.

Publikovanou aplikaci můžete spustit pomocí příkazu [dotnet](../tools/dotnet.md) :

```console
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll

Hello World!
```

Jak je uvedeno na začátku tohoto článku, byl společně s `Hello.dll`vytvořen spustitelný soubor specifický pro operační systém. V systému Windows to bude `Hello.exe`. v systému Linux nebo macOS by to bylo `hello`. S výše uvedeným příkladem je soubor pojmenován pomocí `Hello.exe` nebo `Hello`. Tento publikovaný spustitelný soubor můžete spustit přímo.

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a>Závěr

A je to! Teď můžete začít používat základní koncepty, které jste zde zjistili, k vytvoření vlastních programů.

## <a name="see-also"></a>Viz také:

- [Organizování a testování projektů pomocí .NET Core CLI](testing-with-cli.md)
- [Publikování aplikací .NET Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md)
- [Nasazení aplikace .NET core](../deploying/index.md)
