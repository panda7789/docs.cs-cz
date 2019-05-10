---
title: Návratové hodnoty Main() – C# Průvodce programováním
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 1e4c03985908f6e49d5ce001cdc9c1472f5a6d44
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595602"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="dfcc5-102">Návratové hodnoty Main() (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="dfcc5-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="dfcc5-103">`Main` Metoda může vrátit `void`:</span><span class="sxs-lookup"><span data-stu-id="dfcc5-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="dfcc5-104">Můžete také vrátit `int`:</span><span class="sxs-lookup"><span data-stu-id="dfcc5-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="dfcc5-105">Pokud se návratová hodnota z `Main` nepoužívá vrácení `void` umožňuje kód o něco jednodušší.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="dfcc5-106">Vrací celé číslo, ale umožňuje programu předávat informace o stavu do jiných programů nebo skriptů, které vyvolají spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="dfcc5-107">Hodnota vrácená z `Main` je považován za ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="dfcc5-108">Pokud `void` vrácená `Main` ukončovací kód bude implicitně `0`.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-108">If `void` is returned from `Main` the exit code will be implicitly `0`.</span></span> <span data-ttu-id="dfcc5-109">Následující příklad ukazuje, jak se návratová hodnota z `Main` je přístupný.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="dfcc5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="dfcc5-110">Example</span></span>

<span data-ttu-id="dfcc5-111">Tento příklad používá [.NET Core](../../../core/index.md) nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-111">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="dfcc5-112">Pokud nejste obeznámeni s nástroji příkazového řádku .NET Core, můžete o nich informace v tomto [tématu Začínáme Get](../../../core/tutorials/using-with-xplat-cli.md).</span><span class="sxs-lookup"><span data-stu-id="dfcc5-112">If you are unfamiliar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="dfcc5-113">Upravit `Main` metoda *program.cs* následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="dfcc5-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="dfcc5-114">Pokud program je spuštěn ve Windows, libovolná hodnota vrácená z `Main` funkce je uložen v proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="dfcc5-115">Tato proměnná prostředí se dá načíst pomocí `ERRORLEVEL` z dávkového souboru, nebo `$LastExitCode` z powershellu.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="dfcc5-116">Můžete vytvářet aplikace pomocí [rozhraní příkazového řádku dotnet](../../../core/tools/dotnet.md) `dotnet build` příkazu.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="dfcc5-117">Dále vytvořte skript Powershellu pro spuštění aplikace a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="dfcc5-118">Vložte následující kód do textového souboru a uložte ho jako `test.ps1` ve složce, která obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="dfcc5-119">Spusťte skript prostředí powershell zadáním `test.ps1` řádku powershellu.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="dfcc5-120">Protože kód vrátí hodnotu 0, dávkový soubor se hlásí úspěch.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="dfcc5-121">Pokud změníte MainReturnValTest.cs vrátí nenulovou hodnotu a potom znovu zkompilujete program, ale následné spuštění powershellového skriptu oznámí selhání.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-121">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="dfcc5-122">Ukázkový výstup</span><span class="sxs-lookup"><span data-stu-id="dfcc5-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="dfcc5-123">Hlavní asynchronní návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="dfcc5-123">Async Main return values</span></span>

<span data-ttu-id="dfcc5-124">Asynchronní hlavní vrátit hodnoty přesunout často používaný kód pro volání asynchronních metod `Main` kód generovaný kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="dfcc5-125">Dříve byste museli napsat tento konstruktor pro volání asynchronní kód a ujistěte se, že váš program byl dokončen asynchronní operace:</span><span class="sxs-lookup"><span data-stu-id="dfcc5-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="dfcc5-126">Teď to lze nahradit:</span><span class="sxs-lookup"><span data-stu-id="dfcc5-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="dfcc5-127">Výhodou novou syntaxi je, že kompilátor vždy generovat správný kód.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="dfcc5-128">Kód generovaný kompilátorem</span><span class="sxs-lookup"><span data-stu-id="dfcc5-128">Compiler generated code</span></span>

<span data-ttu-id="dfcc5-129">Pokud vstupní bod aplikace vrátí `Task` nebo `Task<int>`, kompilátor vygeneruje nový vstupní bod, který volá metodu vstupního bodu, která je deklarována v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="dfcc5-130">Za předpokladu, že tento vstupní bod se nazývá `$GeneratedMain`, kompilátor generuje následující kód pro tyto vstupní body:</span><span class="sxs-lookup"><span data-stu-id="dfcc5-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="dfcc5-131">`static Task Main()` výsledky v kompilátoru generování ekvivalent `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="dfcc5-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="dfcc5-132">`static Task Main(string[])` výsledky v kompilátoru generování ekvivalent `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="dfcc5-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="dfcc5-133">`static Task<int> Main()` výsledky v kompilátoru generování ekvivalent `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="dfcc5-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="dfcc5-134">`static Task<int> Main(string[])` výsledky v kompilátoru generování ekvivalent `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="dfcc5-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="dfcc5-135">Pokud se používá v příkladech `async` modifikátor `Main` metoda, kompilátor vygeneruje stejný kód.</span><span class="sxs-lookup"><span data-stu-id="dfcc5-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfcc5-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfcc5-136">See also</span></span>

- [<span data-ttu-id="dfcc5-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dfcc5-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dfcc5-138">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dfcc5-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dfcc5-139">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="dfcc5-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="dfcc5-140">Postupy: Zobrazení argumentů příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="dfcc5-140">How to: Display Command Line Arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="dfcc5-141">Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach</span><span class="sxs-lookup"><span data-stu-id="dfcc5-141">How to: Access Command-Line Arguments Using foreach</span></span>](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
