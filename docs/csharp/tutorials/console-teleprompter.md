---
title: Konzolová aplikace
description: V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#.
keywords: Rozhraní .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: cc8645f9eef070d800627ea1c47cf7de1e877783
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="console-application"></a><span data-ttu-id="0372a-104">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="0372a-104">Console Application</span></span>

## <a name="introduction"></a><span data-ttu-id="0372a-105">Úvod</span><span class="sxs-lookup"><span data-stu-id="0372a-105">Introduction</span></span>
<span data-ttu-id="0372a-106">V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="0372a-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="0372a-107">Naučíte:</span><span class="sxs-lookup"><span data-stu-id="0372a-107">You’ll learn:</span></span>
*   <span data-ttu-id="0372a-108">Základy .NET Core rozhraní příkazového řádku (CLI)</span><span class="sxs-lookup"><span data-stu-id="0372a-108">The basics of the .NET Core Command Line Interface (CLI)</span></span>
*   <span data-ttu-id="0372a-109">Struktura konzolovou aplikaci C#</span><span class="sxs-lookup"><span data-stu-id="0372a-109">The structure of a C# Console Application</span></span>
*   <span data-ttu-id="0372a-110">Konzole vstupně-výstupních operací</span><span class="sxs-lookup"><span data-stu-id="0372a-110">Console I/O</span></span>
*   <span data-ttu-id="0372a-111">Základní informace o rozhraní API pro vstupně-výstupní soubor v .NET Core</span><span class="sxs-lookup"><span data-stu-id="0372a-111">The basics of File I/O APIs in .NET Core</span></span>
*   <span data-ttu-id="0372a-112">Základy úloh asynchronní Model programování v .NET Core</span><span class="sxs-lookup"><span data-stu-id="0372a-112">The basics of the Task Asynchronous Programming Model in .NET Core</span></span>

<span data-ttu-id="0372a-113">Budete sestavit aplikaci, která čte textový soubor a vrátí je obsah na konzole tohoto textového souboru.</span><span class="sxs-lookup"><span data-stu-id="0372a-113">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="0372a-114">Výstup do konzoly bude paced tak, aby odpovídaly nahlas jeho čtení.</span><span class="sxs-lookup"><span data-stu-id="0372a-114">The output to the console will be paced to match reading it aloud.</span></span> <span data-ttu-id="0372a-115">Můžete urychlit nebo zpomalit rychlost stisknutím ' <' nebo ' >' klíče.</span><span class="sxs-lookup"><span data-stu-id="0372a-115">You can speed up or slow down the pace by pressing the ‘<’ or ‘>’ keys.</span></span>

