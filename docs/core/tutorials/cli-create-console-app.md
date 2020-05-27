---
title: Začínáme s .NET Core v rozhraní příkazového řádku
description: Podrobný kurz ukazující, jak začít s .NET Core v systému Windows, Linux nebo macOS pomocí .NET Core CLI.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 7658f2498b87a90b3925d83628f6ea9247a2fc15
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840868"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>Začínáme s .NET Core s využitím .NET Core CLI

V tomto článku se dozvíte, jak začít s vývojem aplikací .NET Core, které fungují na Windows, Linux a macOS, pomocí .NET Core CLI.

Pokud .NET Core CLI neznáte, přečtěte si [přehled .NET Core CLI](../tools/index.md).

## <a name="prerequisites"></a>Požadavky

- [.NET Core SDK 3,1](https://dotnet.microsoft.com/download) nebo novější verze.
- Textový editor nebo editor kódu podle vašeho výběru.

## <a name="hello-console-app"></a>Hello, konzolová aplikace!

[Vzorový kód můžete zobrazit nebo stáhnout](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z úložiště GitHub/Samples GitHub. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otevřete příkazový řádek a vytvořte složku s názvem *Hello*. Přejděte do složky, kterou jste vytvořili, a zadejte následující text.

```dotnetcli
dotnet new console
dotnet run
```

Podívejme se na stručný návod:

01. `dotnet new console`

    [dotnet New](../tools/dotnet-new.md) vytvoří aktuální soubor projektu *Hello. csproj* se závislostmi nezbytnými k vytvoření konzolové aplikace. Vytvoří také základní soubor *program.cs*, který obsahuje vstupní bod pro aplikaci.

    *Hello. csproj*:

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    Soubor projektu určuje vše potřebné k obnovení závislostí a sestavování programu.

    - `<OutputType>`Prvek určuje, že vytváříme spustitelný soubor, a to v jiných slovech konzolové aplikace.
    - `<TargetFramework>`Prvek určuje, jakou implementaci .NET cílíme. V pokročilém scénáři můžete zadat více cílových rozhraní a sestavit je pro všechny v rámci jedné operace. V tomto kurzu se podíváme na vytváření jenom pro .NET Core 3,1.

    *Program.cs*:

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    Program spustí `using System` , což znamená "přenést vše do oboru `System` názvů do rozsahu pro tento soubor". `System`Obor názvů obsahuje `Console` třídu.

    Pak definujeme obor názvů s názvem `Hello` . Můžete to změnit na cokoli, co potřebujete. Třída s názvem `Program` je definována v rámci tohoto oboru názvů s `Main` metodou, která přebírá pole řetězců s názvem `args` . Toto pole obsahuje seznam argumentů předaných při spuštění programu. V takovém případě se toto pole nepoužívá a program jednoduše zapisuje text "Hello World!". „Hello, World!“. Později provedeme změny kódu, který tento argument využije.

    `dotnet new`implicitně volá [dotnet Restore](../tools/dotnet-restore.md) . `dotnet restore`volání [NuGet](https://www.nuget.org/) (Správce balíčků .NET) pro obnovení stromu závislostí. NuGet analyzuje soubor *Hello. csproj* , stáhne závislosti definované v souboru (nebo je z mezipaměti v počítači převede) a zapíše soubor *obj/Project. assets. JSON* , který je nezbytný pro zkompilování a spuštění ukázky.

02. `dotnet run`

    [dotnet spustit](../tools/dotnet-run.md) volá [sestavení dotnet](../tools/dotnet-build.md) , aby bylo zajištěno, že cíle sestavení byly sestaveny, a poté volá `dotnet <assembly.dll>` spustit cílovou aplikaci.

    ```dotnetcli
    dotnet run
    ```

    Zobrazí se následující výstup.

    ```console
    Hello World!
    ```

    Případně můžete také spustit `dotnet build` pro zkompilování kódu bez spuštění konzolových aplikací sestavení. Výsledkem je kompilovaná aplikace, jako soubor DLL, na základě názvu projektu. V tomto případě se vytvoří soubor s názvem *Hello. dll*. Tuto aplikaci můžete spustit `dotnet bin\Debug\netcoreapp3.1\Hello.dll` v systému Windows (používá se `/` pro systémy jiné než Windows).

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    Zobrazí se následující výstup.

    ```console
    Hello World!
    ```

    Když je aplikace zkompilována, byl vytvořen spustitelný soubor specifický pro operační systém společně s nástrojem `Hello.dll` . Ve Windows by to bylo `Hello.exe` . v systému Linux nebo MacOS by to bylo `hello` . S výše uvedeným příkladem je soubor pojmenován s `Hello.exe` nebo `Hello` . Tento spustitelný soubor můžete spustit přímo.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Úprava programu

Pojďme program trochu změnit. Fibonacci čísla jsou zábavné, takže je přidáváme a také k použití argumentu pro přání uživatele, který aplikaci spouští.

01. Obsah souboru *program.cs* nahraďte následujícím kódem:

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. Spusťte [sestavení dotnet](../tools/dotnet-build.md) pro zkompilování změn.

03. Spusťte program předáním parametru do aplikace. Když použijete `dotnet` příkaz ke spuštění aplikace, přidejte `--` na konec. Cokoli napravo od `--` bude předáno jako parametr do aplikace. V následujícím příkladu `John` je hodnota předána do aplikace.

    ```dotnetcli
    dotnet run -- John
    ```

    Zobrazí se následující výstup.

    ```console
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

A to je vše! *Program.cs* můžete upravit jakýmkoli způsobem.

## <a name="working-with-multiple-files"></a>Práce s více soubory

Jednotlivé soubory jsou pro jednoduché jednorázové programy přesné, ale pokud sestavíte komplexnější aplikaci, pravděpodobně budete mít v projektu více souborů kódu. Pojďme si vytvořit z předchozího příkladu Fibonacci ukládáním do mezipaměti některé hodnoty Fibonacci a přidat některé rekurzivní funkce.

01. Přidejte nový soubor do adresáře *Hello* s názvem *FibonacciGenerator.cs* s následujícím kódem:

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. Změňte `Main` metodu v souboru *program.cs* pro vytvoření instance nové třídy a zavolejte její metodu jako v následujícím příkladu:

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. Spusťte [sestavení dotnet](../tools/dotnet-build.md) pro zkompilování změn.

04. Spusťte aplikaci spuštěním příkazu [dotnet](../tools/dotnet-run.md).

    ```dotnetcli
    dotnet run
    ```

    Zobrazí se následující výstup.

    ```console
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

Až budete připraveni k distribuci vaší aplikace, použijte příkaz [dotnet Publish](../tools/dotnet-publish.md) pro vygenerování složky pro _publikování_ v _přihrádce \\ Debug \\ netcoreapp 3.1 \\ Publish \\ _ (použijte `/` pro systémy jiné než Windows). Obsah složky pro _publikování_ můžete distribuovat na jiné platformy, pokud už máte nainstalovanou modul dotnet runtime.

```dotnetcli
dotnet publish
```

Zobrazí se výstup podobný následujícímu.

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

Výše uvedený výstup se může lišit v závislosti na vaší aktuální složce a operačním systému, výstup by měl být podobný.

Publikovanou aplikaci můžete spustit pomocí příkazu [dotnet](../tools/dotnet.md) :

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

Zobrazí se následující výstup.

```console
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

Jak je uvedeno na začátku tohoto článku, byl vytvořen spustitelný soubor specifický pro operační systém společně s nástrojem `Hello.dll` . Ve Windows by to bylo `Hello.exe` . v systému Linux nebo MacOS by to bylo `hello` . S výše uvedeným příkladem je soubor pojmenován s `Hello.exe` nebo `Hello` . Tento publikovaný spustitelný soubor můžete spustit přímo.

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

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

## <a name="conclusion"></a>Závěr

A to je vše! Teď můžete začít používat základní koncepty, které jste zde zjistili, k vytvoření vlastních programů.

## <a name="see-also"></a>Viz také

- [Organizování a testování projektů pomocí .NET Core CLI](testing-with-cli.md)
- [Publikování aplikací .NET Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md)
- [Nasazení aplikace .NET Core](../deploying/index.md)
