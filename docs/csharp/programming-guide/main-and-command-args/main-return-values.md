---
title: Návratové hodnoty Main() – C# Průvodce programováním
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: e41b92239f0ba1a94190262c337f09eedaddab31
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965719"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="81e6d-102">Návratové hodnoty Main() (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="81e6d-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="81e6d-103">`Main` Metoda může vrátit `void`:</span><span class="sxs-lookup"><span data-stu-id="81e6d-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="81e6d-104">Můžete také vrátit `int`:</span><span class="sxs-lookup"><span data-stu-id="81e6d-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="81e6d-105">Pokud se návratová hodnota z `Main` nepoužívá vrácení `void` umožňuje kód o něco jednodušší.</span><span class="sxs-lookup"><span data-stu-id="81e6d-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="81e6d-106">Vrací celé číslo, ale umožňuje programu předávat informace o stavu do jiných programů nebo skriptů, které vyvolají spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="81e6d-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="81e6d-107">Hodnota vrácená z `Main` je považován za ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="81e6d-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="81e6d-108">Následující příklad ukazuje, jak se návratová hodnota z `Main` je přístupný.</span><span class="sxs-lookup"><span data-stu-id="81e6d-108">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="81e6d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="81e6d-109">Example</span></span>

<span data-ttu-id="81e6d-110">Tento příklad používá [.NET Core](../../../core/index.md) nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="81e6d-110">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="81e6d-111">Pokud nejste obeznámeni s nástroji příkazového řádku .NET Core, můžete o nich informace v tomto [tématu Začínáme Get](../../../core/tutorials/using-with-xplat-cli.md).</span><span class="sxs-lookup"><span data-stu-id="81e6d-111">If you are unfamiliar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="81e6d-112">Upravit `Main` metoda *program.cs* následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="81e6d-112">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="81e6d-113">Pokud program je spuštěn ve Windows, libovolná hodnota vrácená z `Main` funkce je uložen v proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="81e6d-113">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="81e6d-114">Tato proměnná prostředí se dá načíst pomocí `ERRORLEVEL` z dávkového souboru, nebo `$LastExitCode` z powershellu.</span><span class="sxs-lookup"><span data-stu-id="81e6d-114">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="81e6d-115">Můžete vytvářet aplikace pomocí [rozhraní příkazového řádku dotnet](../../../core/tools/dotnet.md) `dotnet build` příkazu.</span><span class="sxs-lookup"><span data-stu-id="81e6d-115">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="81e6d-116">Dále vytvořte skript Powershellu pro spuštění aplikace a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="81e6d-116">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="81e6d-117">Vložte následující kód do textového souboru a uložte ho jako `test.ps1` ve složce, která obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="81e6d-117">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="81e6d-118">Spusťte skript prostředí powershell zadáním `test.ps1` řádku powershellu.</span><span class="sxs-lookup"><span data-stu-id="81e6d-118">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="81e6d-119">Protože kód vrátí hodnotu 0, dávkový soubor se hlásí úspěch.</span><span class="sxs-lookup"><span data-stu-id="81e6d-119">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="81e6d-120">Pokud změníte MainReturnValTest.cs vrátí nenulovou hodnotu a potom znovu zkompilujete program, ale následné spuštění powershellového skriptu oznámí selhání.</span><span class="sxs-lookup"><span data-stu-id="81e6d-120">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="81e6d-121">Ukázkový výstup</span><span class="sxs-lookup"><span data-stu-id="81e6d-121">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="81e6d-122">Hlavní asynchronní návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="81e6d-122">Async Main return values</span></span>

<span data-ttu-id="81e6d-123">Asynchronní hlavní vrátit hodnoty přesunout často používaný kód pro volání asynchronních metod `Main` kód generovaný kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="81e6d-123">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="81e6d-124">Dříve byste museli napsat tento konstruktor pro volání asynchronní kód a ujistěte se, že váš program byl dokončen asynchronní operace:</span><span class="sxs-lookup"><span data-stu-id="81e6d-124">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="81e6d-125">Teď to lze nahradit:</span><span class="sxs-lookup"><span data-stu-id="81e6d-125">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="81e6d-126">Výhodou novou syntaxi je, že kompilátor vždy generovat správný kód.</span><span class="sxs-lookup"><span data-stu-id="81e6d-126">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="81e6d-127">Kód generovaný kompilátorem</span><span class="sxs-lookup"><span data-stu-id="81e6d-127">Compiler generated code</span></span>

<span data-ttu-id="81e6d-128">Pokud vstupní bod aplikace vrátí `Task` nebo `Task<int>`, kompilátor vygeneruje nový vstupní bod, který volá metodu vstupního bodu, která je deklarována v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="81e6d-128">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="81e6d-129">Za předpokladu, že tento vstupní bod se nazývá `$GeneratedMain`, kompilátor generuje následující kód pro tyto vstupní body:</span><span class="sxs-lookup"><span data-stu-id="81e6d-129">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="81e6d-130">`static Task Main()` výsledky v kompilátoru generování ekvivalent `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="81e6d-130">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="81e6d-131">`static Task Main(string[])` výsledky v kompilátoru generování ekvivalent `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="81e6d-131">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="81e6d-132">`static Task<int> Main()` výsledky v kompilátoru generování ekvivalent `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="81e6d-132">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="81e6d-133">`static Task<int> Main(string[])` výsledky v kompilátoru generování ekvivalent `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="81e6d-133">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="81e6d-134">Pokud se používá v příkladech `async` modifikátor `Main` metoda, kompilátor vygeneruje stejný kód.</span><span class="sxs-lookup"><span data-stu-id="81e6d-134">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="81e6d-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81e6d-135">See also</span></span>
- [<span data-ttu-id="81e6d-136">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="81e6d-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="81e6d-137">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="81e6d-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="81e6d-138">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="81e6d-138">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="81e6d-139">Postupy: Zobrazení argumentů příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="81e6d-139">How to: Display Command Line Arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="81e6d-140">Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach</span><span class="sxs-lookup"><span data-stu-id="81e6d-140">How to: Access Command-Line Arguments Using foreach</span></span>](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
