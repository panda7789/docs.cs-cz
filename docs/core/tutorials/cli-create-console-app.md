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
# <a name="get-started-with-net-core-using-the-net-core-cli"></a><span data-ttu-id="d9674-103">Začínáme s rozhraním .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="d9674-103">Get started with .NET Core using the .NET Core CLI</span></span>

<span data-ttu-id="d9674-104">Tento článek vám ukáže, jak začít vyvíjet aplikace .NET Core, které fungují ve Windows, Linuxu a macOS pomocí rozhraní .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="d9674-104">This article will show you how to start developing .NET Core apps that work on Windows, Linux, and macOS using the .NET Core CLI.</span></span>

<span data-ttu-id="d9674-105">Pokud nejste obeznámeni s rozhraním .NET Core CLI, podívejte se na [přehled rozhraní .NET Core CLI](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9674-105">If you're unfamiliar with the .NET Core CLI, see the [.NET Core CLI overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d9674-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9674-106">Prerequisites</span></span>

- <span data-ttu-id="d9674-107">[Sada .NET Core SDK 3.1](https://dotnet.microsoft.com/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="d9674-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="d9674-108">Textový editor nebo editor kódu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="d9674-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="d9674-109">Dobrý den, konzole App!</span><span class="sxs-lookup"><span data-stu-id="d9674-109">Hello, Console App!</span></span>

<span data-ttu-id="d9674-110">[Ukázkový kód](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) můžete zobrazit nebo stáhnout z úložiště GitHub dotnet/samples.</span><span class="sxs-lookup"><span data-stu-id="d9674-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="d9674-111">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d9674-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="d9674-112">Otevřete příkazový řádek a vytvořte složku s názvem *Hello*.</span><span class="sxs-lookup"><span data-stu-id="d9674-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="d9674-113">Přejděte do složky, kterou jste vytvořili, a zadejte následující.</span><span class="sxs-lookup"><span data-stu-id="d9674-113">Navigate to the folder you created and type the following.</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="d9674-114">Udělejme rychlý návod:</span><span class="sxs-lookup"><span data-stu-id="d9674-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="d9674-115">[dotnet new](../tools/dotnet-new.md) vytvoří aktuální soubor projektu *Hello.csproj* se závislostmi potřebnými k vytvoření konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9674-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="d9674-116">Vytvoří také *Program.cs*, základní soubor obsahující vstupní bod pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d9674-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>

    <span data-ttu-id="d9674-117">*Hello.csproj*:</span><span class="sxs-lookup"><span data-stu-id="d9674-117">*Hello.csproj*:</span></span>

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    <span data-ttu-id="d9674-118">Soubor projektu určuje vše, co je potřeba k obnovení závislostí a sestavení programu.</span><span class="sxs-lookup"><span data-stu-id="d9674-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

    - <span data-ttu-id="d9674-119">Prvek `<OutputType>` určuje, že vytváříme spustitelný soubor, jinými slovy konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d9674-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="d9674-120">Prvek `<TargetFramework>` určuje, na jakou implementaci rozhraní .NET cílíme.</span><span class="sxs-lookup"><span data-stu-id="d9674-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="d9674-121">V rozšířeném scénáři můžete zadat více cílových architektur a sestavit pro všechny v jedné operaci.</span><span class="sxs-lookup"><span data-stu-id="d9674-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="d9674-122">V tomto kurzu se budeme držet vytváření pouze pro rozhraní .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="d9674-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>

    <span data-ttu-id="d9674-123">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="d9674-123">*Program.cs*:</span></span>

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    <span data-ttu-id="d9674-124">Program začíná `using System`, což znamená "přenést `System` vše v oboru názvů do oboru pro tento soubor".</span><span class="sxs-lookup"><span data-stu-id="d9674-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="d9674-125">Obor `System` názvů obsahuje `Console` třídu.</span><span class="sxs-lookup"><span data-stu-id="d9674-125">The `System` namespace includes the `Console` class.</span></span>

    <span data-ttu-id="d9674-126">Poté definujeme obor `Hello`názvů s názvem .</span><span class="sxs-lookup"><span data-stu-id="d9674-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="d9674-127">Můžete to změnit na cokoliv chcete.</span><span class="sxs-lookup"><span data-stu-id="d9674-127">You can change this to anything you want.</span></span> <span data-ttu-id="d9674-128">Třída s `Program` názvem je definována v `Main` tomto oboru názvů s `args`metodou, která přebírá pole řetězců s názvem .</span><span class="sxs-lookup"><span data-stu-id="d9674-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="d9674-129">Toto pole obsahuje seznam argumentů předaných při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="d9674-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="d9674-130">Jak to je, toto pole se nepoužívá a program jednoduše zapíše text "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="d9674-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="d9674-131">„Hello, World!“.</span><span class="sxs-lookup"><span data-stu-id="d9674-131">to the console.</span></span> <span data-ttu-id="d9674-132">Později provedeme změny kódu, který bude používat tento argument.</span><span class="sxs-lookup"><span data-stu-id="d9674-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

    <span data-ttu-id="d9674-133">`dotnet new`volání [dotnet obnovit](../tools/dotnet-restore.md) implicitně.</span><span class="sxs-lookup"><span data-stu-id="d9674-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="d9674-134">`dotnet restore`volá do [NuGet](https://www.nuget.org/) (správce balíčků.NET) k obnovení stromu závislostí.</span><span class="sxs-lookup"><span data-stu-id="d9674-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="d9674-135">NuGet analyzuje soubor *Hello.csproj,* stáhne závislosti definované v souboru (nebo je uchopí z mezipaměti v počítači) a zapíše soubor *obj/project.assets.json,* který je nezbytný pro kompilaci a spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="d9674-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="d9674-136">[dotnet spustit](../tools/dotnet-run.md) volání [dotnet sestavení](../tools/dotnet-build.md) zajistit, že cíle sestavení `dotnet <assembly.dll>` byly vytvořeny a potom volání ke spuštění cílové aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9674-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="d9674-137">Získáte následující výstup.</span><span class="sxs-lookup"><span data-stu-id="d9674-137">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="d9674-138">Alternativně můžete také `dotnet build` spustit ke kompilaci kódu bez spuštění aplikací konzoly sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9674-138">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="d9674-139">Výsledkem je zkompilovaná aplikace jako soubor DLL na základě názvu projektu.</span><span class="sxs-lookup"><span data-stu-id="d9674-139">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="d9674-140">V tomto případě se vytvořený soubor nazývá *Hello.dll*.</span><span class="sxs-lookup"><span data-stu-id="d9674-140">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="d9674-141">Tato aplikace může `dotnet bin\Debug\netcoreapp3.1\Hello.dll` být spuštěna `/` v systému Windows (použití pro systémy, které nejsou systémy Windows).</span><span class="sxs-lookup"><span data-stu-id="d9674-141">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    <span data-ttu-id="d9674-142">Získáte následující výstup.</span><span class="sxs-lookup"><span data-stu-id="d9674-142">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="d9674-143">Při kompilaci aplikace byl vytvořen spustitelný soubor specifický pro `Hello.dll`operační systém spolu s souborem .</span><span class="sxs-lookup"><span data-stu-id="d9674-143">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="d9674-144">V systému Windows `Hello.exe`by to bylo ; na Linuxu nebo macOS, to by bylo `hello`.</span><span class="sxs-lookup"><span data-stu-id="d9674-144">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="d9674-145">S výše uvedeným příkladem je `Hello.exe` soubor `Hello`pojmenován s nebo .</span><span class="sxs-lookup"><span data-stu-id="d9674-145">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="d9674-146">Tento spustitelný soubor můžete spustit přímo.</span><span class="sxs-lookup"><span data-stu-id="d9674-146">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="d9674-147">Úprava programu</span><span class="sxs-lookup"><span data-stu-id="d9674-147">Modify the program</span></span>

<span data-ttu-id="d9674-148">Pojďme trochu změnit program.</span><span class="sxs-lookup"><span data-stu-id="d9674-148">Let's change the program a bit.</span></span> <span data-ttu-id="d9674-149">Fibonaccičísla jsou zábavné, takže přidejme, že a také použít argument pozdravit osobu, která provozuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d9674-149">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="d9674-150">Nahraďte obsah *Program.cs* souboru následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d9674-150">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. <span data-ttu-id="d9674-151">Spusťte [sestavení dotnet](../tools/dotnet-build.md) a zkompilujte změny.</span><span class="sxs-lookup"><span data-stu-id="d9674-151">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="d9674-152">Spusťte program předání parametru do aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9674-152">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="d9674-153">Když pomocí `dotnet` příkazu spustíte aplikaci, přidejte `--` ji na konec.</span><span class="sxs-lookup"><span data-stu-id="d9674-153">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="d9674-154">Cokoli vpravo `--` od bude předáno jako parametr do aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9674-154">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="d9674-155">V následujícím příkladu `John` je hodnota předána aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d9674-155">In the following example, the value `John` is passed to the app.</span></span>

    ```dotnetcli
    dotnet run -- John
    ```

    <span data-ttu-id="d9674-156">Získáte následující výstup.</span><span class="sxs-lookup"><span data-stu-id="d9674-156">You get the following output.</span></span>

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

<span data-ttu-id="d9674-157">A to je vše!</span><span class="sxs-lookup"><span data-stu-id="d9674-157">And that's it!</span></span> <span data-ttu-id="d9674-158">Můžete *Program.cs* libovolně upravovat.</span><span class="sxs-lookup"><span data-stu-id="d9674-158">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="d9674-159">Práce s více soubory</span><span class="sxs-lookup"><span data-stu-id="d9674-159">Working with multiple files</span></span>

<span data-ttu-id="d9674-160">Jednotlivé soubory jsou v pořádku pro jednoduché jednorázové programy, ale pokud vytváříte složitější aplikaci, pravděpodobně budete mít v projektu více souborů kódu.</span><span class="sxs-lookup"><span data-stu-id="d9674-160">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="d9674-161">Pojďme sestavit z předchozího příkladu Fibonacciho ukládáním některých hodnot Fibonacciho do mezipaměti a přidáním některých rekurzivních funkcí.</span><span class="sxs-lookup"><span data-stu-id="d9674-161">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="d9674-162">Přidejte nový soubor do adresáře *Hello* s názvem *FibonacciGenerator.cs* s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d9674-162">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. <span data-ttu-id="d9674-163">Změňte `Main` metodu v *souboru Program.cs* k vytvoření instance nové třídy a volání její metody jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d9674-163">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. <span data-ttu-id="d9674-164">Spusťte [sestavení dotnet](../tools/dotnet-build.md) a zkompilujte změny.</span><span class="sxs-lookup"><span data-stu-id="d9674-164">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="d9674-165">Spusťte aplikaci spuštěním [dotnet run](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="d9674-165">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="d9674-166">Získáte následující výstup.</span><span class="sxs-lookup"><span data-stu-id="d9674-166">You get the following output.</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="d9674-167">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="d9674-167">Publish your app</span></span>

<span data-ttu-id="d9674-168">Jakmile budete připraveni distribuovat aplikaci, použijte příkaz [dotnet publish](../tools/dotnet-publish.md) ke generování složky _publikování_ při _publikování\\\\\\\\ ladění aplikace netcoreapp3.1_ (používá se `/` pro systémy, které nejsou systémy Windows).</span><span class="sxs-lookup"><span data-stu-id="d9674-168">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="d9674-169">Obsah složky _publikování_ můžete distribuovat na jiné platformy, pokud již nainstalovali dotnet runtime.</span><span class="sxs-lookup"><span data-stu-id="d9674-169">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```dotnetcli
dotnet publish
```

<span data-ttu-id="d9674-170">Získáte výstup podobný následující.</span><span class="sxs-lookup"><span data-stu-id="d9674-170">You get output similar to the following.</span></span>

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="d9674-171">Výše uvedený výstup se může lišit v závislosti na aktuální složce a operačním systému, ale výstup by měl být podobný.</span><span class="sxs-lookup"><span data-stu-id="d9674-171">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="d9674-172">Publikovanou aplikaci můžete spustit pomocí příkazu [dotnet:](../tools/dotnet.md)</span><span class="sxs-lookup"><span data-stu-id="d9674-172">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

<span data-ttu-id="d9674-173">Získáte následující výstup.</span><span class="sxs-lookup"><span data-stu-id="d9674-173">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="d9674-174">Jak již bylo zmíněno na začátku tohoto článku, byl vytvořen `Hello.dll`spustitelný soubor specifický pro operační systém spolu s souborem .</span><span class="sxs-lookup"><span data-stu-id="d9674-174">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="d9674-175">V systému Windows `Hello.exe`by to bylo ; na Linuxu nebo macOS, to by bylo `hello`.</span><span class="sxs-lookup"><span data-stu-id="d9674-175">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="d9674-176">S výše uvedeným příkladem je `Hello.exe` soubor `Hello`pojmenován s nebo .</span><span class="sxs-lookup"><span data-stu-id="d9674-176">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="d9674-177">Tento publikovaný spustitelný soubor můžete spustit přímo.</span><span class="sxs-lookup"><span data-stu-id="d9674-177">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="d9674-178">Závěr</span><span class="sxs-lookup"><span data-stu-id="d9674-178">Conclusion</span></span>

<span data-ttu-id="d9674-179">A to je vše!</span><span class="sxs-lookup"><span data-stu-id="d9674-179">And that's it!</span></span> <span data-ttu-id="d9674-180">Nyní můžete začít používat základní koncepty zde naučil vytvořit si vlastní programy.</span><span class="sxs-lookup"><span data-stu-id="d9674-180">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9674-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9674-181">See also</span></span>

- [<span data-ttu-id="d9674-182">Uspořádání a testování projektů pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="d9674-182">Organizing and testing projects with the .NET Core CLI</span></span>](testing-with-cli.md)
- [<span data-ttu-id="d9674-183">Publikování aplikací .NET Core pomocí rozhraní CLI jádra ROZHRANÍ .NET</span><span class="sxs-lookup"><span data-stu-id="d9674-183">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="d9674-184">Nasazení aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="d9674-184">.NET Core application deployment</span></span>](../deploying/index.md)
