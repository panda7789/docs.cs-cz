---
title: Main() Návratové hodnoty - Průvodce programováním Jazyka C#
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: eaa78c33613093bb0e108870669392d07d346a95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503998"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="72842-102">Main() vrácené hodnoty (Průvodce programováním Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="72842-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="72842-103">Metoda `Main` může `void`vrátit :</span><span class="sxs-lookup"><span data-stu-id="72842-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="72842-104">Může také vrátit `int`:</span><span class="sxs-lookup"><span data-stu-id="72842-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="72842-105">Pokud se návratová hodnota z `Main` `void` nepoužívá, vrácení umožňuje mírně jednodušší kód.</span><span class="sxs-lookup"><span data-stu-id="72842-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="72842-106">Vrácení celého čísla však umožňuje programu sdělit informace o stavu jiným programům nebo skriptům, které vyvolávají spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="72842-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="72842-107">Vrácená hodnota `Main` z je považována za ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="72842-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="72842-108">Pokud `void` je `Main` vrácena z ukončovací kód bude implicitně `0`.</span><span class="sxs-lookup"><span data-stu-id="72842-108">If `void` is returned from `Main` the exit code will be implicitly `0`.</span></span> <span data-ttu-id="72842-109">Následující příklad ukazuje, jak `Main` lze získat přístup k vrácené hodnotě z.</span><span class="sxs-lookup"><span data-stu-id="72842-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="72842-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="72842-110">Example</span></span>

<span data-ttu-id="72842-111">Tento příklad používá nástroje příkazového řádku [.NET Core.](../../../core/index.md)</span><span class="sxs-lookup"><span data-stu-id="72842-111">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="72842-112">Pokud nejste obeznámeni s nástroji příkazového řádku .NET Core, můžete se o nich dozvědět v tomto [tématu Začínáme](../../../core/tutorials/cli-create-console-app.md).</span><span class="sxs-lookup"><span data-stu-id="72842-112">If you are unfamiliar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/cli-create-console-app.md).</span></span>

<span data-ttu-id="72842-113">Metodu `Main` v *program.cs* upravte takto:</span><span class="sxs-lookup"><span data-stu-id="72842-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="72842-114">Při spuštění programu v systému Windows je `Main` jakákoli hodnota vrácená z funkce uložena v proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="72842-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="72842-115">Tuto proměnnou prostředí lze `ERRORLEVEL` načíst pomocí `$LastExitCode` dávkového souboru nebo z prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72842-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="72842-116">Aplikaci můžete sestavit pomocí příkazu [dotnet CLI.](../../../core/tools/dotnet.md) `dotnet build`</span><span class="sxs-lookup"><span data-stu-id="72842-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="72842-117">Dále vytvořte skript Powershellu pro spuštění aplikace a zobrazení výsledku.</span><span class="sxs-lookup"><span data-stu-id="72842-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="72842-118">Vložte následující kód do textového `test.ps1` souboru a uložte jej jako ve složce, která obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="72842-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="72842-119">Spusťte skript powershellu zadáním `test.ps1` na výzvu powershellu.</span><span class="sxs-lookup"><span data-stu-id="72842-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="72842-120">Vzhledem k tomu, že kód vrátí nulu, dávkový soubor bude hlásit úspěch.</span><span class="sxs-lookup"><span data-stu-id="72842-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="72842-121">Pokud však změníte MainReturnValTest.cs vrátíte nenulovou hodnotu a potom program znovu zkompilujete, následné spuštění skriptu prostředí PowerShell oznámí chybu.</span><span class="sxs-lookup"><span data-stu-id="72842-121">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="72842-122">Ukázkový výstup</span><span class="sxs-lookup"><span data-stu-id="72842-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="72842-123">Asynchronní hlavní vrácené hodnoty</span><span class="sxs-lookup"><span data-stu-id="72842-123">Async Main return values</span></span>

<span data-ttu-id="72842-124">Asynchronní hlavní vrácené hodnoty přesunout často používaný kód `Main` potřebný pro volání asynchronní metody v kódu generovanékompilátorem.</span><span class="sxs-lookup"><span data-stu-id="72842-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="72842-125">Dříve budete muset napsat tuto konstrukci volat asynchronní kód a ujistěte se, že program běžel, dokud asynchronní operace dokončena:</span><span class="sxs-lookup"><span data-stu-id="72842-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="72842-126">Nyní může být nahrazen:</span><span class="sxs-lookup"><span data-stu-id="72842-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="72842-127">Výhodou nové syntaxe je, že kompilátor vždy generuje správný kód.</span><span class="sxs-lookup"><span data-stu-id="72842-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="72842-128">Kód generovaný kompilátorem</span><span class="sxs-lookup"><span data-stu-id="72842-128">Compiler generated code</span></span>

<span data-ttu-id="72842-129">Pokud vstupní bod aplikace `Task` `Task<int>`vrátí a , kompilátor vygeneruje nový vstupní bod, který volá metodu vstupního bodu deklarovanou v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="72842-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="72842-130">Za předpokladu, že `$GeneratedMain`je tento vstupní bod volán , kompilátor generuje následující kód pro tyto vstupní body:</span><span class="sxs-lookup"><span data-stu-id="72842-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="72842-131">`static Task Main()`výsledkem je, že kompilátor vyzařuje ekvivalent`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="72842-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="72842-132">`static Task Main(string[])`výsledkem je, že kompilátor vyzařuje ekvivalent`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="72842-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="72842-133">`static Task<int> Main()`výsledkem je, že kompilátor vyzařuje ekvivalent`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="72842-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="72842-134">`static Task<int> Main(string[])`výsledkem je, že kompilátor vyzařuje ekvivalent`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="72842-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="72842-135">Pokud jsou použity `async` příklady `Main` modifikátor u metody, kompilátor by generovat stejný kód.</span><span class="sxs-lookup"><span data-stu-id="72842-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="72842-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="72842-136">See also</span></span>

- [<span data-ttu-id="72842-137">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="72842-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="72842-138">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="72842-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="72842-139">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="72842-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="72842-140">Jak zobrazit argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="72842-140">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
