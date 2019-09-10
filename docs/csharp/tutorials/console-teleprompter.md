---
title: Konzolová aplikace
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 4324b25daa253b3d2446955ad9ca57c2f0294f0c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851018"
---
# <a name="console-application"></a><span data-ttu-id="5b5b4-103">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="5b5b4-103">Console Application</span></span>

<span data-ttu-id="5b5b4-104">V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="5b5b4-105">Naučíte se:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-105">You’ll learn:</span></span>

- <span data-ttu-id="5b5b4-106">Základní informace o rozhraní příkazového řádku .NET Core (CLI)</span><span class="sxs-lookup"><span data-stu-id="5b5b4-106">The basics of the .NET Core Command Line Interface (CLI)</span></span>
- <span data-ttu-id="5b5b4-107">Struktura C# konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="5b5b4-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="5b5b4-108">I/O konzoly</span><span class="sxs-lookup"><span data-stu-id="5b5b4-108">Console I/O</span></span>
- <span data-ttu-id="5b5b4-109">Základy vstupně-výstupních rozhraní API souborů v .NET</span><span class="sxs-lookup"><span data-stu-id="5b5b4-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="5b5b4-110">Základy asynchronního programování založeného na úlohách v .NET</span><span class="sxs-lookup"><span data-stu-id="5b5b4-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="5b5b4-111">Vytvoříte aplikaci, která přečte textový soubor, a vrátí obsah tohoto textového souboru do konzoly.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-111">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="5b5b4-112">Výstup do konzoly je TEMP, aby odpovídal čtení, které nahlasuje.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="5b5b4-113">Tempo můžete zrychlit nebo zpomalit stisknutím klávesy < (menší než) nebo > (větší než).</span><span class="sxs-lookup"><span data-stu-id="5b5b4-113">You can speed up or slow down the pace by pressing the ‘<’ (less than) or ‘>’ (greater than) keys.</span></span>

<span data-ttu-id="5b5b4-114">V tomto kurzu máte spoustu funkcí.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="5b5b4-115">Pojďme je sestavit jednou po jednom.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-115">Let’s build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5b5b4-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b5b4-116">Prerequisites</span></span>

<span data-ttu-id="5b5b4-117">Budete muset nastavit počítač, aby běžel .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-117">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="5b5b4-118">Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="5b5b4-118">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="5b5b4-119">Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-119">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="5b5b4-120">Budete muset nainstalovat svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-120">You’ll need to install your favorite code editor.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="5b5b4-121">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="5b5b4-121">Create the Application</span></span>

