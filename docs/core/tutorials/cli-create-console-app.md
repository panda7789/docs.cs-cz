---
title: Začínáme s .NET Core s využitím rozhraní příkazového řádku .NET Core CLI
description: Podrobný kurz ukazující, jak začít s .NET Core v systému Windows, Linux nebo macOS pomocí rozhraní příkazového řádku (CLI) .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 4285ed3c0488ea615ca89b0b771bf09c8c29b318
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739124"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="a1e4b-103">Začínáme s .NET Core v systému Windows, Linux nebo macOS pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a1e4b-103">Get started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="a1e4b-104">V tomto článku se dozvíte, jak na svém počítači začít vyvíjet aplikace pro různé platformy pomocí nástrojů pro .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-104">This article will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="a1e4b-105">Pokud nejste obeznámeni se sadou nástrojů .NET Core CLI, přečtěte si [přehled .NET Core SDK](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1e4b-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a1e4b-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1e4b-106">Prerequisites</span></span>

- <span data-ttu-id="a1e4b-107">[.NET Core SDK 3,1](https://dotnet.microsoft.com/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="a1e4b-108">Textový editor nebo Editor kódu dle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="a1e4b-109">Hello, konzolová aplikace!</span><span class="sxs-lookup"><span data-stu-id="a1e4b-109">Hello, Console App!</span></span>

<span data-ttu-id="a1e4b-110">[Vzorový kód můžete zobrazit nebo stáhnout](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z úložiště GitHub/Samples GitHub.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="a1e4b-111">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="a1e4b-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="a1e4b-112">Otevřete příkazový řádek a vytvořte složku s názvem *Hello*.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="a1e4b-113">Přejděte do složky, kterou jste vytvořili, a zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="a1e4b-113">Navigate to the folder you created and type the following:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="a1e4b-114">Podívejme se na stručný návod:</span><span class="sxs-lookup"><span data-stu-id="a1e4b-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="a1e4b-115">[dotnet New](../tools/dotnet-new.md) vytvoří aktuální soubor projektu *Hello. csproj* se závislostmi nezbytnými k vytvoření konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="a1e4b-116">Vytvoří také základní soubor *program.cs*, který obsahuje vstupní bod pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>
    
    <span data-ttu-id="a1e4b-117">*Hello. csproj*:</span><span class="sxs-lookup"><span data-stu-id="a1e4b-117">*Hello.csproj*:</span></span>
    
    [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]
    
    <span data-ttu-id="a1e4b-118">Soubor projektu určuje vše potřebné k obnovení závislostí a sestavování programu.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>
    
    - <span data-ttu-id="a1e4b-119">Element `<OutputType>` určuje, že vytváříme spustitelný soubor, a to i v jiných slovech konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="a1e4b-120">Element `<TargetFramework>` určuje, jakou implementaci .NET cílíme.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="a1e4b-121">V pokročilém scénáři můžete zadat více cílových rozhraní a sestavit je pro všechny v rámci jedné operace.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="a1e4b-122">V tomto kurzu se podíváme na vytváření jenom pro .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>
    
    <span data-ttu-id="a1e4b-123">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="a1e4b-123">*Program.cs*:</span></span>
    
    [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]
    
    <span data-ttu-id="a1e4b-124">Program se spustí `using System`, což znamená "přenést vše do oboru názvů `System` do rozsahu pro tento soubor".</span><span class="sxs-lookup"><span data-stu-id="a1e4b-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="a1e4b-125">Obor názvů `System` obsahuje třídu `Console`.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-125">The `System` namespace includes the `Console` class.</span></span>
    
    <span data-ttu-id="a1e4b-126">Pak definujeme obor názvů s názvem `Hello`.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="a1e4b-127">Můžete to změnit na cokoli, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-127">You can change this to anything you want.</span></span> <span data-ttu-id="a1e4b-128">Třída s názvem `Program` je definována v rámci tohoto oboru názvů s metodou `Main`, která přebírá pole řetězců s názvem `args`.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="a1e4b-129">Toto pole obsahuje seznam argumentů předaných při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="a1e4b-130">V takovém případě se toto pole nepoužívá a program jednoduše zapisuje text "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="a1e4b-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="a1e4b-131">do konzoly.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-131">to the console.</span></span> <span data-ttu-id="a1e4b-132">Později provedeme změny kódu, který tento argument využije.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-132">Later, we'll make changes to the code that will make use of this argument.</span></span>
    
    <span data-ttu-id="a1e4b-133">`dotnet new` volá implicitně [dotnet Restore](../tools/dotnet-restore.md) .</span><span class="sxs-lookup"><span data-stu-id="a1e4b-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="a1e4b-134">`dotnet restore` volání [NuGet](https://www.nuget.org/) (Správce balíčků .NET) pro obnovení stromu závislostí.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="a1e4b-135">NuGet analyzuje soubor *Hello. csproj* , stáhne závislosti definované v souboru (nebo je z mezipaměti v počítači převede) a zapíše soubor *obj/Project. assets. JSON* , který je nezbytný pro zkompilování a spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="a1e4b-136">[dotnet spustit](../tools/dotnet-run.md) volá [sestavení dotnet](../tools/dotnet-build.md) , aby bylo zajištěno, že cíle sestavení byly sestaveny, a poté volá `dotnet <assembly.dll>` pro spuštění cílové aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>
    
    ```console
    dotnet run

    Hello World!
    ```
    
    <span data-ttu-id="a1e4b-137">Alternativně můžete také spustit `dotnet build` pro zkompilování kódu bez spuštění konzolových aplikací sestavení.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-137">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="a1e4b-138">Výsledkem je kompilovaná aplikace, jako soubor DLL, na základě názvu projektu.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-138">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="a1e4b-139">V tomto případě se vytvoří soubor s názvem *Hello. dll*.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-139">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="a1e4b-140">Tuto aplikaci můžete spustit s `dotnet bin\Debug\netcoreapp3.1\Hello.dll` ve Windows (použijte `/` pro systémy jiné než Windows).</span><span class="sxs-lookup"><span data-stu-id="a1e4b-140">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>
    
    ```console
    dotnet bin\Debug\netcoreapp3.1\Hello.dll

    Hello World!
    ```
    
    <span data-ttu-id="a1e4b-141">Když je aplikace zkompilována, byl společně s `Hello.dll`vytvořen spustitelný soubor specifický pro operační systém.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-141">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="a1e4b-142">V systému Windows to bude `Hello.exe`. v systému Linux nebo macOS by to bylo `hello`.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-142">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="a1e4b-143">S výše uvedeným příkladem je soubor pojmenován pomocí `Hello.exe` nebo `Hello`.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-143">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="a1e4b-144">Tento spustitelný soubor můžete spustit přímo.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-144">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="a1e4b-145">Úprava programu</span><span class="sxs-lookup"><span data-stu-id="a1e4b-145">Modify the program</span></span>

<span data-ttu-id="a1e4b-146">Pojďme program trochu změnit.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-146">Let's change the program a bit.</span></span> <span data-ttu-id="a1e4b-147">Fibonacci čísla jsou zábavné, takže je přidáváme a také k použití argumentu pro přání uživatele, který aplikaci spouští.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-147">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="a1e4b-148">Obsah souboru *program.cs* nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="a1e4b-148">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/core/console-apps/fibonacci-msbuild/Program.cs)]

