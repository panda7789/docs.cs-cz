---
title: Začínáme s .NET Core pomocí rozhraní příkazového řádku
description: Podrobný kurz znázorňující postup Začínáme s .NET Core v systému Windows, Linux nebo systému macOS pomocí rozhraní .NET Core příkazového řádku (CLI).
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.technology: dotnet-cli
ms.openlocfilehash: 57045a91ce62a730493d219bdf7c30e90fe57759
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216337"
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Začínáme s .NET Core v systému Windows nebo Linux/macOS pomocí příkazového řádku

Toto téma vám ukáže, jak spustit vývoj aplikací pro různé platformy v počítači pomocí nástroje příkazového řádku .NET Core.

Pokud jste obeznámeni s .NET Core rozhraní příkazového řádku sady nástrojů, přečtěte si [.NET Core SDK přehled](../tools/index.md).

## <a name="prerequisites"></a>Požadavky

- [.NET core SDK 1.0](https://www.microsoft.com/net/download/core).
- Textového editoru nebo editoru kódu podle svého výběru.

## <a name="hello-console-app"></a>Hello, konzolovou aplikaci!

Můžete [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z úložiště Githubu dotnet nebo ukázky. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otevřete příkazový řádek a vytvořte složku s názvem *Hello*. Přejděte do složky, kterou jste vytvořili a zadejte následující příkaz:

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

Umožňuje provést rychlé názorný postup:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) Vytvoří aktuální `Hello.csproj` souboru projektu se závislostmi, které jsou potřebné k vytvoření konzolové aplikace.  Vytvoří také `Program.cs`, základní souboru, který obsahuje vstupní bod pro aplikaci.
   
   `Hello.csproj`:

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   Soubor projektu určuje vše, co je potřeba k obnovení závislosti a sestavte program.

   * `OutputType` Značky Určuje, že vytváříme spustitelný soubor, jinými slovy konzolové aplikace.
   * `TargetFramework` Značky Určuje, jaké implementace rozhraní .NET jsme se cílení na. V pokročilém scénáři, můžete zadat několik cílové architektury a sestavení do všech těch v rámci jedné operace. V tomto kurzu jsme budete přilepit k vytváření pouze pro rozhraní .NET Core 1.0.

   `Program.cs`:

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   Program se spustí `using System`, tzn. "předány všechno, co `System` oboru názvů do oboru pro tento soubor". `System` Obor názvů obsahuje základní konstrukce, jako `string`, nebo číselnými typy.

   Potom jsme definovali obor názvů s názvem `Hello`. Můžete to změnit na nic, co chcete. Třída s názvem `Program` je definována v daném oboru názvů pomocí `Main` metody, která přijímá pole řetězců jako její argument. Toto pole obsahuje seznam argumentů předaná při volání zkompilovaný program. Protože se jedná, toto pole nepoužívá: všechny program provádí je napsat "Hello, World!" ke konzole. Později, jsme budete provádět změny kódu, který bude používat argumentu.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) volání [NuGet](https://www.nuget.org/) (.NET Správce balíčků) Chcete-li obnovit stromu závislosti. Analyzuje NuGet *Hello.csproj* souboru, stáhne závislosti uvedená v souboru (nebo je získá z mezipaměti na počítači) a zapíše *obj/project.assets.json* souboru.  *Project.assets.json* souboru je nutné být schopni zkompilování a spuštění.
   
   *Project.assets.json* soubor je trvalý a kompletní sadu grafu závislostí NuGet a jiné informace, které popisují aplikace.  Tento soubor je pro čtení pomocí jiných nástrojů, jako například [ `dotnet build` ](../tools/dotnet-build.md) a [ `dotnet run` ](../tools/dotnet-run.md), povolením procesu zdrojového kódu se správnou sadou závislostí NuGet a vytvoření vazby řešení.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) volání [ `dotnet build` ](../tools/dotnet-build.md) zajistit, aby sestavení, které se sestavily cíle a poté zavolá `dotnet <assembly.dll>` ke spuštění cílová aplikace.
   
    ```
    $ dotnet run
    Hello World!
    ```

    Alternativně můžete také provést [ `dotnet build` ](../tools/dotnet-build.md) zkompilovat kód bez spuštění sestavení konzolové aplikace. Výsledkem je kompilované aplikace jako soubor knihovny DLL, která lze spustit s `dotnet bin\Debug\netcoreapp1.0\Hello.dll` v systému Windows (použijte `/` pro jiné operační systémy). Argumenty pro aplikaci můžete také určit jako budete později na naleznete v tématu.

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    V pokročilém scénáři je možné vytvořit aplikace jako samostatná sada souborů specifických pro platformy, které můžete nasadit a spustit pro počítač, který nemusí mít nainstalovaný .NET Core. V tématu [nasazení aplikace .NET Core](../deploying/index.md) podrobnosti.

### <a name="augmenting-the-program"></a>Rozšířit programu

Umožňuje programu trochu změnit. Čísla Fibonacciho fun, takže umožňuje přidat, kromě použijte argument pozdravit osoba spuštění aplikace.

1. Nahraďte obsah vaší *Program.cs* soubor s následujícím kódem:

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. Spuštění [ `dotnet build` ](../tools/dotnet-build.md) zkompilovat změny.

3. Spusťte program předání parametru aplikace:

   ```
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

A je to!  Můžete `Program.cs` jakýmkoli způsobem se vám líbí.

## <a name="working-with-multiple-files"></a>Práce s více soubory

Jeden soubory jsou vhodná pro jednoduché jednorázové programy, ale pokud vytváříte složitější aplikaci, jste pravděpodobně budete mít více zdrojových souborů v projektu umožňuje sestavení z předchozí příklad Fibonacciho pomocí ukládání do mezipaměti některé hodnoty Fibonacciho a přidat některé rekurzivní funkce. 

1. Přidat nový soubor uvnitř *Hello* adresář s názvem *FibonacciGenerator.cs* následujícím kódem:

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. Změna `Main` metoda v vaše *Program.cs* soubor k vytvoření instance nová třída a volejte příslušnou metodu jako v následujícím příkladu:

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Spuštění [ `dotnet build` ](../tools/dotnet-build.md) zkompilovat změny.

4. Spuštění aplikace spuštěním [ `dotnet run` ](../tools/dotnet-run.md). Výstup programu obrázku:

   ```
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

A je to! Teď můžete začít používat se základními koncepty se naučili v tomto poli vytvořit vlastní programy.

Všimněte si, že příkazy a postupy v tomto kurzu ke spuštění vaší aplikace se používají během doby vývoje pouze. Jakmile budete připraveni k nasazení své aplikace, budete chtít podívejte se na různými [strategie nasazení](../deploying/index.md) pro aplikace .NET Core a [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz.

## <a name="see-also"></a>Viz také

[Uspořádání a testování projektů pomocí nástrojů .NET Core rozhraní příkazového řádku](testing-with-cli.md)