<span data-ttu-id="5b5b4-122">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-122">The first step is to create a new application.</span></span> <span data-ttu-id="5b5b4-123">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="5b5b4-124">Zajistěte, aby byl aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-124">Make that the current directory.</span></span> <span data-ttu-id="5b5b4-125">Zadejte příkaz `dotnet new console` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="5b5b4-126">Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="5b5b4-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="5b5b4-127">Než začnete s úpravami, Projděte si postup spuštění jednoduché aplikace Hello World.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-127">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="5b5b4-128">Po vytvoření aplikace zadejte `dotnet restore` do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="5b5b4-129">Tento příkaz spustí proces obnovení balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="5b5b4-130">NuGet je správce balíčků .NET.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="5b5b4-131">Tento příkaz stáhne všechny chybějící závislosti pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="5b5b4-132">Vzhledem k tomu, že se jedná o nový projekt, není zavedena žádná závislost, takže první spuštění stáhne rozhraní .NET Core Framework.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="5b5b4-133">Po provedení tohoto počátečního kroku budete muset spustit `dotnet restore` jenom při přidávání nových závislých balíčků nebo při aktualizaci verzí jakékoli závislosti.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="5b5b4-134">Po obnovení balíčků spustíte `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="5b5b4-135">Tím se spustí sestavovací modul a vytvoří se spustitelný soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="5b5b4-136">Nakonec můžete `dotnet run` spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="5b5b4-137">Jednoduchý Hello World kód aplikace je v Program.cs.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="5b5b4-138">Otevřete tento soubor ve svém oblíbeném textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="5b5b4-139">Chystáme se udělat první změny.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-139">We’re about to make our first changes.</span></span>
<span data-ttu-id="5b5b4-140">V horní části souboru se podívejte na příkaz using:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="5b5b4-141">Tento příkaz instruuje kompilátor, že všechny typy z `System` oboru názvů jsou v oboru.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="5b5b4-142">Podobně jako u jiných objektů orientovaných na objekty, C# které jste pravděpodobně použili, používá obory názvů k uspořádání typů.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="5b5b4-143">Tento program Hello World není jiný.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-143">This Hello World program is no different.</span></span> <span data-ttu-id="5b5b4-144">Můžete vidět, že program je uzavřen v oboru názvů s názvem na základě názvu aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="5b5b4-145">Pro účely tohoto kurzu změňte název oboru názvů na `TeleprompterConsole`:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="5b5b4-146">Čtení a vracení souboru se souborem</span><span class="sxs-lookup"><span data-stu-id="5b5b4-146">Reading and Echoing the File</span></span>

<span data-ttu-id="5b5b4-147">První funkcí, kterou je třeba přidat, je možnost číst textový soubor a zobrazit celý tento text v konzole.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="5b5b4-148">Nejprve přidáme textový soubor.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-148">First, let’s add a text file.</span></span> <span data-ttu-id="5b5b4-149">Zkopírujte soubor [sampleQuotes. txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z úložiště GitHub pro tuto [ukázku](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="5b5b4-150">Tato akce bude sloužit jako skript pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-150">This will serve as the script for your application.</span></span> <span data-ttu-id="5b5b4-151">Pokud chcete získat informace o tom, jak stáhnout ukázkovou aplikaci pro toto téma, přečtěte si pokyny v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) .</span><span class="sxs-lookup"><span data-stu-id="5b5b4-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="5b5b4-152">Dále do `Program` třídy přidejte následující metodu (hned `Main` pod metodu):</span><span class="sxs-lookup"><span data-stu-id="5b5b4-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

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

<span data-ttu-id="5b5b4-153">Tato metoda používá typy ze dvou nových oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="5b5b4-154">Pro zkompilování je třeba do horní části souboru přidat následující dva řádky:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-154">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="5b5b4-155">Rozhraní je definováno <xref:System.Collections.Generic> v oboru názvů. <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5b5b4-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="5b5b4-156">Třída je definována <xref:System.IO> v oboru názvů. <xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="5b5b4-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="5b5b4-157">Tato metoda je speciální typ C# metody označované jako *Metoda iterátoru*.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="5b5b4-158">Metody enumerátoru vracejí sekvence, které jsou vyhodnocovány laxně vytvářená.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="5b5b4-159">To znamená, že každá položka v sekvenci je vygenerována tak, jak je požadována kódem, který spotřebovává sekvenci.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="5b5b4-160">Metody enumerátoru jsou metody, které obsahují jeden [`yield return`](../language-reference/keywords/yield.md) nebo více příkazů.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="5b5b4-161">Objekt vrácený `ReadFrom` metodou obsahuje kód pro vygenerování každé položky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="5b5b4-162">V tomto příkladu zahrnuje čtení dalšího řádku textu ze zdrojového souboru a vrácení tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="5b5b4-163">Pokaždé, když volající kód požádá o další položku z sekvence, kód přečte další řádek textu ze souboru a vrátí jej.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="5b5b4-164">Když je soubor kompletně načtený, sekvence indikuje, že nejsou k dispozici žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="5b5b4-165">Existují dva další C# prvky syntaxe, které mohou být pro vás nové.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="5b5b4-166">[`using`](../language-reference/keywords/using-statement.md) Příkaz v této metodě spravuje čištění prostředků.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="5b5b4-167">Proměnná, která je inicializována v `using` příkazu (`reader`v tomto <xref:System.IDisposable> příkladu), musí implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="5b5b4-168">Toto rozhraní definuje jedinou metodu `Dispose`, která by měla být volána, když má být prostředek uvolněn.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="5b5b4-169">Kompilátor vygeneruje toto volání, když provádění dosáhne uzavírací závorce `using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="5b5b4-170">Kód generovaný kompilátorem zajišťuje uvolnění prostředku i v případě, že je vyvolána výjimka z kódu v bloku definovaném příkazem using.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="5b5b4-171">Proměnná je definována `var` pomocí klíčového slova. `reader`</span><span class="sxs-lookup"><span data-stu-id="5b5b4-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="5b5b4-172">[`var`](../language-reference/keywords/var.md)definuje *implicitní typovou lokální proměnnou*.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="5b5b4-173">To znamená, že typ proměnné je určen typem pro čas kompilace objektu přiřazeného k proměnné.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="5b5b4-174">Zde je návratová hodnota z <xref:System.IO.File.OpenText(System.String)> metody, což <xref:System.IO.StreamReader> je objekt.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="5b5b4-175">Teď naplníme kód, abychom si mohli přečíst soubor v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-175">Now, let’s fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="5b5b4-176">Spusťte program (pomocí `dotnet run`) a můžete zobrazit všechny vytištěné řádky do konzoly.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="5b5b4-177">Přidání zpoždění a formátování výstupu</span><span class="sxs-lookup"><span data-stu-id="5b5b4-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="5b5b4-178">To, co je ještě daleko příliš rychlé pro čtení nahlasu.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="5b5b4-179">Nyní je třeba přidat prodlevy ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="5b5b4-180">Při spuštění budete tvořit část základního kódu, který umožňuje asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-180">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="5b5b4-181">Tyto první kroky se ale budou řídit několika anti vzory.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="5b5b4-182">Anti-patterny jsou v komentářích při přidávání kódu ukázány a kód se aktualizuje v pozdějších krocích.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="5b5b4-183">Tato část obsahuje dva kroky.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-183">There are two steps to this section.</span></span> <span data-ttu-id="5b5b4-184">Nejprve aktualizujte metodu iterátoru tak, aby vracela jednoduchá slova namísto celých řádků.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-184">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="5b5b4-185">To se provádí s těmito úpravami.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-185">That’s done with these modifications.</span></span> <span data-ttu-id="5b5b4-186">Nahraďte `yield return line;` příkaz následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="5b5b4-187">Dále je nutné upravit způsob, jakým se vybírají řádky souboru, a po zápisu každého slova přidat prodlevu.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="5b5b4-188">Nahraďte `Main` příkaz v metodě následujícím blokem: `Console.WriteLine(line)`</span><span class="sxs-lookup"><span data-stu-id="5b5b4-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

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