02. <span data-ttu-id="a1e4b-149">Spusťte [sestavení dotnet](../tools/dotnet-build.md) pro zkompilování změn.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-149">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="a1e4b-150">Spusťte program předáním parametru do aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-150">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="a1e4b-151">Když použijete příkaz `dotnet` ke spuštění aplikace, přidejte `--` na konec.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-151">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="a1e4b-152">Cokoli napravo od `--` bude do aplikace předán jako parametr.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-152">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="a1e4b-153">V následujícím příkladu je hodnota `John` předána do aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-153">In the following example, the value `John` is passed to the app.</span></span>

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

<span data-ttu-id="a1e4b-154">A je to!</span><span class="sxs-lookup"><span data-stu-id="a1e4b-154">And that's it!</span></span> <span data-ttu-id="a1e4b-155">*Program.cs* můžete upravit jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-155">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="a1e4b-156">Práce s více soubory</span><span class="sxs-lookup"><span data-stu-id="a1e4b-156">Working with multiple files</span></span>

<span data-ttu-id="a1e4b-157">Jednotlivé soubory jsou pro jednoduché jednorázové programy přesné, ale pokud sestavíte komplexnější aplikaci, pravděpodobně budete mít v projektu více souborů kódu.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-157">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="a1e4b-158">Pojďme si vytvořit z předchozího příkladu Fibonacci ukládáním do mezipaměti některé hodnoty Fibonacci a přidat některé rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-158">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="a1e4b-159">Přidejte nový soubor do adresáře *Hello* s názvem *FibonacciGenerator.cs* s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="a1e4b-159">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

