---
title: Konzolová aplikace
description: V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: bae03c9ae02f2888b1b70617ca712ef7927e9dce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355483"
---
# <a name="console-application"></a><span data-ttu-id="2b7f0-103">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="2b7f0-103">Console Application</span></span>

<span data-ttu-id="2b7f0-104">V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="2b7f0-105">Naučíte:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-105">You’ll learn:</span></span>

- <span data-ttu-id="2b7f0-106">Základy .NET Core rozhraní příkazového řádku (CLI)</span><span class="sxs-lookup"><span data-stu-id="2b7f0-106">The basics of the .NET Core Command Line Interface (CLI)</span></span>
- <span data-ttu-id="2b7f0-107">Struktura konzolovou aplikaci C#</span><span class="sxs-lookup"><span data-stu-id="2b7f0-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="2b7f0-108">Konzole vstupně-výstupních operací</span><span class="sxs-lookup"><span data-stu-id="2b7f0-108">Console I/O</span></span>
- <span data-ttu-id="2b7f0-109">Základní informace o rozhraní API pro vstupně-výstupních souborů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="2b7f0-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="2b7f0-110">Základy založený na úlohách asynchronní programování v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="2b7f0-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="2b7f0-111">Budete sestavit aplikaci, která čte textový soubor a vrátí je obsah na konzole tohoto textového souboru.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-111">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="2b7f0-112">Výstup do konzoly je pracovníky tak, aby odpovídaly nahlas jeho čtení.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="2b7f0-113">Můžete urychlit nebo zpomalit rychlost stisknutím ' <' nebo ' >' klíče.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-113">You can speed up or slow down the pace by pressing the ‘<’ or ‘>’ keys.</span></span>

<span data-ttu-id="2b7f0-114">V tomto kurzu je celá řada funkcí.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="2b7f0-115">Umožňuje vytvořit, je po jednom.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-115">Let’s build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2b7f0-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b7f0-116">Prerequisites</span></span>

<span data-ttu-id="2b7f0-117">Budete potřebovat k nastavení vašeho počítače ke spuštění .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-117">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="2b7f0-118">Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-118">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="2b7f0-119">Tuto aplikaci můžete spustit v systému Windows, Linux, systému macOS nebo v kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-119">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="2b7f0-120">Budete muset nainstalovat editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-120">You’ll need to install your favorite code editor.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="2b7f0-121">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="2b7f0-121">Create the Application</span></span>

<span data-ttu-id="2b7f0-122">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-122">The first step is to create a new application.</span></span> <span data-ttu-id="2b7f0-123">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="2b7f0-124">Nastavit aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-124">Make that the current directory.</span></span> <span data-ttu-id="2b7f0-125">Zadejte příkaz `dotnet new console` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="2b7f0-126">Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".</span><span class="sxs-lookup"><span data-stu-id="2b7f0-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="2b7f0-127">Než začnete, provádění změn, přejděte přes kroky a spusťte tak jednoduchou aplikaci Hello World.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-127">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="2b7f0-128">Po vytvoření aplikace, zadejte `dotnet restore` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="2b7f0-129">Tento příkaz spustí proces obnovení balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="2b7f0-130">NuGet je Správce balíčků .NET.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="2b7f0-131">Tento příkaz stáhne všechny chybějící závislosti pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="2b7f0-132">Toto je nový projekt, žádné závislosti na místě, se tak během prvního spuštění stáhnou rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="2b7f0-133">Po provedení tohoto kroku počáteční se jenom musíte spustit `dotnet restore` při přidání nové závislé balíčky nebo aktualizace verze všechny svoje závislosti.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="2b7f0-134">Po obnovení balíčků, můžete spustit `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="2b7f0-135">To provede modul sestavení a vytvoří spustitelný soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="2b7f0-136">Nakonec spuštěním `dotnet run` spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="2b7f0-137">Jednoduchý kód aplikace Hello World je v souboru Program.cs.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="2b7f0-138">Otevřete tento soubor se svém oblíbeném textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="2b7f0-139">Jsme naše první změny.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-139">We’re about to make our first changes.</span></span>
<span data-ttu-id="2b7f0-140">V horní části souboru, najdete v části pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="2b7f0-141">Tento příkaz informuje kompilátor všechny typy z `System` obor názvů jsou v oboru.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="2b7f0-142">Podobně jako ostatní objektově orientované jazyky, které možná zneužil C# používá obory názvů organizovat typy.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="2b7f0-143">Tento program Hello World se neliší.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-143">This Hello World program is no different.</span></span> <span data-ttu-id="2b7f0-144">Uvidíte, že je program uzavřena v oboru názvů s názvem na základě názvu aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="2b7f0-145">V tomto kurzu, změňte název oboru názvů `TeleprompterConsole`:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="2b7f0-146">Čtení a zobrazování souboru</span><span class="sxs-lookup"><span data-stu-id="2b7f0-146">Reading and Echoing the File</span></span>

