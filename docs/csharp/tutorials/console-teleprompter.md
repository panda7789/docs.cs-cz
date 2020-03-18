---
title: Konzolová aplikace
description: Tento kurz vás naučí řadu funkcí v .NET Core a jazyk C#.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 09ce36e7a61f576dc4449976ce676701dc57c9cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76921120"
---
# <a name="console-app"></a><span data-ttu-id="613c7-103">Konzolová aplikace</span><span class="sxs-lookup"><span data-stu-id="613c7-103">Console app</span></span>

<span data-ttu-id="613c7-104">Tento kurz vás naučí řadu funkcí v .NET Core a jazyk C#.</span><span class="sxs-lookup"><span data-stu-id="613c7-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="613c7-105">Co se dozvíte:</span><span class="sxs-lookup"><span data-stu-id="613c7-105">You'll learn:</span></span>

- <span data-ttu-id="613c7-106">Základy rozhraní příkazového příkazu .NET Core</span><span class="sxs-lookup"><span data-stu-id="613c7-106">The basics of the .NET Core CLI</span></span>
- <span data-ttu-id="613c7-107">Struktura aplikace konzoly Jazyka C#</span><span class="sxs-lookup"><span data-stu-id="613c7-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="613c7-108">Vstupně-to-v konzole</span><span class="sxs-lookup"><span data-stu-id="613c7-108">Console I/O</span></span>
- <span data-ttu-id="613c7-109">Základy rozhraní API vstupně-nosných souborů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="613c7-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="613c7-110">Základy asynchronního programování založeného na úlohách v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="613c7-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="613c7-111">Vytvoříte aplikaci, která přečte textový soubor a vrátí obsah tohoto textového souboru do konzoly.</span><span class="sxs-lookup"><span data-stu-id="613c7-111">You'll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="613c7-112">Výstup do konzoly je přecházel tak, aby odpovídal jeho hlasitému čtení.</span><span class="sxs-lookup"><span data-stu-id="613c7-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="613c7-113">Tempo můžete zrychlit nebo zpomalit stisknutím kláves "<" (menší než) nebo ">" (větší než).</span><span class="sxs-lookup"><span data-stu-id="613c7-113">You can speed up or slow down the pace by pressing the '<' (less than) or '>' (greater than) keys.</span></span>

<span data-ttu-id="613c7-114">Existuje mnoho funkcí v tomto tutoriálu.</span><span class="sxs-lookup"><span data-stu-id="613c7-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="613c7-115">Postavíme je jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="613c7-115">Let's build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="613c7-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="613c7-116">Prerequisites</span></span>

