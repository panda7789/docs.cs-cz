---
title: Konzolová aplikace
description: V tomto kurzu se naučíte mnoho funkcí v jazyce C# a .NET Core.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 3ac4312ba5d6088826fdf151609f6693a265e5a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706465"
---
# <a name="console-application"></a><span data-ttu-id="0e82b-103">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="0e82b-103">Console Application</span></span>

<span data-ttu-id="0e82b-104">V tomto kurzu se naučíte mnoho funkcí v jazyce C# a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0e82b-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="0e82b-105">Získáte informace:</span><span class="sxs-lookup"><span data-stu-id="0e82b-105">You’ll learn:</span></span>

- <span data-ttu-id="0e82b-106">Základní informace o .NET Core rozhraní příkazového řádku (CLI)</span><span class="sxs-lookup"><span data-stu-id="0e82b-106">The basics of the .NET Core Command Line Interface (CLI)</span></span>
- <span data-ttu-id="0e82b-107">Struktura konzolovou aplikaci C#</span><span class="sxs-lookup"><span data-stu-id="0e82b-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="0e82b-108">Konzola vstupně-výstupních operací</span><span class="sxs-lookup"><span data-stu-id="0e82b-108">Console I/O</span></span>
- <span data-ttu-id="0e82b-109">Základní informace o souboru vstupně-výstupní operace rozhraní API v .NET</span><span class="sxs-lookup"><span data-stu-id="0e82b-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="0e82b-110">Základní informace o úkolově orientovanou asynchronní programování v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="0e82b-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="0e82b-111">Vytvoříte aplikaci, která čte textový soubor a vrátí obsah tohoto souboru text do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0e82b-111">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="0e82b-112">Výstup na konzole je tempem tak, aby odpovídala jeho nahlas.</span><span class="sxs-lookup"><span data-stu-id="0e82b-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="0e82b-113">Můžete urychlit nebo zpomalit rychlost stisknutím klávesy ' <' (méně než) nebo ">" (větší) klíče.</span><span class="sxs-lookup"><span data-stu-id="0e82b-113">You can speed up or slow down the pace by pressing the ‘<’ (less than) or ‘>’ (greater than) keys.</span></span>

<span data-ttu-id="0e82b-114">Existuje mnoho funkcí v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="0e82b-115">Vytvořme je jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="0e82b-115">Let’s build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0e82b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e82b-116">Prerequisites</span></span>

<span data-ttu-id="0e82b-117">Budete potřebovat k nastavení vašeho počítače ke spuštění .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0e82b-117">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="0e82b-118">Můžete najít pokyny k instalaci na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="0e82b-118">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="0e82b-119">Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0e82b-119">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="0e82b-120">Bude potřeba nainstalovat váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-120">You’ll need to install your favorite code editor.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="0e82b-121">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="0e82b-121">Create the Application</span></span>