<span data-ttu-id="2b7f0-147">První funkce přidání je možnost čtení z textového souboru a zobrazit všechny tento text do konzoly.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="2b7f0-148">Nejprve přidejme do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-148">First, let’s add a text file.</span></span> <span data-ttu-id="2b7f0-149">Kopírování [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) soubor z úložiště GitHub pro tento [ukázka](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="2b7f0-150">To bude sloužit jako skript pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-150">This will serve as the script for your application.</span></span> <span data-ttu-id="2b7f0-151">Pokud vás zajímají informace o tom, jak stáhnout ukázkové aplikace pro toto téma, postupujte podle pokynů v [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) tématu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="2b7f0-152">Dál přidejte následující metodu v vaše `Program` – třída (přímo pod `Main` metoda):</span><span class="sxs-lookup"><span data-stu-id="2b7f0-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

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

<span data-ttu-id="2b7f0-153">Tato metoda používá typů z dva nové obory názvů.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="2b7f0-154">Tento postup můžete zkompilovat budete potřebovat na začátek souboru přidejte následující dva řádky:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-154">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="2b7f0-155"><xref:System.Collections.Generic.IEnumerable%601> Rozhraní je definováno v <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="2b7f0-156"><xref:System.IO.File> Třída definovaná v <xref:System.IO> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="2b7f0-157">Tato metoda je zvláštní druh C# metodu s názvem *Iterator – metoda*.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="2b7f0-158">Vrátí enumerátor metody pořadí, které se vyhodnocují líné.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="2b7f0-159">To znamená, že každá položka v pořadí se vygeneruje, jak vyžádala kód využívání sekvenci.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="2b7f0-160">Enumerátor metody jsou metody, které obsahují jednu nebo více [ `yield return` ](../language-reference/keywords/yield.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="2b7f0-161">Objekt vrácený `ReadFrom` metoda obsahuje kód pro generování každou položku v pořadí.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="2b7f0-162">V tomto příkladu, který zahrnuje čtení na další řádek textu ze zdrojového souboru a vrácení tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="2b7f0-163">Pokaždé, když kód volání požadavků na další položku z řady, kód čte na další řádek textu ze souboru a vrátí ji.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="2b7f0-164">Při soubor je zcela přečíst, sekvenci označuje, že neexistují žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="2b7f0-165">Existují dva další C# syntaxe prvky, které může být pro vás nový.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="2b7f0-166">[ `using` ](../language-reference/keywords/using-statement.md) Příkaz v této metodě spravuje vyčištění prostředků.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="2b7f0-167">Proměnné, která je v inicializovat `using` – příkaz (`reader`, v tomto příkladu) musí implementovat <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="2b7f0-168">Toto rozhraní definuje jedinou metodu `Dispose`, která by měla být volána, když prostředek by měly být uvolněny.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="2b7f0-169">Kompilátor generuje tohoto volání při provádění dosáhne složená závorka `using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="2b7f0-170">Kód generované kompilátorem zajistí, že prostředek vydání i v případě, že je vyvolána výjimka z kódu v bloku definované na pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="2b7f0-171">`reader` Proměnná je definována pomocí `var` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="2b7f0-172">[`var`](../language-reference/keywords/var.md) definuje *implicitně typované lokální proměnné*.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="2b7f0-173">To znamená, že typ proměnné je určen podle typu kompilaci objektu přiřazenou proměnné.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="2b7f0-174">Tady, který je vrácená hodnota z <xref:System.IO.File.OpenText(System.String)> metoda, která je <xref:System.IO.StreamReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="2b7f0-175">Nyní Pojďme zadejte kód pro čtení tohoto souboru v `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-175">Now, let’s fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="2b7f0-176">Spusťte program (pomocí `dotnet run`) a zobrazí se všechny řádky, vytisknout ke konzole.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="2b7f0-177">Přidávání zpoždění a formátování výstupu</span><span class="sxs-lookup"><span data-stu-id="2b7f0-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="2b7f0-178">Je nutné se zobrazuje příliš rychlé pro čtení.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="2b7f0-179">Teď je potřeba přidat zpoždění ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="2b7f0-180">Když začnete, budete se vytváření, některé základní kód, který umožňuje asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-180">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="2b7f0-181">První takto bude postupujte podle několik proti vzory.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="2b7f0-182">Proti vzory jsou zdůraznit v komentářích přidejte kód a kód bude aktualizován v dalších krocích.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="2b7f0-183">Existují dva kroky v této části.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-183">There are two steps to this section.</span></span> <span data-ttu-id="2b7f0-184">Nejprve budete aktualizovat metodu iterator vrátit jednoho slova místo celé řádky.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-184">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="2b7f0-185">Která se provádí s tyto úpravy.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-185">That’s done with these modifications.</span></span> <span data-ttu-id="2b7f0-186">Nahraďte `yield return line;` příkaz následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="2b7f0-187">Dále musíte upravit jak využívat řádky souboru a přidejte zpoždění po napsání jednotlivých slov.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="2b7f0-188">Nahraďte `Console.WriteLine(line)` příkaz v `Main` metoda s následující blok:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

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

