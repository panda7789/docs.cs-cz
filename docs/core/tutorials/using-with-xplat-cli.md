---
title: Začínáme s .NET Core pomocí rozhraní příkazového řádku
description: Podrobný návod ukazuje, jak začít pracovat s .NET Core ve Windows, Linux nebo macOS pomocí rozhraní příkazového řádku .NET Core (CLI).
author: cartermp
ms.author: mairaw
ms.date: 09/10/2018
ms.technology: dotnet-cli
ms.openlocfilehash: b31a0324c0d762e9898c681cc6581b3860d41f89
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203758"
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Začínáme s .NET Core ve Windows, Linux nebo macOS pomocí příkazového řádku

Toto téma se ukazují, jak začít s vývojem aplikací napříč platformami ve vašem počítači pomocí nástroje příkazového řádku .NET Core.

Pokud nejste obeznámeni s sada nástrojů .NET Core CLI, přečtěte si [.NET Core SDK přehled](../tools/index.md).

## <a name="prerequisites"></a>Požadavky

- [.NET core SDK 2.1](https://www.microsoft.com/net/download/core).
- Textového editoru nebo editoru kódu podle vašeho výběru.

## <a name="hello-console-app"></a>Dobrý den, konzolová aplikace!

Je možné [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) v úložišti dotnet/samples Githubu. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Otevřete příkazový řádek a vytvořte složku s názvem *Hello*. Přejděte do složky, kterou jste vytvořili a zadejte následující příkaz:

```console
$ dotnet new console
$ dotnet run
```

Pojďme si rychlý návod:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) Vytvoří aktuální `Hello.csproj` soubor projektu se závislostmi, které jsou potřebné k sestavení aplikace konzoly.  Vytvoří se také `Program.cs`, základní soubor, který obsahuje vstupní bod pro aplikaci.

   `Hello.csproj`:

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   Soubor projektu určuje vše, co je potřeba k obnovení závislostí a sestavit program.

   * `OutputType` Značka Určuje, že vytváříme spustitelný soubor, jinými slovy konzolové aplikace.
   * `TargetFramework` Značky Určuje, jaké implementace .NET jsme cílíte. V pokročilém scénáři, můžete zadat více cílových platforem a sestavit pro všechny ty v rámci jedné operace. V tomto kurzu se budeme držet sestavení pouze pro .NET Core 1.0.

   `Program.cs`:

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   Program spustí s `using System`, což znamená, že "umožňuje přinést si všechno, co `System` oboru názvů do oboru pro tento soubor". `System` Obor názvů obsahuje základní konstrukce, jako `string`, nebo číselné typy.

   My pak definovat obor názvů s názvem `Hello`. Můžete to změnit na všechno, co chcete. Třída s názvem `Program` je definována v daném oboru názvů s `Main` metodu, která přijímá pole řetězců jako svůj argument. Toto pole se seznamem argumentů předaných v při volání zkompilovaný program. Protože se jedná, se nepoužívá tato pole: všechny provádění programu je napsat "Hello World!" do konzoly. Později, uděláme změny kódu, který bude pomocí tohoto argumentu.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   `dotnet new` volání [ `dotnet restore` ](../tools/dotnet-restore.md) implicitně. `dotnet restore` volání do [NuGet](https://www.nuget.org/) (.NET Správce balíčků) Chcete-li obnovit strom závislostí. Analyzuje NuGet *Hello.csproj* soubor, soubory ke stažení závislosti definované v souboru (nebo získá z mezipaměti na svém počítači) a zapíše *obj/project.assets.json* soubor, který je potřeba kompilace a spuštění ukázky. 
   
   > [!IMPORTANT]
   > Pokud používáte verzi sady SDK .NET Core 1.x, budete muset volat `dotnet restore` sami po volání `dotnet new`.

2. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) volání [ `dotnet build` ](../tools/dotnet-build.md) zajistit, aby se sestavily cíle sestavení a poté zavolá `dotnet <assembly.dll>` spustit cílovou aplikaci.

    ```console
    $ dotnet run
    Hello World!
    ```

    Alternativně můžete také spustit [ `dotnet build` ](../tools/dotnet-build.md) pro kompilaci kódu bez nutnosti spuštění sestavení konzolové aplikace. Výsledkem je kompilovanou aplikaci jako soubor DLL, který můžete spustit s `dotnet bin\Debug\netcoreapp2.1\Hello.dll` na Windows (použijte `/` systémů než Windows). Argumenty do aplikace můžete také zadat jak uvidíte později v tématu.
    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    Což je pokročilý scénář je možné vytvořit aplikace jako samostatná sada souborů specifické pro platformu, které je možné nasadit a spustit na počítači, který nemusí nainstalovat .NET Core. Zobrazit [nasazení aplikace .NET Core](../deploying/index.md) podrobnosti.

### <a name="augmenting-the-program"></a>Rozšíření programu

Pojďme trochu změnit program. Čísla Fibonacciho Zábava, přidejme tedy, že kromě použijte argument pozdravili uživatele spuštění aplikace.

1. Nahraďte obsah vaší *Program.cs* souboru následujícím kódem:

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. Spustit [ `dotnet build` ](../tools/dotnet-build.md) pro kompilaci změn.

3. Spusťte program předávání parametru do aplikace:

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

A to je všechno!  Můžete rozšířit `Program.cs` jakkoli chcete.

## <a name="working-with-multiple-files"></a>Práce s více soubory

Jednotlivé soubory, které se dají pro jednoduché jednorázové programy, ale využijete při vytváření složitějších aplikací, budete pravděpodobně to můžeme mít více zdrojové soubory projektu pro sestavení z předchozího příkladu Fibonacciho ukládáním hodnoty Fibonacciho a přidat některé rekurzivní funkce.

1. Přidat nový soubor *Hello* adresář s názvem *FibonacciGenerator.cs* následujícím kódem:

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. Změnit `Main` metoda ve vaší *Program.cs* soubor k vytvoření nové instance třídy a volání metody jako v následujícím příkladu:

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Spustit [ `dotnet build` ](../tools/dotnet-build.md) pro kompilaci změn.

4. Spusťte aplikaci spuštěním [ `dotnet run` ](../tools/dotnet-run.md). Následuje ukázka výstupu programu:

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

A to je všechno! Teď můžete začít používat základní koncepty se tady naučili vytvořit své vlastní programy.

Všimněte si, že příkazy a postupy v tomto kurzu ke spuštění aplikace se používají pouze během vývoje. Jakmile budete připraveni k nasazení své aplikace, budete chtít podívat na různé [strategie nasazení](../deploying/index.md) pro aplikace .NET Core a [ `dotnet publish` ](../tools/dotnet-publish.md) příkazu.

## <a name="see-also"></a>Viz také:

* [Uspořádání a testování projektů pomocí nástroje příkazového řádku .NET Core](testing-with-cli.md)