- <span data-ttu-id="613c7-117">Nastavte počítač tak, aby spouštěl .NET Core.</span><span class="sxs-lookup"><span data-stu-id="613c7-117">Set up your machine to run .NET Core.</span></span> <span data-ttu-id="613c7-118">Pokyny k instalaci naleznete na stránce [ke stažení jádra .NET.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="613c7-118">You can find the installation instructions on the [.NET Core downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="613c7-119">Tuto aplikaci můžete spustit ve Windows, Linuxu, macOS nebo v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="613c7-119">You can run this application on Windows, Linux, macOS, or in a Docker container.</span></span>

- <span data-ttu-id="613c7-120">Nainstalujte si svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="613c7-120">Install your favorite code editor.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="613c7-121">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="613c7-121">Create the app</span></span>

<span data-ttu-id="613c7-122">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="613c7-122">The first step is to create a new application.</span></span> <span data-ttu-id="613c7-123">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="613c7-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="613c7-124">Ať je to aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="613c7-124">Make that the current directory.</span></span> <span data-ttu-id="613c7-125">Zadejte `dotnet new console` příkaz na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="613c7-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="613c7-126">Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="613c7-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="613c7-127">Než začnete provádět úpravy, pojďme projít kroky ke spuštění jednoduché aplikace Hello World.</span><span class="sxs-lookup"><span data-stu-id="613c7-127">Before you start making modifications, let's go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="613c7-128">Po vytvoření aplikace `dotnet restore` zadejte příkaz na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="613c7-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="613c7-129">Tento příkaz spustí proces obnovení balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="613c7-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="613c7-130">NuGet je správce balíčků .NET.</span><span class="sxs-lookup"><span data-stu-id="613c7-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="613c7-131">Tento příkaz stáhne všechny chybějící závislosti pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="613c7-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="613c7-132">Vzhledem k tomu, že se jedná o nový projekt, žádná ze závislostí není na místě, takže první spuštění stáhne rozhraní .NET Core framework.</span><span class="sxs-lookup"><span data-stu-id="613c7-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="613c7-133">Po tomto počátečním kroku budete `dotnet restore` muset spustit pouze při přidání nových závislých balíčků nebo aktualizaci verzí některé z vašich závislostí.</span><span class="sxs-lookup"><span data-stu-id="613c7-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="613c7-134">Po obnovení balíčků spustíte `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="613c7-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="613c7-135">To spustí modul sestavení a vytvoří spustitelný soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="613c7-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="613c7-136">Nakonec spustit `dotnet run` spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="613c7-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="613c7-137">Jednoduchý kód aplikace Hello World je vše v Program.cs.</span><span class="sxs-lookup"><span data-stu-id="613c7-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="613c7-138">Otevřete tento soubor pomocí oblíbeného textového editoru.</span><span class="sxs-lookup"><span data-stu-id="613c7-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="613c7-139">Chystáme se udělat první změny.</span><span class="sxs-lookup"><span data-stu-id="613c7-139">We're about to make our first changes.</span></span> <span data-ttu-id="613c7-140">V horní části souboru, viz using prohlášení:</span><span class="sxs-lookup"><span data-stu-id="613c7-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="613c7-141">Tento příkaz říká kompilátoru, `System` že všechny typy z oboru názvů jsou v oboru.</span><span class="sxs-lookup"><span data-stu-id="613c7-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="613c7-142">Stejně jako ostatní objektově orientované jazyky, které jste použili, c# používá obory názvů k uspořádání typů.</span><span class="sxs-lookup"><span data-stu-id="613c7-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="613c7-143">Tento program Hello World se nijak neliší.</span><span class="sxs-lookup"><span data-stu-id="613c7-143">This Hello World program is no different.</span></span> <span data-ttu-id="613c7-144">Můžete vidět, že program je uzavřen v oboru názvů s názvem založeným na názvu aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="613c7-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="613c7-145">V tomto kurzu změníme název oboru názvů `TeleprompterConsole`na :</span><span class="sxs-lookup"><span data-stu-id="613c7-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="613c7-146">Čtení a ozvěna souboru</span><span class="sxs-lookup"><span data-stu-id="613c7-146">Reading and Echoing the File</span></span>

<span data-ttu-id="613c7-147">První funkcí, kterou chcete přidat, je možnost číst textový soubor a zobrazit veškerý text do konzoly.</span><span class="sxs-lookup"><span data-stu-id="613c7-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="613c7-148">Nejprve přidáme textový soubor.</span><span class="sxs-lookup"><span data-stu-id="613c7-148">First, let's add a text file.</span></span> <span data-ttu-id="613c7-149">Zkopírujte soubor [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z úložiště GitHub pro tuto [ukázku](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="613c7-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="613c7-150">To bude sloužit jako skript pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="613c7-150">This will serve as the script for your application.</span></span> <span data-ttu-id="613c7-151">Pokud chcete informace o tom, jak stáhnout ukázkovou aplikaci pro toto téma, přečtěte si pokyny v tématu [Ukázky a výukové lekce.](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)</span><span class="sxs-lookup"><span data-stu-id="613c7-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="613c7-152">Dále přidejte následující metodu ve `Program` své `Main` třídě (přímo pod metodu):</span><span class="sxs-lookup"><span data-stu-id="613c7-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

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

<span data-ttu-id="613c7-153">Tato metoda používá typy ze dvou nových oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="613c7-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="613c7-154">Aby se toto zkompilovalo, budete muset na začátek souboru přidat následující dva řádky:</span><span class="sxs-lookup"><span data-stu-id="613c7-154">For this to compile you'll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="613c7-155">Rozhraní <xref:System.Collections.Generic.IEnumerable%601> je definováno <xref:System.Collections.Generic> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="613c7-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="613c7-156">Třída <xref:System.IO.File> je definována <xref:System.IO> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="613c7-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="613c7-157">Tato metoda je zvláštní typ metody Jazyka C# nazývaný *metodou Iterátor*.</span><span class="sxs-lookup"><span data-stu-id="613c7-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="613c7-158">Metody výčtu vracejí sekvence, které jsou vyhodnocovány líně.</span><span class="sxs-lookup"><span data-stu-id="613c7-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="613c7-159">To znamená, že každá položka v pořadí je generována tak, jak je požadována kódem, který tuto sekvenci spotřebovává.</span><span class="sxs-lookup"><span data-stu-id="613c7-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="613c7-160">Metody výčtu jsou metody, které [`yield return`](../language-reference/keywords/yield.md) obsahují jeden nebo více příkazů.</span><span class="sxs-lookup"><span data-stu-id="613c7-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="613c7-161">Objekt vrácený `ReadFrom` metodou obsahuje kód pro generování každé položky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="613c7-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="613c7-162">V tomto příkladu, který zahrnuje čtení dalšího řádku textu ze zdrojového souboru a vrácení tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="613c7-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="613c7-163">Pokaždé, když volající kód požaduje další položku z sekvence, kód přečte další řádek textu ze souboru a vrátí jej.</span><span class="sxs-lookup"><span data-stu-id="613c7-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="613c7-164">Když je soubor zcela přečten, sekvence označuje, že neexistují žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="613c7-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="613c7-165">Existují dva další prvky syntaxe jazyka C#, které mohou být pro vás nové.</span><span class="sxs-lookup"><span data-stu-id="613c7-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="613c7-166">Příkaz [`using`](../language-reference/keywords/using-statement.md) v této metodě spravuje vyčištění prostředků.</span><span class="sxs-lookup"><span data-stu-id="613c7-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="613c7-167">Proměnná, která je `using` inicializována v příkazu (`reader`, v tomto příkladu) musí implementovat <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="613c7-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="613c7-168">Toto rozhraní definuje jednu metodu , `Dispose`která by měla být volána, když by měl být prostředek uvolněn.</span><span class="sxs-lookup"><span data-stu-id="613c7-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="613c7-169">Kompilátor generuje toto volání při spuštění dosáhne `using` uzavírací složená závorka příkazu.</span><span class="sxs-lookup"><span data-stu-id="613c7-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="613c7-170">Kód generovaný kompilátorem zajišťuje, že prostředek je uvolněna i v případě, že je vyvolána výjimka z kódu v bloku definované using prohlášení.</span><span class="sxs-lookup"><span data-stu-id="613c7-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="613c7-171">Proměnná `reader` je definována pomocí klíčového `var` slova.</span><span class="sxs-lookup"><span data-stu-id="613c7-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="613c7-172">[`var`](../language-reference/keywords/var.md)definuje *implicitně zadali místní proměnné*.</span><span class="sxs-lookup"><span data-stu-id="613c7-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="613c7-173">To znamená, že typ proměnné je určen typem kompilace objektu přiřazeného proměnné.</span><span class="sxs-lookup"><span data-stu-id="613c7-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="613c7-174">Zde je vrácená hodnota <xref:System.IO.File.OpenText(System.String)> z metody, <xref:System.IO.StreamReader> která je objekt.</span><span class="sxs-lookup"><span data-stu-id="613c7-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="613c7-175">Nyní vyplníme kód a přečteme `Main` soubor v metodě:</span><span class="sxs-lookup"><span data-stu-id="613c7-175">Now, let's fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="613c7-176">Spusťte program `dotnet run`(pomocí) a uvidíte všechny linky vytištěné na konzoli.</span><span class="sxs-lookup"><span data-stu-id="613c7-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="613c7-177">Přidání zpoždění a formátování výstupu</span><span class="sxs-lookup"><span data-stu-id="613c7-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="613c7-178">To, co máte, je zobrazeno příliš rychle na to, abyste to bylo nahlas.</span><span class="sxs-lookup"><span data-stu-id="613c7-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="613c7-179">Nyní je třeba přidat zpoždění ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="613c7-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="613c7-180">Při spuštění budete vytvářet některé základní kód, který umožňuje asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="613c7-180">As you start, you'll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="613c7-181">Nicméně, tyto první kroky budou následovat několik anti-vzory.</span><span class="sxs-lookup"><span data-stu-id="613c7-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="613c7-182">Anti-vzory jsou zdůrazněny v komentářích při přidávání kódu a kód bude aktualizován v pozdějších krocích.</span><span class="sxs-lookup"><span data-stu-id="613c7-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="613c7-183">V této části jsou dva kroky.</span><span class="sxs-lookup"><span data-stu-id="613c7-183">There are two steps to this section.</span></span> <span data-ttu-id="613c7-184">Nejprve aktualizujete metodu iterátoru, abyste vrátili jednotlivá slova namísto celých řádků.</span><span class="sxs-lookup"><span data-stu-id="613c7-184">First, you'll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="613c7-185">To je hotovo s těmito úpravami.</span><span class="sxs-lookup"><span data-stu-id="613c7-185">That's done with these modifications.</span></span> <span data-ttu-id="613c7-186">Nahraďte `yield return line;` příkaz následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="613c7-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="613c7-187">Dále je třeba upravit způsob, jakým spotřebováváte řádky souboru, a přidat zpoždění po napsání každého slova.</span><span class="sxs-lookup"><span data-stu-id="613c7-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="613c7-188">Nahraďte `Console.WriteLine(line)` příkaz `Main` v metodě následujícím blokem:</span><span class="sxs-lookup"><span data-stu-id="613c7-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

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

<span data-ttu-id="613c7-189">Třída <xref:System.Threading.Tasks.Task> je v <xref:System.Threading.Tasks> oboru názvů, takže je `using` třeba přidat tento příkaz v horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="613c7-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="613c7-190">Spusťte ukázku a zkontrolujte výstup.</span><span class="sxs-lookup"><span data-stu-id="613c7-190">Run the sample, and check the output.</span></span> <span data-ttu-id="613c7-191">Nyní je vytištěno každé slovo, následované zpožděním 200 ms.</span><span class="sxs-lookup"><span data-stu-id="613c7-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="613c7-192">Zobrazený výstup však zobrazuje některé problémy, protože zdrojový textový soubor má několik řádků, které mají více než 80 znaků bez zalomení řádku.</span><span class="sxs-lookup"><span data-stu-id="613c7-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="613c7-193">To může být těžké číst, zatímco je to rolování.</span><span class="sxs-lookup"><span data-stu-id="613c7-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="613c7-194">To se dá snadno napravit.</span><span class="sxs-lookup"><span data-stu-id="613c7-194">That's easy to fix.</span></span> <span data-ttu-id="613c7-195">Budete jen sledovat délku každého řádku a generovat nový řádek vždy, když délka řádku dosáhne určité prahové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="613c7-195">You'll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="613c7-196">Deklarujte místní proměnnou po deklaraci `words` v metodě, `ReadFrom` která obsahuje délku řádku:</span><span class="sxs-lookup"><span data-stu-id="613c7-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="613c7-197">Potom přidejte následující kód `yield return word + " ";` za příkaz (před uzavírací složenou závorku):</span><span class="sxs-lookup"><span data-stu-id="613c7-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="613c7-198">Spusťte ukázku a budete moci číst nahlas v předem nakonfigurovaném tempu.</span><span class="sxs-lookup"><span data-stu-id="613c7-198">Run the sample, and you'll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="613c7-199">Asynchronní úlohy</span><span class="sxs-lookup"><span data-stu-id="613c7-199">Async Tasks</span></span>

<span data-ttu-id="613c7-200">V tomto posledním kroku přidáte kód pro zápis výstupu asynchronně v jedné úloze, a zároveň spuštění jiné úlohy pro čtení vstupu od uživatele, pokud chtějí urychlit nebo zpomalit zobrazení textu nebo úplně zastavit zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="613c7-200">In this final step, you'll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="613c7-201">To má několik kroků v něm a na konci, budete mít všechny aktualizace, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="613c7-201">This has a few steps in it and by the end, you'll have all the updates that you need.</span></span> <span data-ttu-id="613c7-202">Prvním krokem je vytvoření asynchronní <xref:System.Threading.Tasks.Task> návratové metody, která představuje kód, který jste dosud vytvořili ke čtení a zobrazení souboru.</span><span class="sxs-lookup"><span data-stu-id="613c7-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you've created so far to read and display the file.</span></span>

<span data-ttu-id="613c7-203">Přidejte tuto `Program` metodu do třídy (je `Main` převzata z těla vaší metody):</span><span class="sxs-lookup"><span data-stu-id="613c7-203">Add this method to your `Program` class (it's taken from the body of your `Main` method):</span></span>

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

<span data-ttu-id="613c7-204">Všimněte si dvou změn.</span><span class="sxs-lookup"><span data-stu-id="613c7-204">You'll notice two changes.</span></span> <span data-ttu-id="613c7-205">Nejprve v těle metody, namísto <xref:System.Threading.Tasks.Task.Wait> volání synchronně čekat na dokončení úkolu, tato `await` verze používá klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="613c7-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="613c7-206">Chcete-li to provést, musíte `async` přidat modifikátor k podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="613c7-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="613c7-207">Tato metoda `Task`vrátí .</span><span class="sxs-lookup"><span data-stu-id="613c7-207">This method returns a `Task`.</span></span> <span data-ttu-id="613c7-208">Všimněte si, že neexistují `Task` žádné návratové příkazy, které vrátí objekt.</span><span class="sxs-lookup"><span data-stu-id="613c7-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="613c7-209">Místo toho `Task` je tento objekt vytvořen kódem, který `await` kompilátor generuje při použití operátoru.</span><span class="sxs-lookup"><span data-stu-id="613c7-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="613c7-210">Můžete si představit, že tato metoda `await`vrátí, když dosáhne .</span><span class="sxs-lookup"><span data-stu-id="613c7-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="613c7-211">Vrácené `Task` označuje, že práce nebyla dokončena.</span><span class="sxs-lookup"><span data-stu-id="613c7-211">The returned `Task` indicates that the work has not completed.</span></span> <span data-ttu-id="613c7-212">Metoda pokračuje po dokončení očekávané úlohy.</span><span class="sxs-lookup"><span data-stu-id="613c7-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="613c7-213">Po dokončení, vrácené `Task` označuje, že je dokončena.</span><span class="sxs-lookup"><span data-stu-id="613c7-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="613c7-214">Volající kód můžete `Task` sledovat, který se vrátil k určení, kdy byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="613c7-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="613c7-215">Tuto novou metodu můžete `Main` volat ve vaší metodě:</span><span class="sxs-lookup"><span data-stu-id="613c7-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="613c7-216">Zde v `Main`, kód synchronně čekat.</span><span class="sxs-lookup"><span data-stu-id="613c7-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="613c7-217">Měli byste `await` použít operátor namísto synchronního čekání, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="613c7-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="613c7-218">Ale v metodě konzolové `Main` aplikace nelze `await` použít operátor.</span><span class="sxs-lookup"><span data-stu-id="613c7-218">But, in a console application's `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="613c7-219">To by mělo za následek ukončení aplikace před dokončením všech úkolů.</span><span class="sxs-lookup"><span data-stu-id="613c7-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="613c7-220">Pokud používáte C# 7.1 nebo novější, [ `async` `Main` ](../whats-new/csharp-7-1.md#async-main)můžete vytvořit konzolové aplikace s metodou .</span><span class="sxs-lookup"><span data-stu-id="613c7-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="613c7-221">Dále je třeba napsat druhou asynchronní metodu číst z konzoly a sledovat '<' (menší než), '>' (větší než) a 'X' nebo 'x' klíče.</span><span class="sxs-lookup"><span data-stu-id="613c7-221">Next, you need to write the second asynchronous method to read from the Console and watch for the '<' (less than), '>' (greater than) and 'X' or 'x' keys.</span></span> <span data-ttu-id="613c7-222">Zde je metoda, kterou přidáte pro tento úkol:</span><span class="sxs-lookup"><span data-stu-id="613c7-222">Here's the method you add for that task:</span></span>

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

<span data-ttu-id="613c7-223">Tím se vytvoří výraz lambda představující <xref:System.Action> delegáta, který přečte klíč z konzoly a upraví místní proměnnou představující zpoždění, když uživatel stiskne klávesy "<" (menší než) nebo ">" (větší než).</span><span class="sxs-lookup"><span data-stu-id="613c7-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the '<' (less than) or '>' (greater than) keys.</span></span> <span data-ttu-id="613c7-224">Metoda delegáta se dokončí, když uživatel stiskne klávesy "X" nebo 'x', které uživateli umožňují kdykoli zastavit zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="613c7-224">The delegate method finishes when user presses the 'X' or 'x'  keys, which allow the user to stop the text display at any time.</span></span> <span data-ttu-id="613c7-225">Tato metoda <xref:System.Console.ReadKey> používá k zablokování a čekání na uživatele stisknout klávesu.</span><span class="sxs-lookup"><span data-stu-id="613c7-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="613c7-226">Chcete-li dokončit tuto funkci, `async Task` je třeba vytvořit novou metodu`GetInput` `ShowTeleprompter`vrácení, která spustí oba tyto úkoly ( a ) a také spravuje sdílená data mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="613c7-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="613c7-227">Je čas vytvořit třídu, která může zpracovávat sdílená data mezi těmito dvěma úkoly.</span><span class="sxs-lookup"><span data-stu-id="613c7-227">It's time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="613c7-228">Tato třída obsahuje dvě veřejné vlastnosti: `Done` zpoždění a příznak označující, že soubor byl zcela přečten:</span><span class="sxs-lookup"><span data-stu-id="613c7-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

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

<span data-ttu-id="613c7-229">Vložte tuto třídu do nového souboru `TeleprompterConsole` a uzavřete ji do oboru názvů, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="613c7-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="613c7-230">Budete také muset přidat `using static` příkaz, takže můžete `Min` odkazovat na metody a `Max` bez ohraničujících názvů tříd nebo oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="613c7-230">You'll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="613c7-231">Příkaz [`using static`](../language-reference/keywords/using-static.md) importuje metody z jedné třídy.</span><span class="sxs-lookup"><span data-stu-id="613c7-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="613c7-232">To je v `using` rozporu s příkazy používané až do tohoto okamžiku, které importovaly všechny třídy z oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="613c7-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="613c7-233">Dále je třeba aktualizovat `ShowTeleprompter` `GetInput` metody a pro `config` použití nového objektu.</span><span class="sxs-lookup"><span data-stu-id="613c7-233">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="613c7-234">Napište `Task` jednu `async` konečnou metodu vrácení, abyste zahájili oba úkoly a ukončili po dokončení prvního úkolu:</span><span class="sxs-lookup"><span data-stu-id="613c7-234">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="613c7-235">Jedna nová metoda je <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> zde volání.</span><span class="sxs-lookup"><span data-stu-id="613c7-235">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="613c7-236">To vytvoří, `Task` který dokončí, jakmile některý z úkolů v seznamu argumentů dokončí.</span><span class="sxs-lookup"><span data-stu-id="613c7-236">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="613c7-237">Dále je třeba aktualizovat `ShowTeleprompter` a `GetInput` metody pro `config` použití objektu pro zpoždění:</span><span class="sxs-lookup"><span data-stu-id="613c7-237">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

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

<span data-ttu-id="613c7-238">Tato nová `ShowTeleprompter` verze volá novou `TeleprompterConfig` metodu ve třídě.</span><span class="sxs-lookup"><span data-stu-id="613c7-238">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="613c7-239">Nyní je třeba `Main` aktualizovat `RunTeleprompter` volání `ShowTeleprompter`namísto:</span><span class="sxs-lookup"><span data-stu-id="613c7-239">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="613c7-240">Závěr</span><span class="sxs-lookup"><span data-stu-id="613c7-240">Conclusion</span></span>

<span data-ttu-id="613c7-241">Tento kurz vám ukázal řadu funkcí kolem jazyka C# a knihoven .NET Core souvisejících s prací v konzolových aplikacích.</span><span class="sxs-lookup"><span data-stu-id="613c7-241">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span> <span data-ttu-id="613c7-242">Můžete stavět na těchto znalostech, abyste prozkoumali více o jazyce a třídách zde zavedených.</span><span class="sxs-lookup"><span data-stu-id="613c7-242">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="613c7-243">Viděli jste základy vstupně-amp;v. souboru a konzoly, blokování a neblokující použití asynchronního programování založeného na úlohách, prohlídku jazyka C# a uspořádání programů jazyka C# a rozhraní PŘÍKAZOVÉHO PŘÍKAZU .NET Core.</span><span class="sxs-lookup"><span data-stu-id="613c7-243">You've seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized, and the .NET Core CLI.</span></span>

<span data-ttu-id="613c7-244">Další informace o vstupně-já souborů najdete v tématu [Soubor a vstupně-tovišti](../../standard/io/index.md) datových proudů.</span><span class="sxs-lookup"><span data-stu-id="613c7-244">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="613c7-245">Další informace o asynchronním programovacím modelu použitém v tomto kurzu naleznete v tématu [Asynchronní programování založené na úlohách](../..//standard/parallel-programming/task-based-asynchronous-programming.md) a v tématu [asynchronního programování.](../async.md)</span><span class="sxs-lookup"><span data-stu-id="613c7-245">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