<span data-ttu-id="0372a-116">V tomto kurzu je celá řada funkcí.</span><span class="sxs-lookup"><span data-stu-id="0372a-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="0372a-117">Umožňuje vytvořit, je po jednom.</span><span class="sxs-lookup"><span data-stu-id="0372a-117">Let’s build them one by one.</span></span> 
## <a name="prerequisites"></a><span data-ttu-id="0372a-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0372a-118">Prerequisites</span></span>
<span data-ttu-id="0372a-119">Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core.</span><span class="sxs-lookup"><span data-stu-id="0372a-119">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="0372a-120">Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="0372a-120">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="0372a-121">Tuto aplikaci můžete spustit v systému Windows, Linux, systému macOS nebo v kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="0372a-121">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="0372a-122">Budete muset nainstalovat editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="0372a-122">You’ll need to install your favorite code editor.</span></span> 
## <a name="create-the-application"></a><span data-ttu-id="0372a-123">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="0372a-123">Create the Application</span></span>
<span data-ttu-id="0372a-124">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="0372a-124">The first step is to create a new application.</span></span> <span data-ttu-id="0372a-125">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0372a-125">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="0372a-126">Nastavit aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="0372a-126">Make that the current directory.</span></span> <span data-ttu-id="0372a-127">Zadejte příkaz `dotnet new console` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="0372a-127">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="0372a-128">Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".</span><span class="sxs-lookup"><span data-stu-id="0372a-128">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="0372a-129">Než začnete, provádění změn, přejděte přes kroky a spusťte tak jednoduchou aplikaci Hello World.</span><span class="sxs-lookup"><span data-stu-id="0372a-129">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="0372a-130">Po vytvoření aplikace, zadejte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="0372a-130">After creating the application, type `dotnet restore` ([see note](#dotnet-restore-note)) at the command prompt.</span></span> <span data-ttu-id="0372a-131">Tento příkaz spustí proces obnovení balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="0372a-131">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="0372a-132">NuGet je Správce balíčků .NET.</span><span class="sxs-lookup"><span data-stu-id="0372a-132">NuGet is a .NET package manager.</span></span> <span data-ttu-id="0372a-133">Tento příkaz stáhne všechny chybějící závislosti pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="0372a-133">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="0372a-134">Toto je nový projekt, žádné závislosti na místě, se tak během prvního spuštění stáhnou rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0372a-134">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="0372a-135">Po provedení tohoto kroku počáteční se jenom musíte spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) při přidání nové závislé balíčky nebo aktualizace verze všechny svoje závislosti.</span><span class="sxs-lookup"><span data-stu-id="0372a-135">After this initial step, you will only need to run `dotnet restore` ([see note](#dotnet-restore-note)) when you add new dependent packages, or update the versions of any of your dependencies.</span></span> <span data-ttu-id="0372a-136">Tento proces také vytvoří soubor zámku projektu (project.lock.json) v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="0372a-136">This process also creates the project lock file (project.lock.json) in your project directory.</span></span> <span data-ttu-id="0372a-137">Tento soubor pomáhá spravovat závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="0372a-137">This file helps to manage the project dependencies.</span></span> <span data-ttu-id="0372a-138">Obsahuje místní umístění všechny závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="0372a-138">It contains the local location of all the project dependencies.</span></span> <span data-ttu-id="0372a-139">Není potřeba umístit soubor do správy zdrojového kódu; Při spuštění budou generovány `dotnet restore` ([viz Poznámka](#dotnet-restore-note)).</span><span class="sxs-lookup"><span data-stu-id="0372a-139">You do not need to put the file in source control; it will be generated when you run `dotnet restore` ([see note](#dotnet-restore-note)).</span></span> 

<span data-ttu-id="0372a-140">Po obnovení balíčků, můžete spustit `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="0372a-140">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="0372a-141">To provede modul sestavení a vytvoří spustitelný soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="0372a-141">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="0372a-142">Nakonec spuštěním `dotnet run` spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0372a-142">Finally, you execute `dotnet run` to run your application.</span></span>  

<span data-ttu-id="0372a-143">Jednoduchý kód aplikace Hello World je v souboru Program.cs.</span><span class="sxs-lookup"><span data-stu-id="0372a-143">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="0372a-144">Otevřete tento soubor se svém oblíbeném textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="0372a-144">Open that file with your favorite text editor.</span></span> <span data-ttu-id="0372a-145">Jsme naše první změny.</span><span class="sxs-lookup"><span data-stu-id="0372a-145">We’re about to make our first changes.</span></span>
<span data-ttu-id="0372a-146">V horní části souboru, najdete v části pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="0372a-146">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="0372a-147">Tento příkaz informuje kompilátor všechny typy z `System` obor názvů jsou v oboru.</span><span class="sxs-lookup"><span data-stu-id="0372a-147">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="0372a-148">Podobně jako ostatní objektově orientované jazyky, které možná zneužil C# používá obory názvů organizovat typy.</span><span class="sxs-lookup"><span data-stu-id="0372a-148">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="0372a-149">Tento program hello world se neliší.</span><span class="sxs-lookup"><span data-stu-id="0372a-149">This hello world program is no different.</span></span> <span data-ttu-id="0372a-150">Uvidíte, že program ohraničeno `ConsoleApplication` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0372a-150">You can see that the program is enclosed in the `ConsoleApplication` namespace.</span></span> <span data-ttu-id="0372a-151">Není velmi popisný název, takže změňte ho na `TeleprompterConsole`:</span><span class="sxs-lookup"><span data-stu-id="0372a-151">That’s not a very descriptive name, so change it to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="0372a-152">Čtení a zobrazování souboru</span><span class="sxs-lookup"><span data-stu-id="0372a-152">Reading and Echoing the File</span></span>
<span data-ttu-id="0372a-153">První funkce přidání je možnost čtení z textového souboru a zobrazit všechny tento text do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0372a-153">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="0372a-154">Nejprve přidejme do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="0372a-154">First, let’s add a text file.</span></span> <span data-ttu-id="0372a-155">Kopírování [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) soubor z úložiště GitHub pro tento [ukázka](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="0372a-155">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="0372a-156">To bude sloužit jako skript pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0372a-156">This will serve as the script for your application.</span></span> <span data-ttu-id="0372a-157">Pokud vás zajímají informace o tom, jak stáhnout ukázkové aplikace pro toto téma, postupujte podle pokynů v [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) tématu.</span><span class="sxs-lookup"><span data-stu-id="0372a-157">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="0372a-158">Dál přidejte následující metodu v třídě Program (přímo pod `Main` metoda):</span><span class="sxs-lookup"><span data-stu-id="0372a-158">Next, add the following method in your Program class (right below the `Main` method):</span></span>

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

<span data-ttu-id="0372a-159">Tato metoda používá typů z dva nové obory názvů.</span><span class="sxs-lookup"><span data-stu-id="0372a-159">This method uses types from two new namespaces.</span></span> <span data-ttu-id="0372a-160">Tento postup můžete zkompilovat budete potřebovat na začátek souboru přidejte následující dva řádky:</span><span class="sxs-lookup"><span data-stu-id="0372a-160">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="0372a-161">`IEnumerable<T>` Rozhraní je definováno v `System.Collections.Generic` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0372a-161">The `IEnumerable<T>` interface is defined in the `System.Collections.Generic` namespace.</span></span> <span data-ttu-id="0372a-162"><xref:System.IO.File> Třída definovaná v `System.IO` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0372a-162">The <xref:System.IO.File> class is defined in the `System.IO` namespace.</span></span>

<span data-ttu-id="0372a-163">Tato metoda je zvláštní druh C# metodu s názvem *enumerátor metoda*.</span><span class="sxs-lookup"><span data-stu-id="0372a-163">This method is a special type of C# method called an *Enumerator method*.</span></span> <span data-ttu-id="0372a-164">Vrátí enumerátor metody pořadí, které se vyhodnocují líné.</span><span class="sxs-lookup"><span data-stu-id="0372a-164">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="0372a-165">To znamená, že každá položka v pořadí se vygeneruje, jak vyžádala kód využívání sekvenci.</span><span class="sxs-lookup"><span data-stu-id="0372a-165">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="0372a-166">Enumerátor metody jsou metody, které obsahují jednu nebo více `yield return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="0372a-166">Enumerator methods are methods that contain one or more `yield return` statements.</span></span> <span data-ttu-id="0372a-167">Objekt vrácený `ReadFrom` metoda obsahuje kód pro generování každou položku v pořadí.</span><span class="sxs-lookup"><span data-stu-id="0372a-167">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="0372a-168">V tomto příkladu, který zahrnuje čtení na další řádek textu ze zdrojového souboru a vrácení tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="0372a-168">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="0372a-169">Pokaždé, když kód volání požadavků na další položku z řady, kód čte na další řádek textu ze souboru a vrátí ji.</span><span class="sxs-lookup"><span data-stu-id="0372a-169">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="0372a-170">Při soubor byl zcela přečíst, sekvenci označuje, že neexistují žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="0372a-170">When the file has been completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="0372a-171">Existují dva další C# syntaxe prvky, které může být pro vás nový.</span><span class="sxs-lookup"><span data-stu-id="0372a-171">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="0372a-172">`using` Příkaz v této metodě spravuje vyčištění prostředků.</span><span class="sxs-lookup"><span data-stu-id="0372a-172">The `using` statement in this method manages resource cleanup.</span></span> <span data-ttu-id="0372a-173">Proměnné, která je v inicializovat `using` – příkaz (`reader`, v tomto příkladu) musí implementovat `IDisposable` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0372a-173">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the `IDisposable` interface.</span></span> <span data-ttu-id="0372a-174"><xref:System.IDisposable> Rozhraní definuje jedinou metodu `Dispose`, která by měla být volána, když prostředek by měly být uvolněny.</span><span class="sxs-lookup"><span data-stu-id="0372a-174">The <xref:System.IDisposable> interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="0372a-175">Kompilátor generuje tohoto volání při provádění dosáhne složená závorka `using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="0372a-175">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="0372a-176">Kód generované kompilátorem zajistí, že prostředek vydání i v případě, že je vyvolána výjimka z kódu v bloku definované na pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="0372a-176">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="0372a-177">`reader` Proměnná je definována pomocí `var` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0372a-177">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="0372a-178">`var` definuje *implicitně typované lokální proměnné*.</span><span class="sxs-lookup"><span data-stu-id="0372a-178">`var` defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="0372a-179">To znamená, že typ proměnné je určen podle typu čas kompilace objekt přiřazenou proměnné.</span><span class="sxs-lookup"><span data-stu-id="0372a-179">That means the type of the variable is determined by the compile time type of the object assigned to the variable.</span></span> <span data-ttu-id="0372a-180">Tady, který je vrácená hodnota z <xref:System.IO.File.OpenText(System.String)> metoda, která je <xref:System.IO.StreamReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="0372a-180">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>
 
<span data-ttu-id="0372a-181">Nyní Pojďme zadejte kód pro čtení tohoto souboru v `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="0372a-181">Now, let’s fill in the code to read the file in the `Main` method:</span></span> 

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line); 
}
```

<span data-ttu-id="0372a-182">Spusťte program (pomocí `dotnet run` a zobrazí se všechny řádky, vytisknout ke konzole).</span><span class="sxs-lookup"><span data-stu-id="0372a-182">Run the program (using `dotnet run` and you can see every line printed out to the console).</span></span>  

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="0372a-183">Přidávání zpoždění a formátování výstupu</span><span class="sxs-lookup"><span data-stu-id="0372a-183">Adding Delays and Formatting output</span></span>
<span data-ttu-id="0372a-184">Je nutné se zobrazuje příliš rychlé pro čtení.</span><span class="sxs-lookup"><span data-stu-id="0372a-184">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="0372a-185">Teď je potřeba přidat zpoždění ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="0372a-185">Now you need to add the delays in the output.</span></span> <span data-ttu-id="0372a-186">Když začnete, budete se vytváření, některé základní kód, který umožňuje asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="0372a-186">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="0372a-187">První takto bude postupujte podle několik proti vzory.</span><span class="sxs-lookup"><span data-stu-id="0372a-187">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="0372a-188">Proti vzory jsou zdůraznit v komentářích přidejte kód a kód bude aktualizován v dalších krocích.</span><span class="sxs-lookup"><span data-stu-id="0372a-188">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="0372a-189">Existují dva kroky v této části.</span><span class="sxs-lookup"><span data-stu-id="0372a-189">There are two steps to this section.</span></span> <span data-ttu-id="0372a-190">Nejprve budete aktualizovat metodu iterator vrátit jednoho slova místo celé řádky.</span><span class="sxs-lookup"><span data-stu-id="0372a-190">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="0372a-191">Která se provádí s tyto úpravy.</span><span class="sxs-lookup"><span data-stu-id="0372a-191">That’s done with these modifications.</span></span> <span data-ttu-id="0372a-192">Nahraďte `yield return line;` příkaz následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="0372a-192">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="0372a-193">Dále musíte upravit jak využívat řádky souboru a přidejte zpoždění po napsání jednotlivých slov.</span><span class="sxs-lookup"><span data-stu-id="0372a-193">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="0372a-194">Nahraďte `Console.WriteLine(line)` příkaz v `Main` metoda s následující blok:</span><span class="sxs-lookup"><span data-stu-id="0372a-194">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<span data-ttu-id="0372a-195">`Task` Třída je v `System.Threading.Tasks` obor názvů, takže budete muset přidat `using` příkaz v horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="0372a-195">The `Task` class is in the `System.Threading.Tasks` namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="0372a-196">Ukázku spustit a zkontrolujte výstup.</span><span class="sxs-lookup"><span data-stu-id="0372a-196">Run the sample, and check the output.</span></span> <span data-ttu-id="0372a-197">Nyní je vytištěno každý jednoho slova, za nímž následuje zpožděním 200 ms.</span><span class="sxs-lookup"><span data-stu-id="0372a-197">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="0372a-198">Ale zobrazených výstup zobrazuje některé problémy, protože zdroj textového souboru má několik řádků, které mají více než 80 znaků bez konec řádku.</span><span class="sxs-lookup"><span data-stu-id="0372a-198">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="0372a-199">Který může být těžko čitelný, když je posouvání pomocí.</span><span class="sxs-lookup"><span data-stu-id="0372a-199">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="0372a-200">To je snadno opravit.</span><span class="sxs-lookup"><span data-stu-id="0372a-200">That’s easy to fix.</span></span> <span data-ttu-id="0372a-201">Budete právě udržování přehledu o délce každého řádku a vygenerovat nový řádek vždy, když délka řádku dosáhne určité prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0372a-201">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="0372a-202">Deklarujte místní proměnné po deklaraci `words` kterém jsou uložena délka řádku:</span><span class="sxs-lookup"><span data-stu-id="0372a-202">Declare a local variable after the declaration of `words` that holds the line length:</span></span>

```csharp
var lineLength = 0;
```
 
<span data-ttu-id="0372a-203">Pak přidejte následující kód po `yield return word + " ";` (než pravé složené závorce):</span><span class="sxs-lookup"><span data-stu-id="0372a-203">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```
 
<span data-ttu-id="0372a-204">Ukázku spustit, a budete moct nahlas přečíst v její předem nakonfigurovaná rychle.</span><span class="sxs-lookup"><span data-stu-id="0372a-204">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="0372a-205">Úloh s modifikátorem Async</span><span class="sxs-lookup"><span data-stu-id="0372a-205">Async Tasks</span></span>
<span data-ttu-id="0372a-206">V tomto posledním kroku přidáte kód pro zápis výstupu asynchronně v jedné úloze při také spuštěna jiná úloha číst vstupní od uživatele, pokud chtějí zrychlit nebo zpomalit zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="0372a-206">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display.</span></span> <span data-ttu-id="0372a-207">To má několik kroků a na konci, budete mít všechny aktualizace, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="0372a-207">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="0372a-208">Prvním krokem je vytvoření asynchronní <xref:System.Threading.Tasks.Task> vrácení metoda, která představuje kód, pokud jste vytvořili pro čtení a zobrazit soubor.</span><span class="sxs-lookup"><span data-stu-id="0372a-208">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="0372a-209">Přidejte tuto metodu za účelem vaše `Program` – třída (jsou převzaty z textu vaší `Main` metoda):</span><span class="sxs-lookup"><span data-stu-id="0372a-209">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="0372a-210">Můžete si všimnout dvou změny.</span><span class="sxs-lookup"><span data-stu-id="0372a-210">You’ll notice two changes.</span></span> <span data-ttu-id="0372a-211">První v těle metody, namísto volání <xref:System.Threading.Tasks.Task.Wait> synchronně počkat na dokončení úlohy, používá tato verze `await` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0372a-211">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="0372a-212">Aby bylo možné provést, je nutné přidat `async` modifikátor k označení metody.</span><span class="sxs-lookup"><span data-stu-id="0372a-212">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="0372a-213">Tato metoda vrátí hodnotu `Task`.</span><span class="sxs-lookup"><span data-stu-id="0372a-213">This method returns a `Task`.</span></span> <span data-ttu-id="0372a-214">Všimněte si, že neexistují žádné návratový příkazy, které vracejí `Task` objektu.</span><span class="sxs-lookup"><span data-stu-id="0372a-214">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="0372a-215">Místo toho, který `Task` objekt se vytvoří v kódu kompilátor vygeneruje při použití `await` operátor.</span><span class="sxs-lookup"><span data-stu-id="0372a-215">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="0372a-216">Představte si, že tato metoda vrátí při dosažení `await`.</span><span class="sxs-lookup"><span data-stu-id="0372a-216">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="0372a-217">Vrácený `Task` znamená, že práce nebyl dokončen.</span><span class="sxs-lookup"><span data-stu-id="0372a-217">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="0372a-218">Metoda obnoví při dokončení awaited úlohy.</span><span class="sxs-lookup"><span data-stu-id="0372a-218">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="0372a-219">Když se provedla k dokončení, vrácený `Task` označuje, že je kompletní.</span><span class="sxs-lookup"><span data-stu-id="0372a-219">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="0372a-220">Volání kódu můžete monitorovat vrácená `Task` k určení, kdy byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="0372a-220">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="0372a-221">Tato nová metoda můžete volat vaší `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="0372a-221">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="0372a-222">Zde v `Main`, kód synchronně čekání.</span><span class="sxs-lookup"><span data-stu-id="0372a-222">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="0372a-223">Měli byste použít `await` operátor místo abyste čekali synchronně, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="0372a-223">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="0372a-224">Ale v konzolové aplikaci `Main` metodu, nemůžete použít `await` operátor.</span><span class="sxs-lookup"><span data-stu-id="0372a-224">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="0372a-225">Může se stát, který by způsobilo ukončení aplikace před všechny úkoly dokončí.</span><span class="sxs-lookup"><span data-stu-id="0372a-225">That would result in the application exiting before all tasks have completed.</span></span>

<span data-ttu-id="0372a-226">Potom budete muset napsat druhé asynchronní metody pro čtení z konzoly a sledovat ' <' a ' >' klíče.</span><span class="sxs-lookup"><span data-stu-id="0372a-226">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ and ‘>’ keys.</span></span> <span data-ttu-id="0372a-227">Tady je metoda, které přidáte pro tuto úlohu:</span><span class="sxs-lookup"><span data-stu-id="0372a-227">Here’s the method you add for that task:</span></span>

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="0372a-228">Tím se vytvoří výrazu lambda představují <xref:System.Action> delegáta, který čte klíč z konzoly a upravuje místní proměnné představující zpoždění při stisknutí ' <' nebo ' >' klíče.</span><span class="sxs-lookup"><span data-stu-id="0372a-228">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ or ‘>’ keys.</span></span> <span data-ttu-id="0372a-229">Tato metoda používá <xref:System.Console.ReadKey> blokovat a čekat, uživatel ke stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="0372a-229">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="0372a-230">Chcete-li dokončit tuto funkci, je potřeba vytvořit novou `async Task` vrácení metoda, která spustí obě tyto úlohy (`GetInput` a `ShowTeleprompter`) a také spravuje sdílených dat mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="0372a-230">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>
 
<span data-ttu-id="0372a-231">Je čas vytvořit třídu, která dokáže zpracovat sdílených dat mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="0372a-231">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="0372a-232">Tato třída obsahuje dvě veřejné vlastnosti: zpoždění a příznak označující, úplně čtení souboru:</span><span class="sxs-lookup"><span data-stu-id="0372a-232">This class contains two public properties: the delay, and a flag to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }
    }
}
```

<span data-ttu-id="0372a-233">Vložte nový soubor třídy a uzavřete třídy v `TeleprompterConsole` obor názvů, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="0372a-233">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="0372a-234">Také budete muset přidat `using static` příkaz tak, aby můžete odkazovat `Min` a `Max` metoda bez nadřazených třída nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="0372a-234">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` method without the enclosing class or namespace names.</span></span> <span data-ttu-id="0372a-235">A `using static` příkaz importuje metody z jedné třídy.</span><span class="sxs-lookup"><span data-stu-id="0372a-235">A `using static` statement imports the methods from one class.</span></span> <span data-ttu-id="0372a-236">To je rozdíl s `using` použít v tomto okamžiku příkazů, které jste importovali všechny třídy z oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0372a-236">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="0372a-237">Jiné, je nová funkce jazyka je `lock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="0372a-237">The other language feature that’s new is the `lock` statement.</span></span> <span data-ttu-id="0372a-238">Tento příkaz zajistí, že pouze jedno vlákno mohou být v tomto kódu v daném okamžiku.</span><span class="sxs-lookup"><span data-stu-id="0372a-238">This statement ensures that only a single thread can be in that code at any given time.</span></span> <span data-ttu-id="0372a-239">Pokud jedno vlákno je v uzamčeném části, musí jiná vlákna počkejte první vlákno ukončíte této části.</span><span class="sxs-lookup"><span data-stu-id="0372a-239">If one thread is in the locked section, other threads must wait for the first thread to exit that section.</span></span> <span data-ttu-id="0372a-240">`lock` Příkaz používá objekt, který chrání zamknout oddíl.</span><span class="sxs-lookup"><span data-stu-id="0372a-240">The `lock` statement uses an object that guards the lock section.</span></span> <span data-ttu-id="0372a-241">Tato třída pracuje standardní stylu k uzamčení soukromý objekt ve třídě.</span><span class="sxs-lookup"><span data-stu-id="0372a-241">This class follows a standard idiom to lock a private object in the class.</span></span>

