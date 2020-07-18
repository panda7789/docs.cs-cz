---
title: Návratové hodnoty Main () – Průvodce programováním v C#
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: a3e29903448c3eb5e0b7dda027677d1785a445e7
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416294"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="4bfda-102">Návratové hodnoty Main () (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4bfda-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="4bfda-103">`Main`Metoda může vracet `void` :</span><span class="sxs-lookup"><span data-stu-id="4bfda-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="4bfda-104">Může také vrátit `int` :</span><span class="sxs-lookup"><span data-stu-id="4bfda-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="4bfda-105">Pokud se návratová hodnota `Main` nepoužívá, vrátí návrat `void` umožňuje mírně jednodušší kód.</span><span class="sxs-lookup"><span data-stu-id="4bfda-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="4bfda-106">Vrácení celého čísla ale umožňuje programu sdělit informace o stavu jiným programům nebo skriptům, které vyvolávají spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="4bfda-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="4bfda-107">Návratová hodnota z `Main` je považována za ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="4bfda-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="4bfda-108">Pokud `void` je vrácen z `Main` , bude ukončovací kód implicitně `0` .</span><span class="sxs-lookup"><span data-stu-id="4bfda-108">If `void` is returned from `Main`, the exit code will be implicitly `0`.</span></span> <span data-ttu-id="4bfda-109">Následující příklad ukazuje, jak lze získat pøístup k návratové hodnotě `Main` .</span><span class="sxs-lookup"><span data-stu-id="4bfda-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="4bfda-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bfda-110">Example</span></span>

<span data-ttu-id="4bfda-111">V tomto příkladu se používají nástroje příkazového řádku [.NET Core](../../../core/index.yml) .</span><span class="sxs-lookup"><span data-stu-id="4bfda-111">This example uses [.NET Core](../../../core/index.yml) command-line tools.</span></span> <span data-ttu-id="4bfda-112">Pokud si nejste obeznámeni s nástroji příkazového řádku .NET Core, můžete o nich získat informace v tomto [článku](../../../core/tutorials/with-visual-studio-code.md)Začínáme.</span><span class="sxs-lookup"><span data-stu-id="4bfda-112">If you are unfamiliar with .NET Core command-line tools, you can learn about them in this [get-started article](../../../core/tutorials/with-visual-studio-code.md).</span></span>

<span data-ttu-id="4bfda-113">Upravte `Main` metodu v *program.cs* následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4bfda-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="4bfda-114">Když je program spuštěn ve Windows, všechny hodnoty vrácené `Main` funkcí jsou uloženy v proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="4bfda-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="4bfda-115">Tato proměnná prostředí se dá načíst pomocí `ERRORLEVEL` dávkového souboru nebo `$LastExitCode` z PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="4bfda-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="4bfda-116">Aplikaci můžete vytvořit pomocí příkazu [DOTNET CLI](../../../core/tools/dotnet.md) `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="4bfda-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="4bfda-117">Potom vytvořte powershellový skript, který spustí aplikaci a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="4bfda-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="4bfda-118">Vložte následující kód do textového souboru a uložte jej jako `test.ps1` ve složce, která obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="4bfda-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="4bfda-119">Spusťte skript prostředí PowerShell zadáním příkazu `test.ps1` do příkazového řádku PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="4bfda-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="4bfda-120">Vzhledem k tomu, že kód vrátí hodnotu nula, dávkový soubor ohlásí úspěch.</span><span class="sxs-lookup"><span data-stu-id="4bfda-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="4bfda-121">Pokud ale změníte MainReturnValTest.cs a vrátíte nenulovou hodnotu a pak znovu zkompilujete program, při následném spuštění skriptu PowerShellu se nahlásí chyba.</span><span class="sxs-lookup"><span data-stu-id="4bfda-121">However, if you change MainReturnValTest.cs to return a non-zero value and then recompile the program, subsequent execution of the powershell script will report failure.</span></span>

```dotnetcli
dotnet run
```

```powershell
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="4bfda-122">Ukázkový výstup</span><span class="sxs-lookup"><span data-stu-id="4bfda-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="4bfda-123">Asynchronní hlavní návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="4bfda-123">Async Main return values</span></span>

<span data-ttu-id="4bfda-124">Asynchronní hlavní návratové hodnoty přesunou často používaný kód, který je nezbytný pro volání asynchronních metod v `Main` kódu generovaném kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="4bfda-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="4bfda-125">Dříve museli jste napsat tuto konstrukci pro volání asynchronního kódu a zajistěte, aby byl program spuštěn až do dokončení asynchronní operace:</span><span class="sxs-lookup"><span data-stu-id="4bfda-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="4bfda-126">Teď to může nahradit:</span><span class="sxs-lookup"><span data-stu-id="4bfda-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="4bfda-127">Výhodou nové syntaxe je, že kompilátor vždy generuje správný kód.</span><span class="sxs-lookup"><span data-stu-id="4bfda-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="4bfda-128">Kód generovaný kompilátorem</span><span class="sxs-lookup"><span data-stu-id="4bfda-128">Compiler-generated code</span></span>

<span data-ttu-id="4bfda-129">Když vstupní bod aplikace vrátí `Task` nebo `Task<int>` , kompilátor vygeneruje nový vstupní bod, který volá metodu vstupního bodu deklarovanou v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="4bfda-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="4bfda-130">Za předpokladu, že je volán tento vstupní bod `$GeneratedMain` , kompilátor generuje pro tyto vstupní body následující kód:</span><span class="sxs-lookup"><span data-stu-id="4bfda-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="4bfda-131">`static Task Main()`Výsledkem je, že kompilátor emituje ekvivalent`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="4bfda-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="4bfda-132">`static Task Main(string[])`Výsledkem je, že kompilátor emituje ekvivalent`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="4bfda-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="4bfda-133">`static Task<int> Main()`Výsledkem je, že kompilátor emituje ekvivalent`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="4bfda-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="4bfda-134">`static Task<int> Main(string[])`Výsledkem je, že kompilátor emituje ekvivalent`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="4bfda-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="4bfda-135">Pokud příklady použili `async` Modifikátor `Main` metody, kompilátor vygeneruje stejný kód.</span><span class="sxs-lookup"><span data-stu-id="4bfda-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bfda-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bfda-136">See also</span></span>

- [<span data-ttu-id="4bfda-137">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4bfda-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4bfda-138">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4bfda-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4bfda-139">Argumenty Main () a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="4bfda-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="4bfda-140">Jak zobrazit argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="4bfda-140">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