<span data-ttu-id="2b7f0-189"><xref:System.Threading.Tasks.Task> Třída je v <xref:System.Threading.Tasks> obor názvů, takže budete muset přidat `using` příkaz v horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="2b7f0-190">Ukázku spustit a zkontrolujte výstup.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-190">Run the sample, and check the output.</span></span> <span data-ttu-id="2b7f0-191">Nyní je vytištěno každý jednoho slova, za nímž následuje zpožděním 200 ms.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="2b7f0-192">Ale zobrazených výstup zobrazuje některé problémy, protože zdroj textového souboru má několik řádků, které mají více než 80 znaků bez konec řádku.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="2b7f0-193">Který může být těžko čitelný, když je posouvání pomocí.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="2b7f0-194">To je snadno opravit.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-194">That’s easy to fix.</span></span> <span data-ttu-id="2b7f0-195">Budete právě udržování přehledu o délce každého řádku a vygenerovat nový řádek vždy, když délka řádku dosáhne určité prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-195">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="2b7f0-196">Deklarujte místní proměnné po deklaraci `words` v `ReadFrom` metoda, která obsahuje délka řádku:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="2b7f0-197">Pak přidejte následující kód po `yield return word + " ";` (než pravé složené závorce):</span><span class="sxs-lookup"><span data-stu-id="2b7f0-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="2b7f0-198">Ukázku spustit, a budete moct nahlas přečíst v její předem nakonfigurovaná rychle.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-198">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="2b7f0-199">Úloh s modifikátorem Async</span><span class="sxs-lookup"><span data-stu-id="2b7f0-199">Async Tasks</span></span>

