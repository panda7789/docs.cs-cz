---
title: Začínáme s .NET Core s využitím rozhraní příkazového řádku
description: Podrobný kurz ukazující, jak začít s .NET Core v systému Windows, Linux nebo macOS pomocí rozhraní příkazového řádku (CLI) .NET Core.
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: cf8c3ae070f4c77789dc55ba4d7888c7b15c8653
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736991"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Začínáme s .NET Core v systému Windows, Linux nebo macOS pomocí příkazového řádku

V tomto tématu se dozvíte, jak na svém počítači začít vyvíjet aplikace pro různé platformy pomocí nástrojů pro .NET Core CLI.

Pokud nejste obeznámeni se sadou nástrojů .NET Core CLI, přečtěte si [přehled .NET Core SDK](../tools/index.md).

## <a name="prerequisites"></a>Požadavky

- [.NET Core SDK 2,1](https://dotnet.microsoft.com/download) nebo novější verze.
- Textový editor nebo Editor kódu dle vašeho výběru.

## <a name="hello-console-app"></a>Hello, konzolová aplikace!

[Vzorový kód můžete zobrazit nebo stáhnout](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z úložiště GitHub/Samples GitHub. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otevřete příkazový řádek a vytvořte složku s názvem *Hello*. Přejděte do složky, kterou jste vytvořili, a zadejte následující:

```dotnetcli
dotnet new console
dotnet run
```

Podívejme se na stručný návod:

1. `dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) vytvoří aktuální soubor projektu *Hello. csproj* se závislostmi nezbytnými pro sestavení konzolové aplikace. Vytvoří také základní soubor *program.cs*, který obsahuje vstupní bod pro aplikaci.

   *Hello. csproj*:

   [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   Soubor projektu určuje vše potřebné k obnovení závislostí a sestavování programu.

   - Značka `OutputType` určuje, že vytváříme spustitelný soubor, a to v jiných slovech konzolové aplikace.
   - Značka `TargetFramework` určuje, jakou implementaci .NET cílíme. V pokročilém scénáři můžete zadat více cílových rozhraní a sestavit je pro všechny v rámci jedné operace. V tomto kurzu se podíváme na vytváření jenom pro .NET Core 2,1.

   *Program.cs*:

   [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]

   Program se spustí `using System`, což znamená "přenést vše do oboru názvů `System` do rozsahu pro tento soubor". Obor názvů `System` obsahuje třídu `Console`.

   Pak definujeme obor názvů s názvem `Hello`. Můžete to změnit na cokoli, co potřebujete. Třída s názvem `Program` je definována v rámci tohoto oboru názvů s metodou `Main`, která přebírá pole řetězců jako argument. Toto pole obsahuje seznam argumentů předaných při volání zkompilovaného programu. V takovém případě se toto pole nepoužívá: celý program provádí zápis "Hello World!". do konzoly. Později provedeme změny kódu, který tento argument využije.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   `dotnet new` volá implicitně [`dotnet restore`](../tools/dotnet-restore.md) . `dotnet restore` volání [NuGet](https://www.nuget.org/) (Správce balíčků .NET) pro obnovení stromu závislostí. NuGet analyzuje soubor *Hello. csproj* , stáhne závislosti definované v souboru (nebo je z mezipaměti v počítači převede) a zapíše soubor *obj/Project. assets. JSON* , který je nezbytný pro zkompilování a spuštění ukázky.

   > [!IMPORTANT]
   > Pokud používáte verzi sady SDK .NET Core 1. x, bude po volání `dotnet new`nutné volat `dotnet restore` sami.

2. `dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) volá [`dotnet build`](../tools/dotnet-build.md) , aby bylo zajištěno, že byly sestaveny cíle sestavení, a poté volá `dotnet <assembly.dll>` pro spuštění cílové aplikace.

    ```console
    $ dotnet run
    Hello World!
    ```

    Alternativně můžete také spustit [`dotnet build`](../tools/dotnet-build.md) pro zkompilování kódu bez spuštění konzolových aplikací sestavení. Výsledkem je kompilovaná aplikace jako soubor DLL, který lze spustit s `dotnet bin\Debug\netcoreapp2.1\Hello.dll` ve Windows (použijte `/` pro systémy jiné než Windows). Můžete také zadat argumenty aplikace, jak uvidíte později v tématu.

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    V rámci pokročilého scénáře je možné aplikaci sestavit jako samostatnou sadu souborů specifických pro platformu, které je možné nasadit a spustit v počítači, který nutně nemá nainstalovaný .NET Core. Podrobnosti najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .

### <a name="augmenting-the-program"></a>Rozšíření programu

Pojďme program trochu změnit. Fibonacci čísla jsou zábavné, takže přidáváme kromě toho také použití argumentu k přání uživatele, který aplikaci spouští.

1. Obsah souboru *program.cs* nahraďte následujícím kódem:

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. Spusťte [`dotnet build`](../tools/dotnet-build.md) pro zkompilování změn.

3. Spusťte program předáním parametru do aplikace:

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

A je to!  *Program.cs* můžete rozšířit jakýmkoli způsobem.

## <a name="working-with-multiple-files"></a>Práce s více soubory

Jednotlivé soubory jsou pro jednoduché jednorázové programy přesné, ale pokud sestavíte komplexnější aplikaci, pravděpodobně budete mít v projektu více zdrojových souborů.
Pojďme si vytvořit z předchozího příkladu Fibonacci ukládáním do mezipaměti některé hodnoty Fibonacci a přidat některé rekurzivní funkce.

1. Přidejte nový soubor do adresáře *Hello* s názvem *FibonacciGenerator.cs* s následujícím kódem:

   [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. Změňte metodu `Main` v souboru *program.cs* pro vytvoření instance nové třídy a zavolejte její metodu jako v následujícím příkladu:

   [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Spusťte [`dotnet build`](../tools/dotnet-build.md) pro zkompilování změn.

4. Spusťte aplikaci spuštěním [`dotnet run`](../tools/dotnet-run.md). Následující příklad ukazuje výstup programu:

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

Až budete připraveni k distribuci vaší aplikace, pomocí příkazu [`dotnet publish`](../tools/dotnet-publish.md) vygenerujte složku pro _publikování_ v _přihrádce\\ladění\\netcoreapp 2.1\\publikovat\\_ (použijte `/` pro systémy jiné než Windows). Obsah složky pro _publikování_ můžete distribuovat na jiné platformy, pokud už máte nainstalovanou modul dotnet runtime.

Publikovanou aplikaci můžete spustit pomocí příkazu [dotnet](../tools/dotnet.md) :

```console
$ dotnet bin\Debug\netcoreapp2.1\publish\Hello.dll
Hello World!
```

## <a name="conclusion"></a>Závěr

A je to! Teď můžete začít používat základní koncepty, které jste zde zjistili, k vytvoření vlastních programů.

## <a name="see-also"></a>Viz také:

- [Organizování a testování projektů pomocí .NET Core CLIch nástrojů](testing-with-cli.md)
- [Publikování aplikací .NET Core pomocí rozhraní příkazového řádku](../deploying/deploy-with-cli.md)
- [Další informace o nasazení aplikace](../deploying/index.md)