<span data-ttu-id="0372a-242">Dále je potřeba aktualizovat `ShowTeleprompter` a `GetInput` můžete použít nové metody `config` objektu.</span><span class="sxs-lookup"><span data-stu-id="0372a-242">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="0372a-243">Zápis jeden konečné `Task` vrácení `async` metoda spuštění obě úlohy a po dokončení prvního úkolu ukončit:</span><span class="sxs-lookup"><span data-stu-id="0372a-243">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="0372a-244">Je zde jeden nová metoda <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> volání.</span><span class="sxs-lookup"><span data-stu-id="0372a-244">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="0372a-245">Které vytváří `Task` který dokončí při dokončení některých úkolů ve svém seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="0372a-245">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="0372a-246">Dále je potřeba aktualizovat i `ShowTeleprompter` a `GetInput` metod používaných `config` objekt zpoždění:</span><span class="sxs-lookup"><span data-stu-id="0372a-246">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{

    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="0372a-247">Tuto novou verzi `ShowTeleprompter` volání do nové metody `TeleprompterConfig` třídy.</span><span class="sxs-lookup"><span data-stu-id="0372a-247">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="0372a-248">Nyní, budete muset aktualizovat `Main` volat `RunTeleprompter` místo `ShowTeleprompter`:</span><span class="sxs-lookup"><span data-stu-id="0372a-248">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

<span data-ttu-id="0372a-249">K dokončení, budete muset přidat `SetDone` metody a `Done` vlastnost, která má `TelePrompterConfig` – třída:</span><span class="sxs-lookup"><span data-stu-id="0372a-249">To finish, you'll need to add the `SetDone` method, and the `Done` property to the `TelePrompterConfig` class:</span></span>

```csharp
public bool Done => done;

private bool done;

public void SetDone()
{
    done = true;    
}
```

## <a name="conclusion"></a><span data-ttu-id="0372a-250">Závěr</span><span class="sxs-lookup"><span data-stu-id="0372a-250">Conclusion</span></span>
<span data-ttu-id="0372a-251">Tento kurz vám ukázal, že jste celou řadu funkcí kolem jazyka C# a knihovny .NET Core týkající se práce v konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="0372a-251">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="0372a-252">Můžete vytvořit tyto znalosti prozkoumat více o jazyce a třídy zavedené sem.</span><span class="sxs-lookup"><span data-stu-id="0372a-252">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="0372a-253">Seznámili jste se základy a vstupně-výstupních operací konzoly, blokování a neblokující použití úlohy na základě asynchronního programování modelu, prohlídka jazyka C# a jak jsou uspořádány programy C# a rozhraní příkazového řádku .NET Core a nástroje.</span><span class="sxs-lookup"><span data-stu-id="0372a-253">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task based Asynchronous programming model, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>
 
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]