<span data-ttu-id="5b5b4-189">Třída je v oboru názvů, takže je nutné přidat tento `using` příkaz na začátek souboru: <xref:System.Threading.Tasks> <xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="5b5b4-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="5b5b4-190">Spusťte ukázku a podívejte se na výstup.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-190">Run the sample, and check the output.</span></span> <span data-ttu-id="5b5b4-191">Nyní se vytisknou všechna jednotlivá slova následovaná zpožděním 200 ms.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="5b5b4-192">Zobrazený výstup však ukazuje některé problémy, protože zdrojový textový soubor obsahuje několik řádků, které mají více než 80 znaků bez zalomení řádku.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="5b5b4-193">To může být obtížné číst, zatímco se posunuje.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="5b5b4-194">To se dá snadno opravit.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-194">That’s easy to fix.</span></span> <span data-ttu-id="5b5b4-195">Pouze budete sledovat délku každého řádku a vygenerujete nový řádek vždy, když délka řádku dosáhne určité prahové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-195">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="5b5b4-196">Deklarovat místní proměnnou za deklarací `words` `ReadFrom` v metodě, která obsahuje délku řádku:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="5b5b4-197">Poté přidejte následující kód za `yield return word + " ";` příkaz (před pravou závorku):</span><span class="sxs-lookup"><span data-stu-id="5b5b4-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="5b5b4-198">Spusťte ukázku a budete moct číst nahlas v jeho předem nakonfigurovaném tempu.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-198">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="5b5b4-199">Asynchronní úlohy</span><span class="sxs-lookup"><span data-stu-id="5b5b4-199">Async Tasks</span></span>

