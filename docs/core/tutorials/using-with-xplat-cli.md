---
title: Začínáme s .NET Core pomocí rozhraní příkazového řádku
description: Podrobný návod ukazuje, jak začít pracovat s .NET Core ve Windows, Linux nebo macOS pomocí rozhraní příkazového řádku .NET Core (CLI).
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.technology: dotnet-cli
ms.openlocfilehash: 5ec7168ebc2ee4fc428d1ab520e986842f111ca7
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43256762"
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="2b1f9-103">Začínáme s .NET Core ve Windows, Linux nebo macOS pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2b1f9-103">Getting started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="2b1f9-104">Toto téma se ukazují, jak začít s vývojem aplikací napříč platformami ve vašem počítači pomocí nástroje příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="2b1f9-105">Pokud nejste obeznámeni s sada nástrojů .NET Core CLI, přečtěte si [.NET Core SDK přehled](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="2b1f9-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2b1f9-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b1f9-106">Prerequisites</span></span>

- <span data-ttu-id="2b1f9-107">[.NET core SDK 1.0](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="2b1f9-107">[.NET Core SDK 1.0](https://www.microsoft.com/net/download/core).</span></span>
- <span data-ttu-id="2b1f9-108">Textového editoru nebo editoru kódu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="2b1f9-109">Dobrý den, konzolová aplikace!</span><span class="sxs-lookup"><span data-stu-id="2b1f9-109">Hello, Console App!</span></span>

<span data-ttu-id="2b1f9-110">Je možné [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) v úložišti dotnet/samples Githubu.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="2b1f9-111">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="2b1f9-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="2b1f9-112">Otevřete příkazový řádek a vytvořte složku s názvem *Hello*.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="2b1f9-113">Přejděte do složky, kterou jste vytvořili a zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="2b1f9-113">Navigate to the folder you created and type the following:</span></span>

```console
$ dotnet new console
$ dotnet restore
$ dotnet run
```

<span data-ttu-id="2b1f9-114">Pojďme si rychlý návod:</span><span class="sxs-lookup"><span data-stu-id="2b1f9-114">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="2b1f9-115">[`dotnet new`](../tools/dotnet-new.md) Vytvoří aktuální `Hello.csproj` soubor projektu se závislostmi, které jsou potřebné k sestavení aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="2b1f9-116">Vytvoří se také `Program.cs`, základní soubor, který obsahuje vstupní bod pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-116">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="2b1f9-117">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="2b1f9-117">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   <span data-ttu-id="2b1f9-118">Soubor projektu určuje vše, co je potřeba k obnovení závislostí a sestavit program.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="2b1f9-119">`OutputType` Značka Určuje, že vytváříme spustitelný soubor, jinými slovy konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="2b1f9-120">`TargetFramework` Značky Určuje, jaké implementace .NET jsme cílíte.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="2b1f9-121">V pokročilém scénáři, můžete zadat více cílových platforem a sestavit pro všechny ty v rámci jedné operace.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="2b1f9-122">V tomto kurzu se budeme držet sestavení pouze pro .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-122">In this tutorial, we'll stick to building only for .NET Core 1.0.</span></span>

   <span data-ttu-id="2b1f9-123">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="2b1f9-123">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   <span data-ttu-id="2b1f9-124">Program spustí s `using System`, což znamená, že "umožňuje přinést si všechno, co `System` oboru názvů do oboru pro tento soubor".</span><span class="sxs-lookup"><span data-stu-id="2b1f9-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="2b1f9-125">`System` Obor názvů obsahuje základní konstrukce, jako `string`, nebo číselné typy.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-125">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="2b1f9-126">My pak definovat obor názvů s názvem `Hello`.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="2b1f9-127">Můžete to změnit na všechno, co chcete.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-127">You can change this to anything you want.</span></span> <span data-ttu-id="2b1f9-128">Třída s názvem `Program` je definována v daném oboru názvů s `Main` metodu, která přijímá pole řetězců jako svůj argument.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="2b1f9-129">Toto pole se seznamem argumentů předaných v při volání zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="2b1f9-130">Protože se jedná, se nepoužívá tato pole: všechny provádění programu je napsat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="2b1f9-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="2b1f9-131">do konzoly.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-131">to the console.</span></span> <span data-ttu-id="2b1f9-132">Později, uděláme změny kódu, který bude pomocí tohoto argumentu.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   <span data-ttu-id="2b1f9-133">[`dotnet restore`](../tools/dotnet-restore.md) volání do [NuGet](https://www.nuget.org/) (.NET Správce balíčků) Chcete-li obnovit strom závislostí.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-133">[`dotnet restore`](../tools/dotnet-restore.md) calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="2b1f9-134">Analyzuje NuGet *Hello.csproj* soubor, soubory ke stažení závislosti uvedené v souboru (nebo získá z mezipaměti na svém počítači) a zapíše *obj/project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-134">NuGet analyzes the *Hello.csproj* file, downloads the dependencies stated in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file.</span></span>  <span data-ttu-id="2b1f9-135">*Project.assets.json* soubor je potřeba mít možnost kompilace a spuštění.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-135">The *project.assets.json* file is necessary to be able to compile and run.</span></span>

   <span data-ttu-id="2b1f9-136">*Project.assets.json* soubor je trvalý a kompletní sadu grafu závislostí NuGet a další informace, které popisují aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-136">The *project.assets.json* file is a persisted and complete set of the graph of NuGet dependencies and other information describing an app.</span></span>  <span data-ttu-id="2b1f9-137">Tento soubor je pro čtení pomocí jiných nástrojů, jako například [ `dotnet build` ](../tools/dotnet-build.md) a [ `dotnet run` ](../tools/dotnet-run.md), povolení k procesu zdrojový kód se správnou sadou závislostí NuGet a vazby řešení.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-137">This file is read by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), enabling them to process the source code with a correct set of NuGet dependencies and binding resolutions.</span></span>

3. `$ dotnet run`

   <span data-ttu-id="2b1f9-138">[`dotnet run`](../tools/dotnet-run.md) volání [ `dotnet build` ](../tools/dotnet-build.md) zajistit, aby se sestavily cíle sestavení a poté zavolá `dotnet <assembly.dll>` spustit cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-138">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```console
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="2b1f9-139">Alternativně můžete také spustit [ `dotnet build` ](../tools/dotnet-build.md) pro kompilaci kódu bez nutnosti spuštění sestavení konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-139">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="2b1f9-140">Výsledkem je kompilovanou aplikaci jako soubor DLL, který můžete spustit s `dotnet bin\Debug\netcoreapp1.0\Hello.dll` na Windows (použijte `/` systémů než Windows).</span><span class="sxs-lookup"><span data-stu-id="2b1f9-140">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp1.0\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="2b1f9-141">Argumenty do aplikace můžete také zadat jak uvidíte později v tématu.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-141">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```console
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="2b1f9-142">Což je pokročilý scénář je možné vytvořit aplikace jako samostatná sada souborů specifické pro platformu, které je možné nasadit a spustit na počítači, který nemusí nainstalovat .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-142">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="2b1f9-143">Zobrazit [nasazení aplikace .NET Core](../deploying/index.md) podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-143">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="2b1f9-144">Rozšíření programu</span><span class="sxs-lookup"><span data-stu-id="2b1f9-144">Augmenting the program</span></span>

<span data-ttu-id="2b1f9-145">Pojďme trochu změnit program.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-145">Let's change the program a bit.</span></span> <span data-ttu-id="2b1f9-146">Čísla Fibonacciho Zábava, přidejme tedy, že kromě použijte argument pozdravili uživatele spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-146">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="2b1f9-147">Nahraďte obsah vaší *Program.cs* souboru následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="2b1f9-147">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. <span data-ttu-id="2b1f9-148">Spustit [ `dotnet build` ](../tools/dotnet-build.md) pro kompilaci změn.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-148">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="2b1f9-149">Spusťte program předávání parametru do aplikace:</span><span class="sxs-lookup"><span data-stu-id="2b1f9-149">Run the program passing a parameter to the app:</span></span>

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

<span data-ttu-id="2b1f9-150">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="2b1f9-150">And that's it!</span></span>  <span data-ttu-id="2b1f9-151">Můžete rozšířit `Program.cs` jakkoli chcete.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-151">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="2b1f9-152">Práce s více soubory</span><span class="sxs-lookup"><span data-stu-id="2b1f9-152">Working with multiple files</span></span>

<span data-ttu-id="2b1f9-153">Jednotlivé soubory, které se dají pro jednoduché jednorázové programy, ale využijete při vytváření složitějších aplikací, budete pravděpodobně to můžeme mít více zdrojové soubory projektu pro sestavení z předchozího příkladu Fibonacciho ukládáním hodnoty Fibonacciho a přidat některé rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-153">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

1. <span data-ttu-id="2b1f9-154">Přidat nový soubor *Hello* adresář s názvem *FibonacciGenerator.cs* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="2b1f9-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. <span data-ttu-id="2b1f9-155">Změnit `Main` metoda ve vaší *Program.cs* soubor k vytvoření nové instance třídy a volání metody jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2b1f9-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="2b1f9-156">Spustit [ `dotnet build` ](../tools/dotnet-build.md) pro kompilaci změn.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="2b1f9-157">Spusťte aplikaci spuštěním [ `dotnet run` ](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="2b1f9-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="2b1f9-158">Následuje ukázka výstupu programu:</span><span class="sxs-lookup"><span data-stu-id="2b1f9-158">The following shows the program output:</span></span>

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

<span data-ttu-id="2b1f9-159">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="2b1f9-159">And that's it!</span></span> <span data-ttu-id="2b1f9-160">Teď můžete začít používat základní koncepty se tady naučili vytvořit své vlastní programy.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-160">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

<span data-ttu-id="2b1f9-161">Všimněte si, že příkazy a postupy v tomto kurzu ke spuštění aplikace se používají pouze během vývoje.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-161">Note that the commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="2b1f9-162">Jakmile budete připraveni k nasazení své aplikace, budete chtít podívat na různé [strategie nasazení](../deploying/index.md) pro aplikace .NET Core a [ `dotnet publish` ](../tools/dotnet-publish.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="2b1f9-162">Once you're ready to deploy your app, you'll want to take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b1f9-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b1f9-163">See also</span></span>

* [<span data-ttu-id="2b1f9-164">Uspořádání a testování projektů pomocí nástroje příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="2b1f9-164">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