<span data-ttu-id="2b7f0-200">V tomto posledním kroku přidáte kód pro zápis výstupu asynchronně v jedné úloze při také spuštěna jiná úloha číst vstupní od uživatele, pokud chtějí zrychlit nebo zpomalit zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-200">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display.</span></span> <span data-ttu-id="2b7f0-201">To má několik kroků a na konci, budete mít všechny aktualizace, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-201">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="2b7f0-202">Prvním krokem je vytvoření asynchronní <xref:System.Threading.Tasks.Task> vrácení metoda, která představuje kód, pokud jste vytvořili pro čtení a zobrazit soubor.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="2b7f0-203">Přidejte tuto metodu za účelem vaše `Program` – třída (jsou převzaty z textu vaší `Main` metoda):</span><span class="sxs-lookup"><span data-stu-id="2b7f0-203">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="2b7f0-204">Můžete si všimnout dvou změny.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-204">You’ll notice two changes.</span></span> <span data-ttu-id="2b7f0-205">První v těle metody, namísto volání <xref:System.Threading.Tasks.Task.Wait> synchronně počkat na dokončení úlohy, používá tato verze `await` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="2b7f0-206">Aby bylo možné provést, je nutné přidat `async` modifikátor k označení metody.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="2b7f0-207">Tato metoda vrátí hodnotu `Task`.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-207">This method returns a `Task`.</span></span> <span data-ttu-id="2b7f0-208">Všimněte si, že neexistují žádné návratový příkazy, které vracejí `Task` objektu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="2b7f0-209">Místo toho, který `Task` objekt se vytvoří v kódu kompilátor vygeneruje při použití `await` operátor.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="2b7f0-210">Představte si, že tato metoda vrátí při dosažení `await`.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="2b7f0-211">Vrácený `Task` znamená, že práce nebyl dokončen.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-211">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="2b7f0-212">Metoda obnoví při dokončení awaited úlohy.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="2b7f0-213">Když se provedla k dokončení, vrácený `Task` označuje, že je kompletní.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="2b7f0-214">Volání kódu můžete monitorovat vrácená `Task` k určení, kdy byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="2b7f0-215">Tato nová metoda můžete volat vaší `Main` metoda:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="2b7f0-216">Zde v `Main`, kód synchronně čekání.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="2b7f0-217">Měli byste použít `await` operátor místo abyste čekali synchronně, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="2b7f0-218">Ale v konzolové aplikaci `Main` metodu, nemůžete použít `await` operátor.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-218">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="2b7f0-219">Může se stát, který by způsobilo ukončení aplikace před všechny úkoly dokončí.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="2b7f0-220">Pokud používáte C# 7.1 nebo novější, můžete vytvořit konzolové aplikace s [ `async` `Main` metoda](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="2b7f0-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="2b7f0-221">Potom budete muset napsat druhé asynchronní metody pro čtení z konzoly a sledovat ' <' a ' >' klíče.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-221">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ and ‘>’ keys.</span></span> <span data-ttu-id="2b7f0-222">Tady je metoda, které přidáte pro tuto úlohu:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-222">Here’s the method you add for that task:</span></span>

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