<span data-ttu-id="5b5b4-200">V tomto posledním kroku přidáte kód pro asynchronní zápis výstupu do jedné úlohy a zároveň spustíte jiný úkol pro čtení vstupu od uživatele, pokud chtějí zrychlit nebo zpomalit zobrazení textu, nebo ukončit zobrazování textu.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-200">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="5b5b4-201">V tomto případě je to několik kroků a na konci budete mít k dispozici všechny potřebné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-201">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="5b5b4-202">Prvním krokem je vytvořit asynchronní <xref:System.Threading.Tasks.Task> návratovou metodu, která představuje kód, který jste dosud vytvořili pro čtení a zobrazení souboru.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="5b5b4-203">Přidejte tuto metodu do `Program` třídy (ta je pořízena z těla vaší `Main` metody):</span><span class="sxs-lookup"><span data-stu-id="5b5b4-203">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

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

<span data-ttu-id="5b5b4-204">Všimnete si dvou změn.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-204">You’ll notice two changes.</span></span> <span data-ttu-id="5b5b4-205">Nejprve v těle metody namísto volání <xref:System.Threading.Tasks.Task.Wait> synchronního čekání na dokončení úlohy `await` používá tato verze klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="5b5b4-206">K tomu je nutné přidat `async` modifikátor do podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="5b5b4-207">Tato metoda vrátí `Task`.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-207">This method returns a `Task`.</span></span> <span data-ttu-id="5b5b4-208">Všimněte si, že neexistují žádné návratové příkazy `Task` , které vracejí objekt.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="5b5b4-209">Místo toho `await` je objektvytvořenpomocíkódu,kterýkompilátorgenerujepři`Task` použití operátoru.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="5b5b4-210">Můžete si představit, že tato metoda vrátí, když dosáhne `await`.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="5b5b4-211">Vrácená `Task` zpráva znamená, že práce nebyla dokončena.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-211">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="5b5b4-212">Metoda pokračuje, až se dokončí očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="5b5b4-213">Když se provede dokončení, vrátí `Task` se na to, že se dokončilo.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="5b5b4-214">Volání kódu může sledovat, že `Task` bylo vráceno, aby bylo možné určit, kdy bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="5b5b4-215">Tuto novou metodu můžete zavolat v `Main` metodě:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="5b5b4-216">Zde v `Main`nástroji kód asynchronně čeká.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="5b5b4-217">Místo synchronního čekání `await` , pokud je to možné, byste měli použít operátor.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="5b5b4-218">Ale v `Main` metodě konzolové aplikace nemůžete `await` použít operátor.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-218">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="5b5b4-219">To by vedlo k ukončení aplikace před dokončením všech úloh.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="5b5b4-220">Pokud používáte C# 7,1 nebo novější, můžete vytvořit konzolové aplikace s [ `async` `Main` metodou](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="5b5b4-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="5b5b4-221">Dále je potřeba napsat druhou asynchronní metodu pro čtení z konzoly a sledovat "<" (menší než), ">" (větší než) a "X" nebo "klíče" x ".</span><span class="sxs-lookup"><span data-stu-id="5b5b4-221">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ (less than), ‘>’ (greater than) and ‘X’ or ‘x’ keys.</span></span> <span data-ttu-id="5b5b4-222">Zde je metoda, kterou přidáte pro tuto úlohu:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-222">Here’s the method you add for that task:</span></span>

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

