---
title: Konzolová aplikace
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v jazyce C#.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: dbe64fe0a01ddab9e7a3ad0a9118b3fe59fba8aa
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656980"
---
# <a name="console-app"></a><span data-ttu-id="57ee3-103">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="57ee3-103">Console app</span></span>

<span data-ttu-id="57ee3-104">V tomto kurzu se naučíte řadou funkcí v .NET Core a v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="57ee3-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="57ee3-105">Naučíte se:</span><span class="sxs-lookup"><span data-stu-id="57ee3-105">You'll learn:</span></span>

- <span data-ttu-id="57ee3-106">Základy .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="57ee3-106">The basics of the .NET Core CLI</span></span>
- <span data-ttu-id="57ee3-107">Struktura konzolové aplikace v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="57ee3-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="57ee3-108">I/O konzoly</span><span class="sxs-lookup"><span data-stu-id="57ee3-108">Console I/O</span></span>
- <span data-ttu-id="57ee3-109">Základy vstupně-výstupních rozhraní API souborů v .NET</span><span class="sxs-lookup"><span data-stu-id="57ee3-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="57ee3-110">Základy asynchronního programování založeného na úlohách v .NET</span><span class="sxs-lookup"><span data-stu-id="57ee3-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="57ee3-111">Vytvoříte aplikaci, která přečte textový soubor, a vrátí obsah tohoto textového souboru do konzoly.</span><span class="sxs-lookup"><span data-stu-id="57ee3-111">You'll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="57ee3-112">Výstup do konzoly je TEMP, aby odpovídal čtení, které nahlasuje.</span><span class="sxs-lookup"><span data-stu-id="57ee3-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="57ee3-113">Tempo můžete zrychlit nebo zpomalit stisknutím klávesy < (menší než) nebo > (větší než).</span><span class="sxs-lookup"><span data-stu-id="57ee3-113">You can speed up or slow down the pace by pressing the '<' (less than) or '>' (greater than) keys.</span></span>

<span data-ttu-id="57ee3-114">V tomto kurzu máte spoustu funkcí.</span><span class="sxs-lookup"><span data-stu-id="57ee3-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="57ee3-115">Pojďme je sestavit jednou po jednom.</span><span class="sxs-lookup"><span data-stu-id="57ee3-115">Let's build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="57ee3-116">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="57ee3-116">Prerequisites</span></span>