<span data-ttu-id="0e82b-122">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e82b-122">The first step is to create a new application.</span></span> <span data-ttu-id="0e82b-123">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0e82b-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="0e82b-124">Ujistěte se, že do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="0e82b-124">Make that the current directory.</span></span> <span data-ttu-id="0e82b-125">Zadejte příkaz `dotnet new console` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0e82b-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="0e82b-126">Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".</span><span class="sxs-lookup"><span data-stu-id="0e82b-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="0e82b-127">Než začnete, úpravy, Podívejme se kroky ke spuštění jednoduché aplikace Hello World.</span><span class="sxs-lookup"><span data-stu-id="0e82b-127">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="0e82b-128">Po vytvoření aplikace, zadejte `dotnet restore` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0e82b-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="0e82b-129">Tento příkaz spustí proces obnovení balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="0e82b-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="0e82b-130">Správce balíčků NuGet je Správce balíčků .NET.</span><span class="sxs-lookup"><span data-stu-id="0e82b-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="0e82b-131">Tento příkaz načte všechny chybějící závislosti pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="0e82b-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="0e82b-132">Toto je nový projekt, závislosti nejsou v místě, tak při prvním spuštění se stáhnout .NET Core framework.</span><span class="sxs-lookup"><span data-stu-id="0e82b-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="0e82b-133">Po provedení tohoto kroku počáteční je pouze potřeba spustit `dotnet restore` při přidání nové závislé balíčky nebo aktualizace verze závislosti.</span><span class="sxs-lookup"><span data-stu-id="0e82b-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="0e82b-134">Po obnovení balíčků, spustíte `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="0e82b-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="0e82b-135">To spustí modul sestavení a vytvoří spustitelný soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e82b-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="0e82b-136">Nakonec spuštěním `dotnet run` ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e82b-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="0e82b-137">Kód jednoduché aplikace Hello World je všechny v souboru Program.cs.</span><span class="sxs-lookup"><span data-stu-id="0e82b-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="0e82b-138">Otevřete tento soubor v oblíbeném textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="0e82b-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="0e82b-139">Jsme naši první změny.</span><span class="sxs-lookup"><span data-stu-id="0e82b-139">We’re about to make our first changes.</span></span>
<span data-ttu-id="0e82b-140">V horní části souboru, najdete v článku using – příkaz:</span><span class="sxs-lookup"><span data-stu-id="0e82b-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="0e82b-141">Tento příkaz sděluje kompilátoru, že všechny typy `System` obor názvů jsou v oboru.</span><span class="sxs-lookup"><span data-stu-id="0e82b-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="0e82b-142">Jako objektově orientované jazyků, které jste mohli použít C# používá obory názvů pro uspořádání typů.</span><span class="sxs-lookup"><span data-stu-id="0e82b-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="0e82b-143">Tento program Hello World se nijak neliší.</span><span class="sxs-lookup"><span data-stu-id="0e82b-143">This Hello World program is no different.</span></span> <span data-ttu-id="0e82b-144">Uvidíte, že je program uzavřeny v oboru názvů s názvem na základě názvu aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="0e82b-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="0e82b-145">Pro účely tohoto kurzu Změníme název oboru názvů `TeleprompterConsole`:</span><span class="sxs-lookup"><span data-stu-id="0e82b-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="0e82b-146">Čtení a zobrazování souboru</span><span class="sxs-lookup"><span data-stu-id="0e82b-146">Reading and Echoing the File</span></span>

<span data-ttu-id="0e82b-147">První funkce přidání je schopnost čtení z textového souboru a zobrazí tento text do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0e82b-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="0e82b-148">Nejprve přidáme do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="0e82b-148">First, let’s add a text file.</span></span> <span data-ttu-id="0e82b-149">Kopírovat [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) soubor z úložiště GitHub pro tuto [ukázka](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="0e82b-150">To bude sloužit jako skript pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0e82b-150">This will serve as the script for your application.</span></span> <span data-ttu-id="0e82b-151">Pokud chcete informace o tom, jak stáhnout ukázkovou aplikaci pro toto téma, postupujte podle pokynů v [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) tématu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="0e82b-152">V dalším kroku přidejte následující metodu do vaší `Program` třídy (přímo pod `Main` metoda):</span><span class="sxs-lookup"><span data-stu-id="0e82b-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

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

<span data-ttu-id="0e82b-153">Tato metoda používá typy z dva nové obory názvů.</span><span class="sxs-lookup"><span data-stu-id="0e82b-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="0e82b-154">Pro tuto kompilaci je potřeba na začátek souboru přidejte následující dva řádky:</span><span class="sxs-lookup"><span data-stu-id="0e82b-154">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="0e82b-155"><xref:System.Collections.Generic.IEnumerable%601> Rozhraní je definováno v <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0e82b-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="0e82b-156"><xref:System.IO.File> Třída je definována v <xref:System.IO> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0e82b-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="0e82b-157">Tato metoda je speciální typ jazyka C# metodu s názvem *metody iterátoru*.</span><span class="sxs-lookup"><span data-stu-id="0e82b-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="0e82b-158">Enumerátor metody vrací sekvence, které jsou vyhodnocovány laxně.</span><span class="sxs-lookup"><span data-stu-id="0e82b-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="0e82b-159">To znamená, že každá položka v sekvenci se vygeneruje, jak to požadoval kód využívání sekvence.</span><span class="sxs-lookup"><span data-stu-id="0e82b-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="0e82b-160">Enumerátor metody jsou metody, které obsahují jeden nebo více [ `yield return` ](../language-reference/keywords/yield.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="0e82b-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="0e82b-161">Objekt vrácený rutinou `ReadFrom` metoda obsahuje kód pro vygenerování každé položky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="0e82b-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="0e82b-162">V tomto příkladu, který zahrnuje čtení Zalamovat text ze zdrojového souboru a vrátí tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="0e82b-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="0e82b-163">Pokaždé, když volající kód požadavků na další položku z řady, kód načte Zalamovat text ze souboru a vrátí jej.</span><span class="sxs-lookup"><span data-stu-id="0e82b-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="0e82b-164">Pokud soubor je zcela čtení, sekvence označuje, že neexistují žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="0e82b-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="0e82b-165">Existují dva další C# prvky syntaxe, které mohou být pro vás nová.</span><span class="sxs-lookup"><span data-stu-id="0e82b-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="0e82b-166">[ `using` ](../language-reference/keywords/using-statement.md) Příkaz v této metodě spravuje vyčištění prostředků.</span><span class="sxs-lookup"><span data-stu-id="0e82b-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="0e82b-167">Proměnné, která je inicializována v `using` – příkaz (`reader`, v tomto příkladu), musí implementovat <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0e82b-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="0e82b-168">Toto rozhraní definuje jedinou metodu `Dispose`, která by měla být volána při prostředku by měly být vydány.</span><span class="sxs-lookup"><span data-stu-id="0e82b-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="0e82b-169">Kompilátor generuje toto volání, když spuštění dosáhne složené závorce `using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="0e82b-170">Kód generovaný kompilátorem zajistí, že prostředek je uvolněn i v případě, že dojde k výjimce z kódu v bloku určené na pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="0e82b-171">`reader` Proměnné definované `var` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0e82b-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="0e82b-172">[`var`](../language-reference/keywords/var.md) definuje *implicitně typované lokální proměnné*.</span><span class="sxs-lookup"><span data-stu-id="0e82b-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="0e82b-173">To znamená, že typ proměnné je určen podle typu za kompilace objektu přiřazena k proměnné.</span><span class="sxs-lookup"><span data-stu-id="0e82b-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="0e82b-174">Tady, který je návratová hodnota z <xref:System.IO.File.OpenText(System.String)> metodu, která je <xref:System.IO.StreamReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="0e82b-175">Teď Pojďme vyplnit kód ke čtení souboru v `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="0e82b-175">Now, let’s fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="0e82b-176">Spusťte program (pomocí `dotnet run`) a zobrazí se každý jednotlivý řádek tisknout do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0e82b-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="0e82b-177">Přidávání zpoždění a formátování výstupu</span><span class="sxs-lookup"><span data-stu-id="0e82b-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="0e82b-178">Je nutné se zobrazí příliš rychle k nahlas.</span><span class="sxs-lookup"><span data-stu-id="0e82b-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="0e82b-179">Teď budete muset přidat zpoždění ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="0e82b-180">Když začnete, budete mít sestavování, některé základní kód, který umožňuje asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="0e82b-180">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="0e82b-181">První postup se postupujte podle několika antimodely.</span><span class="sxs-lookup"><span data-stu-id="0e82b-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="0e82b-182">Antimodely jsou uvedli v komentářích jako přidat kód a kód bude aktualizován v dalších krocích.</span><span class="sxs-lookup"><span data-stu-id="0e82b-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="0e82b-183">Existují dva kroky k této sekci.</span><span class="sxs-lookup"><span data-stu-id="0e82b-183">There are two steps to this section.</span></span> <span data-ttu-id="0e82b-184">Nejprve budete aktualizovat metodu iterátoru k vrácení jednoho slova místo celé řádky.</span><span class="sxs-lookup"><span data-stu-id="0e82b-184">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="0e82b-185">Který se provádí s těmito úpravami.</span><span class="sxs-lookup"><span data-stu-id="0e82b-185">That’s done with these modifications.</span></span> <span data-ttu-id="0e82b-186">Nahradit `yield return line;` příkaz následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="0e82b-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="0e82b-187">Dále je třeba upravit, jak využívat řádky souboru a přidání zpoždění po zápisu všech slov.</span><span class="sxs-lookup"><span data-stu-id="0e82b-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="0e82b-188">Nahradit `Console.WriteLine(line)` výroky `Main` metodu s následující blok:</span><span class="sxs-lookup"><span data-stu-id="0e82b-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

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

<span data-ttu-id="0e82b-189"><xref:System.Threading.Tasks.Task> Hodina může začít <xref:System.Threading.Tasks> obor názvů, takže je třeba ho přidat `using` příkazu v horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="0e82b-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="0e82b-190">Spusťte ukázku a podívejte se ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-190">Run the sample, and check the output.</span></span> <span data-ttu-id="0e82b-191">Teď je vytištěna každý jednoho slova, za nímž následuje zpožděním 200 ms.</span><span class="sxs-lookup"><span data-stu-id="0e82b-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="0e82b-192">Ale zobrazené výstup ukazuje některé problémy, protože text souboru zdroje má několik řádků, které mají více než 80 znaků bez konce řádku.</span><span class="sxs-lookup"><span data-stu-id="0e82b-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="0e82b-193">Může být obtížné číst, zatímco je posouvání.</span><span class="sxs-lookup"><span data-stu-id="0e82b-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="0e82b-194">To je snadno to vyřešíme.</span><span class="sxs-lookup"><span data-stu-id="0e82b-194">That’s easy to fix.</span></span> <span data-ttu-id="0e82b-195">Stejně budete udržovat přehled o délce každý řádek a generovat nový řádek pokaždé, když se dosáhne určité prahové hodnoty délky řádku.</span><span class="sxs-lookup"><span data-stu-id="0e82b-195">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="0e82b-196">Deklarujte místní proměnné po deklaraci `words` v `ReadFrom` metodu, která obsahuje délky řádku:</span><span class="sxs-lookup"><span data-stu-id="0e82b-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="0e82b-197">Potom přidejte následující kód za `yield return word + " ";` – příkaz (před pravou složenou závorku):</span><span class="sxs-lookup"><span data-stu-id="0e82b-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="0e82b-198">Spusťte ukázku a budete moct rychlost čtení na její předem nakonfigurovaná tempu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-198">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="0e82b-199">Úloh s modifikátorem Async</span><span class="sxs-lookup"><span data-stu-id="0e82b-199">Async Tasks</span></span>

<span data-ttu-id="0e82b-200">V tomto posledním kroku budete přidejte kód pro zápis výstupu asynchronně v jednom úkolu, při vstupu od uživatele, pokud je to vyžadováno pro urychlení nebo zpomalit zobrazení textu také běží jiné úlohy ke čtení nebo úplně zastavit zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-200">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="0e82b-201">Tato akce nemá několika krocích a do konce, budete mít všechny aktualizace, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="0e82b-201">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="0e82b-202">Prvním krokem je vytvoření asynchronní <xref:System.Threading.Tasks.Task> vrací metoda, která představuje kód zatím jste vytvořili pro čtení a zobrazení souboru.</span><span class="sxs-lookup"><span data-stu-id="0e82b-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="0e82b-203">Přidejte tuto metodu za účelem vaše `Program` třídy (je převzata z těla vaše `Main` metoda):</span><span class="sxs-lookup"><span data-stu-id="0e82b-203">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

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

<span data-ttu-id="0e82b-204">Můžete si všimnout dvou změn.</span><span class="sxs-lookup"><span data-stu-id="0e82b-204">You’ll notice two changes.</span></span> <span data-ttu-id="0e82b-205">První v těle metody, namísto volání metody <xref:System.Threading.Tasks.Task.Wait> synchronně čekat na dokončení úlohy, používá tato verze `await` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0e82b-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="0e82b-206">Abyste to mohli udělat, budete muset přidat `async` modifikátor do podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="0e82b-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="0e82b-207">Tato metoda vrátí hodnotu `Task`.</span><span class="sxs-lookup"><span data-stu-id="0e82b-207">This method returns a `Task`.</span></span> <span data-ttu-id="0e82b-208">Všimněte si, že neexistují žádné návratové příkazy, které vracejí `Task` objektu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="0e82b-209">Místo toho, který `Task` kódem, vygeneruje kompilátor při použití je vytvořen objekt `await` operátor.</span><span class="sxs-lookup"><span data-stu-id="0e82b-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="0e82b-210">Představte si, že tato metoda vrátí při dosažení `await`.</span><span class="sxs-lookup"><span data-stu-id="0e82b-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="0e82b-211">Vrácený `Task` označuje, že práce nebyla dokončena.</span><span class="sxs-lookup"><span data-stu-id="0e82b-211">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="0e82b-212">Metoda obnoví při dokončení očekávané úlohy.</span><span class="sxs-lookup"><span data-stu-id="0e82b-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="0e82b-213">Když po provedení do konce, vrácený `Task` označuje, že je dokončeno.</span><span class="sxs-lookup"><span data-stu-id="0e82b-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="0e82b-214">Volání kódu můžete sledovat, která vrátila `Task` k určení, kdy bude uvolňování dokončeno.</span><span class="sxs-lookup"><span data-stu-id="0e82b-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="0e82b-215">Tato nová metoda může volat v vaše `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="0e82b-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="0e82b-216">Tady v `Main`, kód synchronně čekání.</span><span class="sxs-lookup"><span data-stu-id="0e82b-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="0e82b-217">Měli byste použít `await` operátor místo synchronním čekání, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="0e82b-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="0e82b-218">Ale v konzolové aplikaci `Main` metodu, nelze použít `await` operátor.</span><span class="sxs-lookup"><span data-stu-id="0e82b-218">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="0e82b-219">Bude výsledkem ukončení aplikace předtím, než se dokončí všechny úlohy.</span><span class="sxs-lookup"><span data-stu-id="0e82b-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="0e82b-220">Pokud používáte C# 7.1 nebo novější, můžete vytvořit konzolové aplikace s [ `async` `Main` metoda](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="0e82b-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="0e82b-221">Dále je třeba zadat druhý asynchronní metodu ke čtení z konzoly a podívejte se ' <' (méně než), ">" (větší) a "X" nebo "x" klíče.</span><span class="sxs-lookup"><span data-stu-id="0e82b-221">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ (less than), ‘>’ (greater than) and ‘X’ or ‘x’ keys.</span></span> <span data-ttu-id="0e82b-222">Tady je pro tuto úlohu, které přidáte metodu:</span><span class="sxs-lookup"><span data-stu-id="0e82b-222">Here’s the method you add for that task:</span></span>

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
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="0e82b-223">Tím se vytvoří pro reprezentaci výrazu lambda <xref:System.Action> delegáta, který čte klíč z konzoly a upravuje místní proměnnou představující zpoždění, když uživatel stiskne ' <' (méně než) nebo ">" (větší) klíče.</span><span class="sxs-lookup"><span data-stu-id="0e82b-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ (less than) or ‘>’ (greater than) keys.</span></span> <span data-ttu-id="0e82b-224">Metody delegáta dokončí, když uživatel stiskne "X" nebo "x" klíče, které uživateli umožní zastavit zobrazení textu v každém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="0e82b-224">The delegate method finishes when user presses the ‘X’ or ‘x’  keys, which allow the user to stop the text display at any time.</span></span>
<span data-ttu-id="0e82b-225">Tato metoda používá <xref:System.Console.ReadKey> blokovat a čekat, uživatel ke stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="0e82b-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="0e82b-226">Dokončete tuto funkci je potřeba vytvořit nový `async Task` vrací metoda, která spustí oba z těchto úloh (`GetInput` a `ShowTeleprompter`) a také spravuje sdílených dat mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="0e82b-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="0e82b-227">Je čas vytvořit třídu, která dokáže zpracovat sdílených dat mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="0e82b-227">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="0e82b-228">Tato třída obsahuje dvě veřejné vlastnosti: zpoždění a příznak `Done` k označení zcela čtení souboru:</span><span class="sxs-lookup"><span data-stu-id="0e82b-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            DelayInMilliseconds = newDelay;
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="0e82b-229">Vložit tuto třídu do nového souboru a použijte tuto třídu v `TeleprompterConsole` obor názvů, jak je znázorněno výše.</span><span class="sxs-lookup"><span data-stu-id="0e82b-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="0e82b-230">Také budete muset přidat `using static` příkaz tak, aby můžete odkazovat `Min` a `Max` metody bez nadřazené třídy nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0e82b-230">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="0e82b-231">A [ `using static` ](../language-reference/keywords/using-static.md) příkaz importuje metody z jedné třídy.</span><span class="sxs-lookup"><span data-stu-id="0e82b-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="0e82b-232">To je rozdíl od s `using` do této chvíle používat příkazy, které jste importovali všechny třídy z oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0e82b-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="0e82b-233">V dalším kroku je potřeba aktualizovat `ShowTeleprompter` a `GetInput` metod používaných nové `config` objektu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-233">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="0e82b-234">Zápis jeden konečný `Task` vrácení `async` metoda obě úlohy spuštění a ukončení po dokončení první úlohy:</span><span class="sxs-lookup"><span data-stu-id="0e82b-234">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="0e82b-235">Je zde jeden novou metodu <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> volání.</span><span class="sxs-lookup"><span data-stu-id="0e82b-235">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="0e82b-236">Který vytváří `Task` , který dokončí, jakmile se dokončí všechny úlohy ve svém seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="0e82b-236">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="0e82b-237">Dále je třeba oba aktualizovat `ShowTeleprompter` a `GetInput` metod používaných `config` objekt pro zpoždění:</span><span class="sxs-lookup"><span data-stu-id="0e82b-237">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
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
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
                config.SetDone();
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="0e82b-238">Tato nová verze `ShowTeleprompter` volá novou metodu `TeleprompterConfig` třídy.</span><span class="sxs-lookup"><span data-stu-id="0e82b-238">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="0e82b-239">Teď, budete muset aktualizovat `Main` volat `RunTeleprompter` místo `ShowTeleprompter`:</span><span class="sxs-lookup"><span data-stu-id="0e82b-239">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="0e82b-240">Závěr</span><span class="sxs-lookup"><span data-stu-id="0e82b-240">Conclusion</span></span>

<span data-ttu-id="0e82b-241">Tento kurz vám ukázal, že jste celou řadu funkcí jazyka C# a knihovny .NET Core týkající se práce v konzolových aplikacích.</span><span class="sxs-lookup"><span data-stu-id="0e82b-241">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="0e82b-242">Můžete sestavit s bližším prozkoumáváním jazyka a tříd sem zavedl tyto znalosti.</span><span class="sxs-lookup"><span data-stu-id="0e82b-242">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="0e82b-243">Jste se seznámili se základy souborové služby a konzoly vstupně-výstupních operací, blokujících a neblokujících použití asynchronní programování založené na úlohách, prohlídka jazyka C# a jak jsou uspořádány programy jazyka C# a rozhraní příkazového řádku .NET Core a nástroje.</span><span class="sxs-lookup"><span data-stu-id="0e82b-243">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>

<span data-ttu-id="0e82b-244">Další informace o vstupně-výstupní operace souboru, najdete v článku [Souborová služba a vstupně-výstupní operace Stream](../../standard/io/index.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-244">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="0e82b-245">Další informace o asynchronní programovací model použitý v tomto kurzu, najdete v článku [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) tématu a [asynchronní programování](../async.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="0e82b-245">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