02. <span data-ttu-id="a1e4b-160">Změňte metodu `Main` v souboru *program.cs* pro vytvoření instance nové třídy a zavolejte její metodu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a1e4b-160">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

03. <span data-ttu-id="a1e4b-161">Spusťte [sestavení dotnet](../tools/dotnet-build.md) pro zkompilování změn.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-161">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="a1e4b-162">Spusťte aplikaci spuštěním příkazu [dotnet](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="a1e4b-162">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span> <span data-ttu-id="a1e4b-163">Následující příklad ukazuje výstup programu:</span><span class="sxs-lookup"><span data-stu-id="a1e4b-163">The following shows the program output:</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="a1e4b-164">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="a1e4b-164">Publish your app</span></span>

<span data-ttu-id="a1e4b-165">Až budete připraveni k distribuci vaší aplikace, pomocí příkazu [dotnet Publish](../tools/dotnet-publish.md) vygenerujte složku pro _publikování_ v _přihrádce\\ladění\\netcoreapp 3.1\\publikovat\\_ (použijte `/` pro systémy jiné než Windows).</span><span class="sxs-lookup"><span data-stu-id="a1e4b-165">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="a1e4b-166">Obsah složky pro _publikování_ můžete distribuovat na jiné platformy, pokud už máte nainstalovanou modul dotnet runtime.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-166">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```console
dotnet publish
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="a1e4b-167">Výše uvedený výstup se může lišit v závislosti na vaší aktuální složce a operačním systému, výstup by měl být podobný.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-167">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="a1e4b-168">Publikovanou aplikaci můžete spustit pomocí příkazu [dotnet](../tools/dotnet.md) :</span><span class="sxs-lookup"><span data-stu-id="a1e4b-168">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```console
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll

Hello World!
```

<span data-ttu-id="a1e4b-169">Jak je uvedeno na začátku tohoto článku, byl společně s `Hello.dll`vytvořen spustitelný soubor specifický pro operační systém.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-169">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="a1e4b-170">V systému Windows to bude `Hello.exe`. v systému Linux nebo macOS by to bylo `hello`.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-170">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="a1e4b-171">S výše uvedeným příkladem je soubor pojmenován pomocí `Hello.exe` nebo `Hello`.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-171">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="a1e4b-172">Tento publikovaný spustitelný soubor můžete spustit přímo.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-172">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="a1e4b-173">Závěr</span><span class="sxs-lookup"><span data-stu-id="a1e4b-173">Conclusion</span></span>

<span data-ttu-id="a1e4b-174">A je to!</span><span class="sxs-lookup"><span data-stu-id="a1e4b-174">And that's it!</span></span> <span data-ttu-id="a1e4b-175">Teď můžete začít používat základní koncepty, které jste zde zjistili, k vytvoření vlastních programů.</span><span class="sxs-lookup"><span data-stu-id="a1e4b-175">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1e4b-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1e4b-176">See also</span></span>

- [<span data-ttu-id="a1e4b-177">Organizování a testování projektů pomocí .NET Core CLIch nástrojů</span><span class="sxs-lookup"><span data-stu-id="a1e4b-177">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
- [<span data-ttu-id="a1e4b-178">Publikování aplikací .NET Core pomocí rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a1e4b-178">Publish .NET Core apps with the CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="a1e4b-179">Další informace o nasazení aplikace</span><span class="sxs-lookup"><span data-stu-id="a1e4b-179">Learn more about app deployment</span></span>](../deploying/index.md)
