---
title: "Návratové hodnoty Main() (Průvodce programováním v C#)"
ms.date: 08/02/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f317879a4941adfd3d125c7697226f8a510254c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="0f153-102">Návratové hodnoty Main() (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="0f153-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="0f153-103">`Main` Metoda může vrátit `void`:</span><span class="sxs-lookup"><span data-stu-id="0f153-103">The `Main` method can return `void`:</span></span>

[!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]

<span data-ttu-id="0f153-104">Také můžete vrátit `int`:</span><span class="sxs-lookup"><span data-stu-id="0f153-104">It can also return an `int`:</span></span>

[!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]

<span data-ttu-id="0f153-105">Pokud z hodnoty návratový `Main` se nepoužívá, vrácení `void` umožňuje mírně jednodušší kódu.</span><span class="sxs-lookup"><span data-stu-id="0f153-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="0f153-106">Vrací celé číslo, ale umožňuje programu předávat informace o stavu do jiných programů nebo skriptů, které vyvolají spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="0f153-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="0f153-107">Vrácená hodnota z `Main` je považován za kód ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="0f153-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="0f153-108">Následující příklad ukazuje, jak z hodnoty návratový `Main` je přístupná.</span><span class="sxs-lookup"><span data-stu-id="0f153-108">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="0f153-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f153-109">Example</span></span>

<span data-ttu-id="0f153-110">Tento příklad používá [.NET Core](../../../core/index.md) nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0f153-110">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="0f153-111">Pokud jste unfamilar pomocí nástroje příkazového řádku .NET Core, informace o najdete je v tomto [Get Začínáme tématu](../../../core/tutorials/using-with-xplat-cli.md).</span><span class="sxs-lookup"><span data-stu-id="0f153-111">If you are unfamilar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="0f153-112">Změnit `Main` metoda v *program.cs* následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0f153-112">Modify the `Main` method in *program.cs* as follows:</span></span>

[!code-csharp[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]

<span data-ttu-id="0f153-113">Když program se spustí v systému Windows, libovolná hodnota vrácená z `Main` funkce je uložené v proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="0f153-113">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="0f153-114">Tato proměnná prostředí se dá načíst pomocí `ERRORLEVEL` z dávkového souboru nebo `$LastExitCode` z prostředí powershell.</span><span class="sxs-lookup"><span data-stu-id="0f153-114">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="0f153-115">Můžete vytvořit aplikace pomocí [dotnet rozhraní příkazového řádku](../../../core/tools/dotnet.md) `dotnet build` příkaz.</span><span class="sxs-lookup"><span data-stu-id="0f153-115">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="0f153-116">Dále vytvořte skript prostředí Powershell a spusťte aplikaci zobrazit výsledek.</span><span class="sxs-lookup"><span data-stu-id="0f153-116">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="0f153-117">Vložte následující kód do textového souboru a uložte ho jako `test.ps1` ve složce, která obsahuje projektu.</span><span class="sxs-lookup"><span data-stu-id="0f153-117">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="0f153-118">Spustit skript prostředí powershell zadáním `test.ps1` v příkazovém řádku prostředí powershell.</span><span class="sxs-lookup"><span data-stu-id="0f153-118">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="0f153-119">Protože kód vrátí hodnotu 0, dávkového souboru oznámí úspěšné.</span><span class="sxs-lookup"><span data-stu-id="0f153-119">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="0f153-120">Pokud změníte MainReturnValTest.cs vrátí nenulovou hodnotu a pak znovu kompilace programu, však následné provádění skriptu prostředí powershell oznámí selhání.</span><span class="sxs-lookup"><span data-stu-id="0f153-120">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="0f153-121">Ukázkový výstup</span><span class="sxs-lookup"><span data-stu-id="0f153-121">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="0f153-122">Hlavní asynchronní návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="0f153-122">Async Main return values</span></span>

<span data-ttu-id="0f153-123">Asynchronní hlavní vrátit hodnoty přesunout často používaný kód, který je nezbytný pro volání asynchronních metod v `Main` generované kompilátorem kódu.</span><span class="sxs-lookup"><span data-stu-id="0f153-123">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="0f153-124">Dříve museli byste tento konstrukce volání asynchronní kódu a ujistěte se, že vaše aplikace spuštěna až do dokončení asynchronní operaci zápisu:</span><span class="sxs-lookup"><span data-stu-id="0f153-124">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

<span data-ttu-id="0f153-125">Teď to může být nahrazen:</span><span class="sxs-lookup"><span data-stu-id="0f153-125">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="0f153-126">Výhodou nové syntaxe je, že kompilátor vždy generuje správný kód.</span><span class="sxs-lookup"><span data-stu-id="0f153-126">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="0f153-127">Kompilátor vygeneruje kód</span><span class="sxs-lookup"><span data-stu-id="0f153-127">Compiler generated code</span></span>

<span data-ttu-id="0f153-128">Když se vrátí vstupní bod aplikace `Task` nebo `Task<int>`, kompilátor vygeneruje nový vstupní bod, který volá metoda deklarované v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f153-128">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="0f153-129">Za předpokladu, že tento vstupní bod se nazývá `$GeneratedMain`, kompilátor generuje následující kód pro tyto vstupní body:</span><span class="sxs-lookup"><span data-stu-id="0f153-129">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="0f153-130">`static Task Main()`výsledky v kompilátoru emitování ekvivalent`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="0f153-130">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="0f153-131">`static Task Main(string[])`výsledky v kompilátoru emitování ekvivalent`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="0f153-131">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="0f153-132">`static Task<int> Main()`výsledky v kompilátoru emitování ekvivalent`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="0f153-132">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="0f153-133">`static Task<int> Main(string[])`výsledky v kompilátoru emitování ekvivalent`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="0f153-133">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="0f153-134">Pokud se používá v příkladech `async` modifikátor na `Main` metoda, kompilátor by generovat stejný kód.</span><span class="sxs-lookup"><span data-stu-id="0f153-134">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f153-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f153-135">See also</span></span>
<span data-ttu-id="0f153-136">[Průvodce programováním v C#](../../programming-guide/index.md)
[referenční dokumentace jazyka C#](../index.md)
[Main() a příkazového řádku argumenty](index.md)
[postupy: zobrazení příkazového řádku Argumenty](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[postupy: přístup příkazového řádku argumenty pomocí příkazu foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)</span><span class="sxs-lookup"><span data-stu-id="0f153-136">[C# Programming Guide](../../programming-guide/index.md)
[C# Reference](../index.md)
[Main() and Command-Line Arguments](index.md)
[How to: Display Command Line Arguments](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[How to: Access Command-Line Arguments Using foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)</span></span>