- <span data-ttu-id="57ee3-117">Nastavte počítač tak, aby běžel .NET Core.</span><span class="sxs-lookup"><span data-stu-id="57ee3-117">Set up your machine to run .NET Core.</span></span> <span data-ttu-id="57ee3-118">Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="57ee3-118">You can find the installation instructions on the [.NET Core downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="57ee3-119">Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="57ee3-119">You can run this application on Windows, Linux, macOS, or in a Docker container.</span></span>

- <span data-ttu-id="57ee3-120">Nainstalujte svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="57ee3-120">Install your favorite code editor.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="57ee3-121">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="57ee3-121">Create the app</span></span>

<span data-ttu-id="57ee3-122">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="57ee3-122">The first step is to create a new application.</span></span> <span data-ttu-id="57ee3-123">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="57ee3-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="57ee3-124">Zajistěte, aby byl aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="57ee3-124">Make that the current directory.</span></span> <span data-ttu-id="57ee3-125">Zadejte příkaz `dotnet new console` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="57ee3-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="57ee3-126">Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="57ee3-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="57ee3-127">Než začnete s úpravami, Projděte si postup spuštění jednoduché aplikace Hello World.</span><span class="sxs-lookup"><span data-stu-id="57ee3-127">Before you start making modifications, let's go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="57ee3-128">Po vytvoření aplikace zadejte do `dotnet restore` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="57ee3-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="57ee3-129">Tento příkaz spustí proces obnovení balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="57ee3-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="57ee3-130">NuGet je správce balíčků .NET.</span><span class="sxs-lookup"><span data-stu-id="57ee3-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="57ee3-131">Tento příkaz stáhne všechny chybějící závislosti pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="57ee3-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="57ee3-132">Vzhledem k tomu, že se jedná o nový projekt, není zavedena žádná závislost, takže první spuštění stáhne rozhraní .NET Core Framework.</span><span class="sxs-lookup"><span data-stu-id="57ee3-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="57ee3-133">Po provedení tohoto počátečního kroku budete muset spustit jenom `dotnet restore` při přidávání nových závislých balíčků nebo při aktualizaci verzí jakékoli závislosti.</span><span class="sxs-lookup"><span data-stu-id="57ee3-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="57ee3-134">Po obnovení balíčků spustíte `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="57ee3-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="57ee3-135">Tím se spustí sestavovací modul a vytvoří se spustitelný soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="57ee3-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="57ee3-136">Nakonec můžete spustit `dotnet run` aplikaci.</span><span class="sxs-lookup"><span data-stu-id="57ee3-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="57ee3-137">Jednoduchý Hello World kód aplikace je v Program.cs.</span><span class="sxs-lookup"><span data-stu-id="57ee3-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="57ee3-138">Otevřete tento soubor ve svém oblíbeném textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="57ee3-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="57ee3-139">Chystáme se udělat první změny.</span><span class="sxs-lookup"><span data-stu-id="57ee3-139">We're about to make our first changes.</span></span> <span data-ttu-id="57ee3-140">V horní části souboru se podívejte na příkaz using:</span><span class="sxs-lookup"><span data-stu-id="57ee3-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="57ee3-141">Tento příkaz instruuje kompilátor, že všechny typy z `System` oboru názvů jsou v oboru.</span><span class="sxs-lookup"><span data-stu-id="57ee3-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="57ee3-142">Podobně jako u jiných objektů orientovaných na objekty, které jste pravděpodobně použili, jazyk C# používá obory názvů k uspořádání typů.</span><span class="sxs-lookup"><span data-stu-id="57ee3-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="57ee3-143">Tento program Hello World není jiný.</span><span class="sxs-lookup"><span data-stu-id="57ee3-143">This Hello World program is no different.</span></span> <span data-ttu-id="57ee3-144">Můžete vidět, že program je uzavřen v oboru názvů s názvem na základě názvu aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="57ee3-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="57ee3-145">Pro účely tohoto kurzu změňte název oboru názvů na `TeleprompterConsole` :</span><span class="sxs-lookup"><span data-stu-id="57ee3-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="57ee3-146">Čtení a vracení souboru se souborem</span><span class="sxs-lookup"><span data-stu-id="57ee3-146">Reading and Echoing the File</span></span>

<span data-ttu-id="57ee3-147">První funkcí, kterou je třeba přidat, je možnost číst textový soubor a zobrazit celý tento text v konzole.</span><span class="sxs-lookup"><span data-stu-id="57ee3-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="57ee3-148">Nejprve přidáme textový soubor.</span><span class="sxs-lookup"><span data-stu-id="57ee3-148">First, let's add a text file.</span></span> <span data-ttu-id="57ee3-149">Zkopírujte soubor [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z úložiště GitHub pro tuto [ukázku](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="57ee3-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="57ee3-150">Tato akce bude sloužit jako skript pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="57ee3-150">This will serve as the script for your application.</span></span> <span data-ttu-id="57ee3-151">Pokud chcete získat informace o tom, jak stáhnout ukázkovou aplikaci pro toto téma, přečtěte si pokyny v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#view-and-download-samples) .</span><span class="sxs-lookup"><span data-stu-id="57ee3-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples) topic.</span></span>

<span data-ttu-id="57ee3-152">Dále do třídy přidejte následující metodu `Program` (hned pod `Main` metodu):</span><span class="sxs-lookup"><span data-stu-id="57ee3-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

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

<span data-ttu-id="57ee3-153">Tato metoda používá typy ze dvou nových oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="57ee3-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="57ee3-154">Pro zkompilování je třeba do horní části souboru přidat následující dva řádky:</span><span class="sxs-lookup"><span data-stu-id="57ee3-154">For this to compile you'll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="57ee3-155"><xref:System.Collections.Generic.IEnumerable%601>Rozhraní je definováno v <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="57ee3-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="57ee3-156"><xref:System.IO.File>Třída je definována v <xref:System.IO> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="57ee3-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="57ee3-157">Tato metoda je speciální typ metody jazyka C# s názvem *Metoda iterátoru*.</span><span class="sxs-lookup"><span data-stu-id="57ee3-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="57ee3-158">Metody enumerátoru vracejí sekvence, které jsou vyhodnocovány laxně vytvářená.</span><span class="sxs-lookup"><span data-stu-id="57ee3-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="57ee3-159">To znamená, že každá položka v sekvenci je vygenerována tak, jak je požadována kódem, který spotřebovává sekvenci.</span><span class="sxs-lookup"><span data-stu-id="57ee3-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="57ee3-160">Metody enumerátoru jsou metody, které obsahují jeden nebo více [`yield return`](../language-reference/keywords/yield.md) příkazů.</span><span class="sxs-lookup"><span data-stu-id="57ee3-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="57ee3-161">Objekt vrácený `ReadFrom` metodou obsahuje kód pro vygenerování každé položky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="57ee3-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="57ee3-162">V tomto příkladu zahrnuje čtení dalšího řádku textu ze zdrojového souboru a vrácení tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="57ee3-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="57ee3-163">Pokaždé, když volající kód požádá o další položku z sekvence, kód přečte další řádek textu ze souboru a vrátí jej.</span><span class="sxs-lookup"><span data-stu-id="57ee3-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="57ee3-164">Když je soubor kompletně načtený, sekvence indikuje, že nejsou k dispozici žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="57ee3-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="57ee3-165">Existují dva další prvky syntaxe jazyka C#, které mohou být pro vás nové.</span><span class="sxs-lookup"><span data-stu-id="57ee3-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="57ee3-166">[`using`](../language-reference/keywords/using-statement.md)Příkaz v této metodě spravuje čištění prostředků.</span><span class="sxs-lookup"><span data-stu-id="57ee3-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="57ee3-167">Proměnná, která je inicializována v `using` příkazu ( `reader` v tomto příkladu), musí implementovat <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="57ee3-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="57ee3-168">Toto rozhraní definuje jedinou metodu, `Dispose` která by měla být volána, když má být prostředek uvolněn.</span><span class="sxs-lookup"><span data-stu-id="57ee3-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="57ee3-169">Kompilátor vygeneruje toto volání, když provádění dosáhne uzavírací závorce `using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="57ee3-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="57ee3-170">Kód generovaný kompilátorem zajišťuje uvolnění prostředku i v případě, že je vyvolána výjimka z kódu v bloku definovaném příkazem using.</span><span class="sxs-lookup"><span data-stu-id="57ee3-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="57ee3-171">`reader`Proměnná je definována pomocí `var` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="57ee3-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="57ee3-172">[`var`](../language-reference/keywords/var.md) definuje *implicitní typovou lokální proměnnou*.</span><span class="sxs-lookup"><span data-stu-id="57ee3-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="57ee3-173">To znamená, že typ proměnné je určen typem pro čas kompilace objektu přiřazeného k proměnné.</span><span class="sxs-lookup"><span data-stu-id="57ee3-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="57ee3-174">Zde je návratová hodnota z <xref:System.IO.File.OpenText(System.String)> metody, což je <xref:System.IO.StreamReader> objekt.</span><span class="sxs-lookup"><span data-stu-id="57ee3-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="57ee3-175">Teď naplníme kód, abychom si mohli přečíst soubor v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="57ee3-175">Now, let's fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="57ee3-176">Spusťte program (pomocí `dotnet run` ) a můžete zobrazit všechny vytištěné řádky do konzoly.</span><span class="sxs-lookup"><span data-stu-id="57ee3-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="57ee3-177">Přidání zpoždění a formátování výstupu</span><span class="sxs-lookup"><span data-stu-id="57ee3-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="57ee3-178">To, co je ještě daleko příliš rychlé pro čtení nahlasu.</span><span class="sxs-lookup"><span data-stu-id="57ee3-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="57ee3-179">Nyní je třeba přidat prodlevy ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="57ee3-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="57ee3-180">Při spuštění budete tvořit část základního kódu, který umožňuje asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="57ee3-180">As you start, you'll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="57ee3-181">Tyto první kroky se ale budou řídit několika anti vzory.</span><span class="sxs-lookup"><span data-stu-id="57ee3-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="57ee3-182">Anti-patterny jsou v komentářích při přidávání kódu ukázány a kód se aktualizuje v pozdějších krocích.</span><span class="sxs-lookup"><span data-stu-id="57ee3-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="57ee3-183">Tato část obsahuje dva kroky.</span><span class="sxs-lookup"><span data-stu-id="57ee3-183">There are two steps to this section.</span></span> <span data-ttu-id="57ee3-184">Nejprve aktualizujte metodu iterátoru tak, aby vracela jednoduchá slova namísto celých řádků.</span><span class="sxs-lookup"><span data-stu-id="57ee3-184">First, you'll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="57ee3-185">To se provádí s těmito úpravami.</span><span class="sxs-lookup"><span data-stu-id="57ee3-185">That's done with these modifications.</span></span> <span data-ttu-id="57ee3-186">Nahraďte `yield return line;` příkaz následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="57ee3-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="57ee3-187">Dále je nutné upravit způsob, jakým se vybírají řádky souboru, a po zápisu každého slova přidat prodlevu.</span><span class="sxs-lookup"><span data-stu-id="57ee3-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="57ee3-188">Nahraďte `Console.WriteLine(line)` příkaz v `Main` metodě následujícím blokem:</span><span class="sxs-lookup"><span data-stu-id="57ee3-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

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

<span data-ttu-id="57ee3-189"><xref:System.Threading.Tasks.Task>Třída je v <xref:System.Threading.Tasks> oboru názvů, takže je nutné přidat tento `using` příkaz na začátek souboru:</span><span class="sxs-lookup"><span data-stu-id="57ee3-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="57ee3-190">Spusťte ukázku a podívejte se na výstup.</span><span class="sxs-lookup"><span data-stu-id="57ee3-190">Run the sample, and check the output.</span></span> <span data-ttu-id="57ee3-191">Nyní se vytisknou všechna jednotlivá slova následovaná zpožděním 200 ms.</span><span class="sxs-lookup"><span data-stu-id="57ee3-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="57ee3-192">Zobrazený výstup však ukazuje některé problémy, protože zdrojový textový soubor obsahuje několik řádků, které mají více než 80 znaků bez zalomení řádku.</span><span class="sxs-lookup"><span data-stu-id="57ee3-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="57ee3-193">To může být obtížné číst, zatímco se posunuje.</span><span class="sxs-lookup"><span data-stu-id="57ee3-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="57ee3-194">To se dá snadno opravit.</span><span class="sxs-lookup"><span data-stu-id="57ee3-194">That's easy to fix.</span></span> <span data-ttu-id="57ee3-195">Pouze budete sledovat délku každého řádku a vygenerujete nový řádek vždy, když délka řádku dosáhne určité prahové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="57ee3-195">You'll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="57ee3-196">Deklarovat místní proměnnou za deklarací `words` v `ReadFrom` metodě, která obsahuje délku řádku:</span><span class="sxs-lookup"><span data-stu-id="57ee3-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="57ee3-197">Poté přidejte následující kód za `yield return word + " ";` příkaz (před pravou závorku):</span><span class="sxs-lookup"><span data-stu-id="57ee3-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="57ee3-198">Spusťte ukázku a budete moct číst nahlas v jeho předem nakonfigurovaném tempu.</span><span class="sxs-lookup"><span data-stu-id="57ee3-198">Run the sample, and you'll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="57ee3-199">Asynchronní úlohy</span><span class="sxs-lookup"><span data-stu-id="57ee3-199">Async Tasks</span></span>

<span data-ttu-id="57ee3-200">V tomto posledním kroku přidáte kód pro asynchronní zápis výstupu do jedné úlohy a zároveň spustíte jiný úkol pro čtení vstupu od uživatele, pokud chtějí zrychlit nebo zpomalit zobrazení textu, nebo ukončit zobrazování textu.</span><span class="sxs-lookup"><span data-stu-id="57ee3-200">In this final step, you'll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="57ee3-201">V tomto případě je to několik kroků a na konci budete mít k dispozici všechny potřebné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="57ee3-201">This has a few steps in it and by the end, you'll have all the updates that you need.</span></span> <span data-ttu-id="57ee3-202">Prvním krokem je vytvořit asynchronní <xref:System.Threading.Tasks.Task> návratovou metodu, která představuje kód, který jste dosud vytvořili pro čtení a zobrazení souboru.</span><span class="sxs-lookup"><span data-stu-id="57ee3-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you've created so far to read and display the file.</span></span>

<span data-ttu-id="57ee3-203">Přidejte tuto metodu do `Program` třídy (ta je pořízena z těla vaší `Main` metody):</span><span class="sxs-lookup"><span data-stu-id="57ee3-203">Add this method to your `Program` class (it's taken from the body of your `Main` method):</span></span>

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

<span data-ttu-id="57ee3-204">Všimnete si dvou změn.</span><span class="sxs-lookup"><span data-stu-id="57ee3-204">You'll notice two changes.</span></span> <span data-ttu-id="57ee3-205">Nejprve v těle metody namísto volání <xref:System.Threading.Tasks.Task.Wait> synchronního čekání na dokončení úlohy používá tato verze `await` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="57ee3-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="57ee3-206">K tomu je nutné přidat `async` modifikátor do podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="57ee3-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="57ee3-207">Tato metoda vrátí `Task` .</span><span class="sxs-lookup"><span data-stu-id="57ee3-207">This method returns a `Task`.</span></span> <span data-ttu-id="57ee3-208">Všimněte si, že neexistují žádné návratové příkazy, které vracejí `Task` objekt.</span><span class="sxs-lookup"><span data-stu-id="57ee3-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="57ee3-209">Místo toho `Task` je objekt vytvořen pomocí kódu, který kompilátor generuje při použití `await` operátoru.</span><span class="sxs-lookup"><span data-stu-id="57ee3-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="57ee3-210">Můžete si představit, že tato metoda vrátí, když dosáhne `await` .</span><span class="sxs-lookup"><span data-stu-id="57ee3-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="57ee3-211">Vrácená zpráva `Task` znamená, že práce nebyla dokončena.</span><span class="sxs-lookup"><span data-stu-id="57ee3-211">The returned `Task` indicates that the work has not completed.</span></span> <span data-ttu-id="57ee3-212">Metoda pokračuje, až se dokončí očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="57ee3-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="57ee3-213">Když se provede dokončení, vrátí se na to `Task` , že se dokončilo.</span><span class="sxs-lookup"><span data-stu-id="57ee3-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="57ee3-214">Volání kódu může sledovat, že bylo vráceno, aby bylo možné `Task` určit, kdy bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="57ee3-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="57ee3-215">Tuto novou metodu můžete zavolat v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="57ee3-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="57ee3-216">Zde v nástroji `Main` kód asynchronně čeká.</span><span class="sxs-lookup"><span data-stu-id="57ee3-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="57ee3-217">`await`Místo synchronního čekání, pokud je to možné, byste měli použít operátor.</span><span class="sxs-lookup"><span data-stu-id="57ee3-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="57ee3-218">Ale v metodě konzolové aplikace `Main` nemůžete použít `await` operátor.</span><span class="sxs-lookup"><span data-stu-id="57ee3-218">But, in a console application's `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="57ee3-219">To by vedlo k ukončení aplikace před dokončením všech úloh.</span><span class="sxs-lookup"><span data-stu-id="57ee3-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="57ee3-220">Používáte-li C# 7,1 nebo novější, můžete vytvořit konzolové aplikace s [ `async` `Main` metodou](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="57ee3-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="57ee3-221">Dále je potřeba napsat druhou asynchronní metodu pro čtení z konzoly a sledovat "<" (menší než), ">" (větší než) a "X" nebo "klíče" x ".</span><span class="sxs-lookup"><span data-stu-id="57ee3-221">Next, you need to write the second asynchronous method to read from the Console and watch for the '<' (less than), '>' (greater than) and 'X' or 'x' keys.</span></span> <span data-ttu-id="57ee3-222">Zde je metoda, kterou přidáte pro tuto úlohu:</span><span class="sxs-lookup"><span data-stu-id="57ee3-222">Here's the method you add for that task:</span></span>

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

<span data-ttu-id="57ee3-223">Tím se vytvoří výraz lambda <xref:System.Action> , který reprezentuje delegáta, který přečte klíč z konzoly, a upraví místní proměnnou představující zpoždění, když uživatel stiskne klávesu ' < ' (menší než) nebo ' > ' (větší než).</span><span class="sxs-lookup"><span data-stu-id="57ee3-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the '<' (less than) or '>' (greater than) keys.</span></span> <span data-ttu-id="57ee3-224">Metoda Delegate se dokončí, když uživatel stiskne klávesy X nebo x, které uživateli umožňují zastavit zobrazování textu kdykoli.</span><span class="sxs-lookup"><span data-stu-id="57ee3-224">The delegate method finishes when user presses the 'X' or 'x'  keys, which allow the user to stop the text display at any time.</span></span> <span data-ttu-id="57ee3-225">Tato metoda používá <xref:System.Console.ReadKey> k blokování a čekání, až uživatel stiskne klávesu.</span><span class="sxs-lookup"><span data-stu-id="57ee3-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="57ee3-226">K dokončení této funkce je nutné vytvořit novou `async Task` návratovou metodu, která spustí obě tyto úlohy ( `GetInput` a `ShowTeleprompter` ), a také spravovat sdílená data mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="57ee3-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="57ee3-227">Je čas vytvořit třídu, která může zpracovávat sdílená data mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="57ee3-227">It's time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="57ee3-228">Tato třída obsahuje dvě veřejné vlastnosti: zpoždění a příznak `Done` označující, že soubor byl zcela načten:</span><span class="sxs-lookup"><span data-stu-id="57ee3-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

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

<span data-ttu-id="57ee3-229">Tuto třídu vložte do nového souboru a vložte tuto třídu do `TeleprompterConsole` oboru názvů, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="57ee3-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="57ee3-230">Budete také muset přidat `using static` příkaz, abyste mohli odkazovat na `Min` `Max` metody a bez názvů ohraničující třídy nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="57ee3-230">You'll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="57ee3-231">[`using static`](../language-reference/keywords/using-static.md)Příkaz naimportuje metody z jedné třídy.</span><span class="sxs-lookup"><span data-stu-id="57ee3-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="57ee3-232">To je v kontrastu s `using` příkazy použitými do tohoto bodu, které importovaly všechny třídy z oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="57ee3-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="57ee3-233">Dále je nutné aktualizovat `ShowTeleprompter` `GetInput` metody a pro použití nového `config` objektu.</span><span class="sxs-lookup"><span data-stu-id="57ee3-233">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="57ee3-234">Napsat jednu finální `Task` `async` metodu vrácení, která spustí úlohy a ukončí po dokončení první úlohy:</span><span class="sxs-lookup"><span data-stu-id="57ee3-234">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="57ee3-235">Jednou z metod je toto <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> volání.</span><span class="sxs-lookup"><span data-stu-id="57ee3-235">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="57ee3-236">Tím se vytvoří `Task` , který se dokončí, jakmile se dokončí libovolný úkol v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="57ee3-236">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="57ee3-237">Dále je nutné aktualizovat `ShowTeleprompter` `GetInput` metody a pro použití `config` objektu pro zpoždění:</span><span class="sxs-lookup"><span data-stu-id="57ee3-237">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

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

<span data-ttu-id="57ee3-238">Tato nová verze `ShowTeleprompter` volá novou metodu ve `TeleprompterConfig` třídě.</span><span class="sxs-lookup"><span data-stu-id="57ee3-238">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="57ee3-239">Nyní je třeba aktualizovat `Main` volání na `RunTeleprompter` místo `ShowTeleprompter` :</span><span class="sxs-lookup"><span data-stu-id="57ee3-239">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="57ee3-240">Závěr</span><span class="sxs-lookup"><span data-stu-id="57ee3-240">Conclusion</span></span>

<span data-ttu-id="57ee3-241">V tomto kurzu jste si ukázali řadu funkcí pro jazyk C# a knihovny .NET Core, které souvisejí s prací v konzolových aplikacích.</span><span class="sxs-lookup"><span data-stu-id="57ee3-241">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span> <span data-ttu-id="57ee3-242">Na základě těchto znalostí můžete prozkoumat další informace o jazyce a třídách, které jsou zde zavedeny.</span><span class="sxs-lookup"><span data-stu-id="57ee3-242">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="57ee3-243">Seznámili jste se se základy pro vstupně-výstupní operace se soubory a konzolou, blokování a neblokování použití asynchronního programování založeného na úlohách, prohlídka jazyka C# a způsobu uspořádání programů v jazyce C# a .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="57ee3-243">You've seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized, and the .NET Core CLI.</span></span>

<span data-ttu-id="57ee3-244">Další informace o vstupně-výstupních operacích souborů najdete v tématu [vstupně-výstupní operace se soubory a datovým proudem](../../standard/io/index.md) .</span><span class="sxs-lookup"><span data-stu-id="57ee3-244">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="57ee3-245">Další informace o modelu asynchronního programování používaném v tomto kurzu naleznete v tématu [asynchronní programování založené na úlohách](../../standard/parallel-programming/task-based-asynchronous-programming.md) a v tématu věnovaném [asynchronnímu programování](../async.md) .</span><span class="sxs-lookup"><span data-stu-id="57ee3-245">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../../standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