<span data-ttu-id="2b7f0-223">Tím se vytvoří výrazu lambda představují <xref:System.Action> delegáta, který čte klíč z konzoly a upravuje místní proměnné představující zpoždění při stisknutí ' <' nebo ' >' klíče.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ or ‘>’ keys.</span></span> <span data-ttu-id="2b7f0-224">Tato metoda používá <xref:System.Console.ReadKey> blokovat a čekat, uživatel ke stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-224">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="2b7f0-225">Chcete-li dokončit tuto funkci, je potřeba vytvořit novou `async Task` vrácení metoda, která spustí obě tyto úlohy (`GetInput` a `ShowTeleprompter`) a také spravuje sdílených dat mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-225">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="2b7f0-226">Je čas vytvořit třídu, která dokáže zpracovat sdílených dat mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-226">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="2b7f0-227">Tato třída obsahuje dvě veřejné vlastnosti: zpoždění a příznak `Done` k označení úplně čtení souboru:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-227">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

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

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="2b7f0-228">Vložte nový soubor třídy a uzavřete třídy v `TeleprompterConsole` obor názvů, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-228">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="2b7f0-229">Také budete muset přidat `using static` příkaz tak, aby můžete odkazovat `Min` a `Max` metody bez nadřazených třída nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-229">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="2b7f0-230">A [ `using static` ](../language-reference/keywords/using-static.md) příkaz importuje metody z jedné třídy.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-230">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="2b7f0-231">To je rozdíl s `using` použít v tomto okamžiku příkazů, které jste importovali všechny třídy z oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-231">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="2b7f0-232">Jiné, je nová funkce jazyka je [ `lock` ](../language-reference/keywords/lock-statement.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-232">The other language feature that’s new is the [`lock`](../language-reference/keywords/lock-statement.md) statement.</span></span> <span data-ttu-id="2b7f0-233">Tento příkaz zajistí, že pouze jedno vlákno mohou být v tomto kódu v daném okamžiku.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-233">This statement ensures that only a single thread can be in that code at any given time.</span></span> <span data-ttu-id="2b7f0-234">Pokud jedno vlákno je v uzamčeném části, musí jiná vlákna počkejte první vlákno ukončíte této části.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-234">If one thread is in the locked section, other threads must wait for the first thread to exit that section.</span></span> <span data-ttu-id="2b7f0-235">`lock` Příkaz používá objekt, který chrání zamknout oddíl.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-235">The `lock` statement uses an object that guards the lock section.</span></span> <span data-ttu-id="2b7f0-236">Tato třída pracuje standardní stylu k uzamčení soukromý objekt ve třídě.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-236">This class follows a standard idiom to lock a private object in the class.</span></span>

<span data-ttu-id="2b7f0-237">Dále je potřeba aktualizovat `ShowTeleprompter` a `GetInput` můžete použít nové metody `config` objektu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-237">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="2b7f0-238">Zápis jeden konečné `Task` vrácení `async` metoda spuštění obě úlohy a po dokončení prvního úkolu ukončit:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-238">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="2b7f0-239">Je zde jeden nová metoda <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> volání.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-239">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="2b7f0-240">Které vytváří `Task` který dokončí při dokončení některých úkolů ve svém seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-240">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="2b7f0-241">Dále je potřeba aktualizovat i `ShowTeleprompter` a `GetInput` metod používaných `config` objekt zpoždění:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-241">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

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

<span data-ttu-id="2b7f0-242">Tuto novou verzi `ShowTeleprompter` volání do nové metody `TeleprompterConfig` třídy.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-242">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="2b7f0-243">Nyní, budete muset aktualizovat `Main` volat `RunTeleprompter` místo `ShowTeleprompter`:</span><span class="sxs-lookup"><span data-stu-id="2b7f0-243">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="2b7f0-244">Závěr</span><span class="sxs-lookup"><span data-stu-id="2b7f0-244">Conclusion</span></span>

<span data-ttu-id="2b7f0-245">Tento kurz vám ukázal, že jste celou řadu funkcí kolem jazyka C# a knihovny .NET Core týkající se práce v konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-245">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="2b7f0-246">Můžete vytvořit tyto znalosti prozkoumat více o jazyce a třídy zavedené sem.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-246">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="2b7f0-247">Seznámili jste se základy a konzoly vstupně-výstupních operací, blokování a neblokující použití asynchronní programování založené na úlohách, prohlídka jazyka C# a jak jsou uspořádány programy C# a rozhraní příkazového řádku .NET Core a nástroje.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-247">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>

<span data-ttu-id="2b7f0-248">Další informace o vstupně-výstupní soubor najdete v tématu [souborové služby a vstupně-výstupní datový proud](../../standard/io/index.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-248">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="2b7f0-249">Další informace o asynchronní programovací model použili v tomto kurzu, najdete v článku [založený na úlohách asynchronní programování](../..//standard/parallel-programming/task-based-asynchronous-programming.md) tématu a [asynchronní programování](../async.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="2b7f0-249">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
