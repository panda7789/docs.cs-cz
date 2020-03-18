---
title: Začínáme s .NET Core v rozhraní příkazového řádku
description: Podrobný kurz, který ukazuje, jak začít s rozhraním .NET Core ve Windows, Linuxu nebo macOS pomocí rozhraní .NET Core CLI.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240854"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>Začínáme s rozhraním .NET Core pomocí rozhraní CLI jádra .NET

Tento článek vám ukáže, jak začít vyvíjet aplikace .NET Core, které fungují ve Windows, Linuxu a macOS pomocí rozhraní .NET Core CLI.

Pokud nejste obeznámeni s rozhraním .NET Core CLI, podívejte se na [přehled rozhraní .NET Core CLI](../tools/index.md).

## <a name="prerequisites"></a>Požadavky

- [Sada .NET Core SDK 3.1](https://dotnet.microsoft.com/download) nebo novější verze.
- Textový editor nebo editor kódu podle vašeho výběru.

## <a name="hello-console-app"></a>Dobrý den, konzole App!

[Ukázkový kód](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) můžete zobrazit nebo stáhnout z úložiště GitHub dotnet/samples. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otevřete příkazový řádek a vytvořte složku s názvem *Hello*. Přejděte do složky, kterou jste vytvořili, a zadejte následující.

```dotnetcli
dotnet new console
dotnet run
```

Udělejme rychlý návod:

01. `dotnet new console`

    [dotnet new](../tools/dotnet-new.md) vytvoří aktuální soubor projektu *Hello.csproj* se závislostmi potřebnými k vytvoření konzolové aplikace. Vytvoří také *Program.cs*, základní soubor obsahující vstupní bod pro aplikaci.

    *Hello.csproj*:

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    Soubor projektu určuje vše, co je potřeba k obnovení závislostí a sestavení programu.

    - Prvek `<OutputType>` určuje, že vytváříme spustitelný soubor, jinými slovy konzolovou aplikaci.
    - Prvek `<TargetFramework>` určuje, na jakou implementaci rozhraní .NET cílíme. V rozšířeném scénáři můžete zadat více cílových architektur a sestavit pro všechny v jedné operaci. V tomto kurzu se budeme držet vytváření pouze pro rozhraní .NET Core 3.1.

    *Program.cs*:

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    Program začíná `using System`, což znamená "přenést `System` vše v oboru názvů do oboru pro tento soubor". Obor `System` názvů obsahuje `Console` třídu.

    Poté definujeme obor `Hello`názvů s názvem . Můžete to změnit na cokoliv chcete. Třída s `Program` názvem je definována v `Main` tomto oboru názvů s `args`metodou, která přebírá pole řetězců s názvem . Toto pole obsahuje seznam argumentů předaných při spuštění programu. Jak to je, toto pole se nepoužívá a program jednoduše zapíše text "Hello World!" „Hello, World!“. Později provedeme změny kódu, který bude používat tento argument.

    `dotnet new`volání [dotnet obnovit](../tools/dotnet-restore.md) implicitně. `dotnet restore`volá do [NuGet](https://www.nuget.org/) (správce balíčků.NET) k obnovení stromu závislostí. NuGet analyzuje soubor *Hello.csproj,* stáhne závislosti definované v souboru (nebo je uchopí z mezipaměti v počítači) a zapíše soubor *obj/project.assets.json,* který je nezbytný pro kompilaci a spuštění ukázky.

02. `dotnet run`

    [dotnet spustit](../tools/dotnet-run.md) volání [dotnet sestavení](../tools/dotnet-build.md) zajistit, že cíle sestavení `dotnet <assembly.dll>` byly vytvořeny a potom volání ke spuštění cílové aplikace.

    ```dotnetcli
    dotnet run
    ```

    Získáte následující výstup.

    ```console
    Hello World!
    ```

    Alternativně můžete také `dotnet build` spustit ke kompilaci kódu bez spuštění aplikací konzoly sestavení. Výsledkem je zkompilovaná aplikace jako soubor DLL na základě názvu projektu. V tomto případě se vytvořený soubor nazývá *Hello.dll*. Tato aplikace může `dotnet bin\Debug\netcoreapp3.1\Hello.dll` být spuštěna `/` v systému Windows (použití pro systémy, které nejsou systémy Windows).

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    Získáte následující výstup.

    ```console
    Hello World!
    ```

    Při kompilaci aplikace byl vytvořen spustitelný soubor specifický pro `Hello.dll`operační systém spolu s souborem . V systému Windows `Hello.exe`by to bylo ; na Linuxu nebo macOS, to by bylo `hello`. S výše uvedeným příkladem je `Hello.exe` soubor `Hello`pojmenován s nebo . Tento spustitelný soubor můžete spustit přímo.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Úprava programu

Pojďme trochu změnit program. Fibonaccičísla jsou zábavné, takže přidejme, že a také použít argument pozdravit osobu, která provozuje aplikaci.

01. Nahraďte obsah *Program.cs* souboru následujícím kódem:

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. Spusťte [sestavení dotnet](../tools/dotnet-build.md) a zkompilujte změny.

03. Spusťte program předání parametru do aplikace. Když pomocí `dotnet` příkazu spustíte aplikaci, přidejte `--` ji na konec. Cokoli vpravo `--` od bude předáno jako parametr do aplikace. V následujícím příkladu `John` je hodnota předána aplikaci.

    ```dotnetcli
    dotnet run -- John
    ```

    Získáte následující výstup.

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

A to je vše! Můžete *Program.cs* libovolně upravovat.

## <a name="working-with-multiple-files"></a>Práce s více soubory

Jednotlivé soubory jsou v pořádku pro jednoduché jednorázové programy, ale pokud vytváříte složitější aplikaci, pravděpodobně budete mít v projektu více souborů kódu. Pojďme sestavit z předchozího příkladu Fibonacciho ukládáním některých hodnot Fibonacciho do mezipaměti a přidáním některých rekurzivních funkcí.

01. Přidejte nový soubor do adresáře *Hello* s názvem *FibonacciGenerator.cs* s následujícím kódem:

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. Změňte `Main` metodu v *souboru Program.cs* k vytvoření instance nové třídy a volání její metody jako v následujícím příkladu:

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. Spusťte [sestavení dotnet](../tools/dotnet-build.md) a zkompilujte změny.

04. Spusťte aplikaci spuštěním [dotnet run](../tools/dotnet-run.md).

    ```dotnetcli
    dotnet run
    ```

    Získáte následující výstup.

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

Jakmile budete připraveni distribuovat aplikaci, použijte příkaz [dotnet publish](../tools/dotnet-publish.md) ke generování složky _publikování_ při _publikování\\\\\\\\ ladění aplikace netcoreapp3.1_ (používá se `/` pro systémy, které nejsou systémy Windows). Obsah složky _publikování_ můžete distribuovat na jiné platformy, pokud již nainstalovali dotnet runtime.

```dotnetcli
dotnet publish
```

Získáte výstup podobný následující.

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

Výše uvedený výstup se může lišit v závislosti na aktuální složce a operačním systému, ale výstup by měl být podobný.

Publikovanou aplikaci můžete spustit pomocí příkazu [dotnet:](../tools/dotnet.md)

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

Získáte následující výstup.

```console
Hello World!
```

Jak již bylo zmíněno na začátku tohoto článku, byl vytvořen `Hello.dll`spustitelný soubor specifický pro operační systém spolu s souborem . V systému Windows `Hello.exe`by to bylo ; na Linuxu nebo macOS, to by bylo `hello`. S výše uvedeným příkladem je `Hello.exe` soubor `Hello`pojmenován s nebo . Tento publikovaný spustitelný soubor můžete spustit přímo.

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a>Závěr

A to je vše! Nyní můžete začít používat základní koncepty zde naučil vytvořit si vlastní programy.

## <a name="see-also"></a>Viz také

- [Uspořádání a testování projektů pomocí rozhraní CLI jádra .NET](testing-with-cli.md)
- [Publikování aplikací .NET Core pomocí rozhraní CLI jádra ROZHRANÍ .NET](../deploying/deploy-with-cli.md)
- [Nasazení aplikace .NET Core](../deploying/index.md)