<span data-ttu-id="5b5b4-223">Tím se vytvoří výraz lambda, který reprezentuje <xref:System.Action> delegáta, který přečte klíč z konzoly, a upraví místní proměnnou představující zpoždění, když uživatel stiskne klávesu ' < ' (menší než) nebo ' > ' (větší než).</span><span class="sxs-lookup"><span data-stu-id="5b5b4-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ (less than) or ‘>’ (greater than) keys.</span></span> <span data-ttu-id="5b5b4-224">Metoda Delegate se dokončí, když uživatel stiskne klávesy X nebo x, které uživateli umožňují zastavit zobrazování textu kdykoli.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-224">The delegate method finishes when user presses the ‘X’ or ‘x’  keys, which allow the user to stop the text display at any time.</span></span>
<span data-ttu-id="5b5b4-225">Tato metoda používá <xref:System.Console.ReadKey> k blokování a čekání, až uživatel stiskne klávesu.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="5b5b4-226">K dokončení této funkce je nutné vytvořit novou `async Task` návratovou metodu, která spustí obě tyto úlohy (`GetInput` a `ShowTeleprompter`), a také spravovat sdílená data mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="5b5b4-227">Je čas vytvořit třídu, která může zpracovávat sdílená data mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-227">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="5b5b4-228">Tato třída obsahuje dvě veřejné vlastnosti: zpoždění a příznak `Done` označující, že soubor byl zcela načten:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

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

<span data-ttu-id="5b5b4-229">Tuto třídu vložte do nového souboru a vložte tuto třídu do `TeleprompterConsole` oboru názvů, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="5b5b4-230">Budete také muset přidat `using static` příkaz, abyste mohli odkazovat na `Min` metody a `Max` bez názvů ohraničující třídy nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-230">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="5b5b4-231">[`using static`](../language-reference/keywords/using-static.md) Příkaz naimportuje metody z jedné třídy.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="5b5b4-232">To je v kontrastu s `using` příkazy použitými do tohoto bodu, které importovaly všechny třídy z oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="5b5b4-233">Dále je nutné aktualizovat `ShowTeleprompter` metody a `GetInput` pro použití nového `config` objektu.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-233">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="5b5b4-234">Napsat jednu finální `Task` metodu `async` vrácení, která spustí úlohy a ukončí po dokončení první úlohy:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-234">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="5b5b4-235">Jednou z metod je <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> toto volání.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-235">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="5b5b4-236">Tím se vytvoří `Task` , který se dokončí, jakmile se dokončí libovolný úkol v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-236">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="5b5b4-237">Dále je nutné aktualizovat `ShowTeleprompter` metody a `GetInput` pro použití `config` objektu pro zpoždění:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-237">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

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

<span data-ttu-id="5b5b4-238">Tato nová verze `ShowTeleprompter` volá novou metodu `TeleprompterConfig` ve třídě.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-238">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="5b5b4-239">Nyní je třeba aktualizovat `Main` volání `RunTeleprompter` na místo `ShowTeleprompter`:</span><span class="sxs-lookup"><span data-stu-id="5b5b4-239">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="5b5b4-240">Závěr</span><span class="sxs-lookup"><span data-stu-id="5b5b4-240">Conclusion</span></span>

<span data-ttu-id="5b5b4-241">V tomto kurzu jste si ukázali, kolik funkcí kolem C# jazyka a knihoven .NET Core souvisí s prací v konzolových aplikacích.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-241">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="5b5b4-242">Na základě těchto znalostí můžete prozkoumat další informace o jazyce a třídách, které jsou zde zavedeny.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-242">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="5b5b4-243">Seznámili jste se se základy pro vstupně-výstupní operace se soubory a konzolou, blokování a neblokování použití asynchronního programování založeného na úlohách C# , prohlídku C# jazyka a způsobu uspořádání programů a rozhraní příkazového řádku .NET Core a nástroje.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-243">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>

<span data-ttu-id="5b5b4-244">Další informace o vstupně-výstupních operacích souborů najdete v tématu [vstupně-výstupní operace se soubory a datovým proudem](../../standard/io/index.md) .</span><span class="sxs-lookup"><span data-stu-id="5b5b4-244">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="5b5b4-245">Další informace o modelu asynchronního programování používaném v tomto kurzu naleznete v tématu [asynchronní programování založené na úlohách](../..//standard/parallel-programming/task-based-asynchronous-programming.md) a v tématu věnovaném [asynchronnímu programování](../async.md) .</span><span class="sxs-lookup"><span data-stu-id="5b5b4-245">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
