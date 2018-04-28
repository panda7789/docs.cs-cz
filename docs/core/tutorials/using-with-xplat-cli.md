---
title: Začínáme s .NET Core pomocí rozhraní příkazového řádku
description: Podrobný kurz znázorňující postup Začínáme s .NET Core v systému Windows, Linux nebo systému macOS pomocí rozhraní .NET Core příkazového řádku (CLI).
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.topic: get-started-article
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 23aec1b951c4b65d62bd4da4b4c94043b1411cf3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="76396-103">Začínáme s .NET Core v systému Windows nebo Linux/macOS pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="76396-103">Getting started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="76396-104">Toto téma vám ukáže, jak spustit vývoj aplikací pro různé platformy v počítači pomocí nástroje příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="76396-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="76396-105">Pokud jste obeznámeni s .NET Core rozhraní příkazového řádku sady nástrojů, přečtěte si [.NET Core SDK přehled](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="76396-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="76396-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76396-106">Prerequisites</span></span>

- <span data-ttu-id="76396-107">[.NET core SDK 1.0](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="76396-107">[.NET Core SDK 1.0](https://www.microsoft.com/net/download/core).</span></span>
- <span data-ttu-id="76396-108">Textového editoru nebo editoru kódu podle svého výběru.</span><span class="sxs-lookup"><span data-stu-id="76396-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="76396-109">Hello, konzolovou aplikaci!</span><span class="sxs-lookup"><span data-stu-id="76396-109">Hello, Console App!</span></span>

<span data-ttu-id="76396-110">Můžete [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z úložiště Githubu dotnet nebo ukázky.</span><span class="sxs-lookup"><span data-stu-id="76396-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="76396-111">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="76396-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="76396-112">Otevřete příkazový řádek a vytvořte složku s názvem *Hello*.</span><span class="sxs-lookup"><span data-stu-id="76396-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="76396-113">Přejděte do složky, kterou jste vytvořili a zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="76396-113">Navigate to the folder you created and type the following:</span></span>

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

<span data-ttu-id="76396-114">Umožňuje provést rychlé názorný postup:</span><span class="sxs-lookup"><span data-stu-id="76396-114">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="76396-115">[`dotnet new`](../tools/dotnet-new.md) Vytvoří aktuální `Hello.csproj` souboru projektu se závislostmi, které jsou potřebné k vytvoření konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="76396-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="76396-116">Vytvoří také `Program.cs`, základní souboru, který obsahuje vstupní bod pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="76396-116">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="76396-117">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="76396-117">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   <span data-ttu-id="76396-118">Soubor projektu určuje vše, co je potřeba k obnovení závislosti a sestavte program.</span><span class="sxs-lookup"><span data-stu-id="76396-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="76396-119">`OutputType` Značky Určuje, že vytváříme spustitelný soubor, jinými slovy konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="76396-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="76396-120">`TargetFramework` Značky Určuje, jaké implementace rozhraní .NET jsme se cílení na.</span><span class="sxs-lookup"><span data-stu-id="76396-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="76396-121">V pokročilém scénáři, můžete zadat několik cílové architektury a sestavení do všech těch v rámci jedné operace.</span><span class="sxs-lookup"><span data-stu-id="76396-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="76396-122">V tomto kurzu jsme budete přilepit k vytváření pouze pro rozhraní .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="76396-122">In this tutorial, we'll stick to building only for .NET Core 1.0.</span></span>

   <span data-ttu-id="76396-123">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="76396-123">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   <span data-ttu-id="76396-124">Program se spustí `using System`, tzn. "předány všechno, co `System` oboru názvů do oboru pro tento soubor".</span><span class="sxs-lookup"><span data-stu-id="76396-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="76396-125">`System` Obor názvů obsahuje základní konstrukce, jako `string`, nebo číselnými typy.</span><span class="sxs-lookup"><span data-stu-id="76396-125">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="76396-126">Potom jsme definovali obor názvů s názvem `Hello`.</span><span class="sxs-lookup"><span data-stu-id="76396-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="76396-127">Můžete to změnit na nic, co chcete.</span><span class="sxs-lookup"><span data-stu-id="76396-127">You can change this to anything you want.</span></span> <span data-ttu-id="76396-128">Třída s názvem `Program` je definována v daném oboru názvů pomocí `Main` metody, která přijímá pole řetězců jako její argument.</span><span class="sxs-lookup"><span data-stu-id="76396-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="76396-129">Toto pole obsahuje seznam argumentů předaná při volání zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="76396-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="76396-130">Protože se jedná, toto pole nepoužívá: všechny program provádí je napsat "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="76396-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="76396-131">ke konzole.</span><span class="sxs-lookup"><span data-stu-id="76396-131">to the console.</span></span> <span data-ttu-id="76396-132">Později, jsme budete provádět změny kódu, který bude používat argumentu.</span><span class="sxs-lookup"><span data-stu-id="76396-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   <span data-ttu-id="76396-133">[`dotnet restore`](../tools/dotnet-restore.md) volání [NuGet](https://www.nuget.org/) (.NET Správce balíčků) Chcete-li obnovit stromu závislosti.</span><span class="sxs-lookup"><span data-stu-id="76396-133">[`dotnet restore`](../tools/dotnet-restore.md) calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="76396-134">Analyzuje NuGet *Hello.csproj* souboru, stáhne závislosti uvedená v souboru (nebo je získá z mezipaměti na počítači) a zapíše *obj/project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="76396-134">NuGet analyzes the *Hello.csproj* file, downloads the dependencies stated in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file.</span></span>  <span data-ttu-id="76396-135">*Project.assets.json* souboru je nutné být schopni zkompilování a spuštění.</span><span class="sxs-lookup"><span data-stu-id="76396-135">The *project.assets.json* file is necessary to be able to compile and run.</span></span>
   
   <span data-ttu-id="76396-136">*Project.assets.json* soubor je trvalý a kompletní sadu grafu závislostí NuGet a jiné informace, které popisují aplikace.</span><span class="sxs-lookup"><span data-stu-id="76396-136">The *project.assets.json* file is a persisted and complete set of the graph of NuGet dependencies and other information describing an app.</span></span>  <span data-ttu-id="76396-137">Tento soubor je pro čtení pomocí jiných nástrojů, jako například [ `dotnet build` ](../tools/dotnet-build.md) a [ `dotnet run` ](../tools/dotnet-run.md), povolením procesu zdrojového kódu se správnou sadou závislostí NuGet a vytvoření vazby řešení.</span><span class="sxs-lookup"><span data-stu-id="76396-137">This file is read by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), enabling them to process the source code with a correct set of NuGet dependencies and binding resolutions.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="76396-138">[`dotnet run`](../tools/dotnet-run.md) volání [ `dotnet build` ](../tools/dotnet-build.md) zajistit, aby sestavení, které se sestavily cíle a poté zavolá `dotnet <assembly.dll>` ke spuštění cílová aplikace.</span><span class="sxs-lookup"><span data-stu-id="76396-138">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>
   
    ```
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="76396-139">Alternativně můžete také provést [ `dotnet build` ](../tools/dotnet-build.md) zkompilovat kód bez spuštění sestavení konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="76396-139">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="76396-140">Výsledkem je kompilované aplikace jako soubor knihovny DLL, která lze spustit s `dotnet bin\Debug\netcoreapp1.0\Hello.dll` v systému Windows (použijte `/` pro jiné operační systémy).</span><span class="sxs-lookup"><span data-stu-id="76396-140">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp1.0\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="76396-141">Argumenty pro aplikaci můžete také určit jako budete později na naleznete v tématu.</span><span class="sxs-lookup"><span data-stu-id="76396-141">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="76396-142">V pokročilém scénáři je možné vytvořit aplikace jako samostatná sada souborů specifických pro platformy, které můžete nasadit a spustit pro počítač, který nemusí mít nainstalovaný .NET Core.</span><span class="sxs-lookup"><span data-stu-id="76396-142">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="76396-143">V tématu [nasazení aplikace .NET Core](../deploying/index.md) podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="76396-143">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="76396-144">Rozšířit programu</span><span class="sxs-lookup"><span data-stu-id="76396-144">Augmenting the program</span></span>

<span data-ttu-id="76396-145">Umožňuje programu trochu změnit.</span><span class="sxs-lookup"><span data-stu-id="76396-145">Let's change the program a bit.</span></span> <span data-ttu-id="76396-146">Čísla Fibonacciho fun, takže umožňuje přidat, kromě použijte argument pozdravit osoba spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="76396-146">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="76396-147">Nahraďte obsah vaší *Program.cs* soubor s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="76396-147">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. <span data-ttu-id="76396-148">Spuštění [ `dotnet build` ](../tools/dotnet-build.md) zkompilovat změny.</span><span class="sxs-lookup"><span data-stu-id="76396-148">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="76396-149">Spusťte program předání parametru aplikace:</span><span class="sxs-lookup"><span data-stu-id="76396-149">Run the program passing a parameter to the app:</span></span>

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

<span data-ttu-id="76396-150">A je to!</span><span class="sxs-lookup"><span data-stu-id="76396-150">And that's it!</span></span>  <span data-ttu-id="76396-151">Můžete `Program.cs` jakýmkoli způsobem se vám líbí.</span><span class="sxs-lookup"><span data-stu-id="76396-151">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="76396-152">Práce s více soubory</span><span class="sxs-lookup"><span data-stu-id="76396-152">Working with multiple files</span></span>

<span data-ttu-id="76396-153">Jeden soubory jsou vhodná pro jednoduché jednorázové programy, ale pokud vytváříte složitější aplikaci, jste pravděpodobně budete mít více zdrojových souborů v projektu umožňuje sestavení z předchozí příklad Fibonacciho pomocí ukládání do mezipaměti některé hodnoty Fibonacciho a přidat některé rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="76396-153">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span> 

1. <span data-ttu-id="76396-154">Přidat nový soubor uvnitř *Hello* adresář s názvem *FibonacciGenerator.cs* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="76396-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. <span data-ttu-id="76396-155">Změna `Main` metoda v vaše *Program.cs* soubor k vytvoření instance nová třída a volejte příslušnou metodu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="76396-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="76396-156">Spuštění [ `dotnet build` ](../tools/dotnet-build.md) zkompilovat změny.</span><span class="sxs-lookup"><span data-stu-id="76396-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="76396-157">Spuštění aplikace spuštěním [ `dotnet run` ](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="76396-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="76396-158">Výstup programu obrázku:</span><span class="sxs-lookup"><span data-stu-id="76396-158">The following shows the program output:</span></span>

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

<span data-ttu-id="76396-159">A je to!</span><span class="sxs-lookup"><span data-stu-id="76396-159">And that's it!</span></span> <span data-ttu-id="76396-160">Teď můžete začít používat se základními koncepty se naučili v tomto poli vytvořit vlastní programy.</span><span class="sxs-lookup"><span data-stu-id="76396-160">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

<span data-ttu-id="76396-161">Všimněte si, že příkazy a postupy v tomto kurzu ke spuštění vaší aplikace se používají během doby vývoje pouze.</span><span class="sxs-lookup"><span data-stu-id="76396-161">Note that the commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="76396-162">Jakmile budete připraveni k nasazení své aplikace, budete chtít podívejte se na různými [strategie nasazení](../deploying/index.md) pro aplikace .NET Core a [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="76396-162">Once you're ready to deploy your app, you'll want to take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

## <a name="see-also"></a><span data-ttu-id="76396-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="76396-163">See also</span></span>

[<span data-ttu-id="76396-164">Uspořádání a testování projektů pomocí nástrojů .NET Core rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="76396-164">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
