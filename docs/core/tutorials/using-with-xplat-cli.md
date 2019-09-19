---
title: Začínáme s .NET Core s využitím rozhraní příkazového řádku
description: Podrobný kurz ukazující, jak začít s .NET Core v systému Windows, Linux nebo macOS pomocí rozhraní příkazového řádku (CLI) .NET Core.
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: b5ef70967c8404dc5ce5b816bb9a1c3b1d7e4230
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117346"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="93606-103">Začínáme s .NET Core v systému Windows, Linux nebo macOS pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="93606-103">Get started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="93606-104">V tomto tématu se dozvíte, jak na svém počítači začít vyvíjet aplikace pro různé platformy pomocí nástrojů pro .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="93606-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="93606-105">Pokud nejste obeznámeni se sadou nástrojů .NET Core CLI, přečtěte si [přehled .NET Core SDK](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="93606-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="93606-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93606-106">Prerequisites</span></span>

- <span data-ttu-id="93606-107">[.NET Core SDK 2,1](https://dotnet.microsoft.com/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="93606-107">[.NET Core SDK 2.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="93606-108">Textový editor nebo Editor kódu dle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="93606-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="93606-109">Hello, konzolová aplikace!</span><span class="sxs-lookup"><span data-stu-id="93606-109">Hello, Console App!</span></span>

<span data-ttu-id="93606-110">[Vzorový kód můžete zobrazit nebo stáhnout](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z úložiště GitHub/Samples GitHub.</span><span class="sxs-lookup"><span data-stu-id="93606-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="93606-111">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="93606-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="93606-112">Otevřete příkazový řádek a vytvořte složku s názvem *Hello*.</span><span class="sxs-lookup"><span data-stu-id="93606-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="93606-113">Přejděte do složky, kterou jste vytvořili, a zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="93606-113">Navigate to the folder you created and type the following:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="93606-114">Podívejme se na stručný návod:</span><span class="sxs-lookup"><span data-stu-id="93606-114">Let's do a quick walkthrough:</span></span>

1. `dotnet new console`

   <span data-ttu-id="93606-115">[`dotnet new`](../tools/dotnet-new.md)Vytvoří aktuální `Hello.csproj` soubor projektu se závislostmi nezbytnými k vytvoření konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="93606-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="93606-116">Vytvoří také základní soubor `Program.cs`, který obsahuje vstupní bod pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="93606-116">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="93606-117">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="93606-117">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   <span data-ttu-id="93606-118">Soubor projektu určuje vše potřebné k obnovení závislostí a sestavování programu.</span><span class="sxs-lookup"><span data-stu-id="93606-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   - <span data-ttu-id="93606-119">`OutputType` Značka určuje, že vytváříme spustitelný soubor, a to v jiných slovech konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="93606-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   - <span data-ttu-id="93606-120">`TargetFramework` Značka určuje, jakou implementaci .NET cílíme.</span><span class="sxs-lookup"><span data-stu-id="93606-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="93606-121">V pokročilém scénáři můžete zadat více cílových rozhraní a sestavit je pro všechny v rámci jedné operace.</span><span class="sxs-lookup"><span data-stu-id="93606-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="93606-122">V tomto kurzu se podíváme na vytváření jenom pro .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="93606-122">In this tutorial, we'll stick to building only for .NET Core 2.1.</span></span>

   <span data-ttu-id="93606-123">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="93606-123">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   <span data-ttu-id="93606-124">Program spustí `using System`, což znamená "přenést vše `System` do oboru názvů do rozsahu pro tento soubor".</span><span class="sxs-lookup"><span data-stu-id="93606-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="93606-125">Obor názvů zahrnuje základní konstrukce `string`, jako jsou nebo číselné typy. `System`</span><span class="sxs-lookup"><span data-stu-id="93606-125">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="93606-126">Pak definujeme obor názvů s `Hello`názvem.</span><span class="sxs-lookup"><span data-stu-id="93606-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="93606-127">Můžete to změnit na cokoli, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="93606-127">You can change this to anything you want.</span></span> <span data-ttu-id="93606-128">Třída s názvem `Program` je definována v rámci tohoto oboru názvů `Main` s metodou, která přijímá pole řetězců jako argument.</span><span class="sxs-lookup"><span data-stu-id="93606-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="93606-129">Toto pole obsahuje seznam argumentů předaných při volání zkompilovaného programu.</span><span class="sxs-lookup"><span data-stu-id="93606-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="93606-130">V takovém případě se toto pole nepoužívá: celý program provádí zápis "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="93606-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="93606-131">do konzoly.</span><span class="sxs-lookup"><span data-stu-id="93606-131">to the console.</span></span> <span data-ttu-id="93606-132">Později provedeme změny kódu, který tento argument využije.</span><span class="sxs-lookup"><span data-stu-id="93606-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   <span data-ttu-id="93606-133">`dotnet new`volání [`dotnet restore`](../tools/dotnet-restore.md) implicitně.</span><span class="sxs-lookup"><span data-stu-id="93606-133">`dotnet new` calls [`dotnet restore`](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="93606-134">`dotnet restore`volání [NuGet](https://www.nuget.org/) (Správce balíčků .NET) pro obnovení stromu závislostí.</span><span class="sxs-lookup"><span data-stu-id="93606-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="93606-135">NuGet analyzuje soubor *Hello. csproj* , stáhne závislosti definované v souboru (nebo je z mezipaměti v počítači převede) a zapíše soubor *obj/Project. assets. JSON* , který je nezbytný pro zkompilování a spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="93606-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="93606-136">Pokud používáte verzi sady SDK .NET Core 1. x, budete muset zavolat `dotnet restore` sami po volání. `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="93606-136">If you're using a .NET Core 1.x version of the SDK, you'll have to call `dotnet restore` yourself after calling `dotnet new`.</span></span>

2. `dotnet run`

   <span data-ttu-id="93606-137">[`dotnet run`](../tools/dotnet-run.md)volá [`dotnet build`](../tools/dotnet-build.md) , aby se zajistilo sestavení cílů sestavení, a pak volání `dotnet <assembly.dll>` pro spuštění cílové aplikace.</span><span class="sxs-lookup"><span data-stu-id="93606-137">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```console
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="93606-138">Alternativně můžete také provést [`dotnet build`](../tools/dotnet-build.md) kompilaci kódu bez spuštění konzolových aplikací sestavení.</span><span class="sxs-lookup"><span data-stu-id="93606-138">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="93606-139">Výsledkem je kompilovaná aplikace jako soubor DLL, který lze spustit v systému Windows ( `dotnet bin\Debug\netcoreapp2.1\Hello.dll` používá `/` se pro systémy jiné než Windows).</span><span class="sxs-lookup"><span data-stu-id="93606-139">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp2.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="93606-140">Můžete také zadat argumenty aplikace, jak uvidíte později v tématu.</span><span class="sxs-lookup"><span data-stu-id="93606-140">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="93606-141">V rámci pokročilého scénáře je možné aplikaci sestavit jako samostatnou sadu souborů specifických pro platformu, které je možné nasadit a spustit v počítači, který nutně nemá nainstalovaný .NET Core.</span><span class="sxs-lookup"><span data-stu-id="93606-141">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="93606-142">Podrobnosti najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="93606-142">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="93606-143">Rozšíření programu</span><span class="sxs-lookup"><span data-stu-id="93606-143">Augmenting the program</span></span>

<span data-ttu-id="93606-144">Pojďme program trochu změnit.</span><span class="sxs-lookup"><span data-stu-id="93606-144">Let's change the program a bit.</span></span> <span data-ttu-id="93606-145">Fibonacci čísla jsou zábavné, takže přidáváme kromě toho také použití argumentu k přání uživatele, který aplikaci spouští.</span><span class="sxs-lookup"><span data-stu-id="93606-145">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="93606-146">Obsah souboru *program.cs* nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="93606-146">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. <span data-ttu-id="93606-147">Spusťte [`dotnet build`](../tools/dotnet-build.md) pro zkompilování změn.</span><span class="sxs-lookup"><span data-stu-id="93606-147">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="93606-148">Spusťte program předáním parametru do aplikace:</span><span class="sxs-lookup"><span data-stu-id="93606-148">Run the program passing a parameter to the app:</span></span>

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

<span data-ttu-id="93606-149">A je to!</span><span class="sxs-lookup"><span data-stu-id="93606-149">And that's it!</span></span>  <span data-ttu-id="93606-150">Můžete rozšířit `Program.cs` libovolný způsob, jakým chcete.</span><span class="sxs-lookup"><span data-stu-id="93606-150">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="93606-151">Práce s více soubory</span><span class="sxs-lookup"><span data-stu-id="93606-151">Working with multiple files</span></span>

<span data-ttu-id="93606-152">Jednotlivé soubory jsou pro jednoduché jednorázové programy přesné, ale pokud sestavíte komplexnější aplikaci, pravděpodobně budete mít v projektu více zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="93606-152">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project.</span></span>
<span data-ttu-id="93606-153">Pojďme si vytvořit z předchozího příkladu Fibonacci ukládáním do mezipaměti některé hodnoty Fibonacci a přidat některé rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="93606-153">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

1. <span data-ttu-id="93606-154">Přidejte nový soubor do adresáře *Hello* s názvem *FibonacciGenerator.cs* s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="93606-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. <span data-ttu-id="93606-155">Změňte metodu v souboru program.cs pro vytvoření instance nové třídy a zavolejte její metodu jako v následujícím příkladu: `Main`</span><span class="sxs-lookup"><span data-stu-id="93606-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="93606-156">Spusťte [`dotnet build`](../tools/dotnet-build.md) pro zkompilování změn.</span><span class="sxs-lookup"><span data-stu-id="93606-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="93606-157">Spusťte aplikaci spuštěním příkazu [`dotnet run`](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="93606-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="93606-158">Následující příklad ukazuje výstup programu:</span><span class="sxs-lookup"><span data-stu-id="93606-158">The following shows the program output:</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="93606-159">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="93606-159">Publish your app</span></span>

<span data-ttu-id="93606-160">Až budete připraveni k distribuci [`dotnet publish`](../tools/dotnet-publish.md) vaší aplikace, použijte příkaz pro vygenerování `/` _\\\\složky pro publikování v přihrádce netcoreapp 2.1\\publikovat\\_  (použijte pro systémy jiné než Windows).</span><span class="sxs-lookup"><span data-stu-id="93606-160">Once you're ready to distribute your app, use the [`dotnet publish`](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp2.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="93606-161">Obsah složky pro _publikování_ můžete distribuovat na jiné platformy, pokud už máte nainstalovanou modul dotnet runtime.</span><span class="sxs-lookup"><span data-stu-id="93606-161">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

<span data-ttu-id="93606-162">Publikovanou aplikaci můžete spustit pomocí příkazu [dotnet](../tools/dotnet.md) :</span><span class="sxs-lookup"><span data-stu-id="93606-162">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```console
$ dotnet bin\Debug\netcoreapp2.1\publish\Hello.dll
Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="93606-163">Závěr</span><span class="sxs-lookup"><span data-stu-id="93606-163">Conclusion</span></span>

<span data-ttu-id="93606-164">A je to!</span><span class="sxs-lookup"><span data-stu-id="93606-164">And that's it!</span></span> <span data-ttu-id="93606-165">Teď můžete začít používat základní koncepty, které jste zde zjistili, k vytvoření vlastních programů.</span><span class="sxs-lookup"><span data-stu-id="93606-165">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="93606-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93606-166">See also</span></span>

- [<span data-ttu-id="93606-167">Organizování a testování projektů pomocí .NET Core CLIch nástrojů</span><span class="sxs-lookup"><span data-stu-id="93606-167">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
- [<span data-ttu-id="93606-168">Publikování aplikací .NET Core pomocí rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="93606-168">Publish .NET Core apps with the CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="93606-169">Další informace o nasazení aplikace</span><span class="sxs-lookup"><span data-stu-id="93606-169">Learn more about app deployment</span></span>](../deploying/index.md)
