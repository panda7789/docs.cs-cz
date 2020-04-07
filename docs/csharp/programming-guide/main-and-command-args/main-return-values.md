---
title: Main() Návratové hodnoty - Průvodce programováním Jazyka C#
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 7061b6c1988da9f6dfac115ee555a914531df863
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805925"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="972a9-102">Main() vrácené hodnoty (Průvodce programováním Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="972a9-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="972a9-103">Metoda `Main` může `void`vrátit :</span><span class="sxs-lookup"><span data-stu-id="972a9-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="972a9-104">Může také vrátit `int`:</span><span class="sxs-lookup"><span data-stu-id="972a9-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="972a9-105">Pokud se návratová hodnota z `Main` `void` nepoužívá, vrácení umožňuje mírně jednodušší kód.</span><span class="sxs-lookup"><span data-stu-id="972a9-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="972a9-106">Vrácení celého čísla však umožňuje programu sdělit informace o stavu jiným programům nebo skriptům, které vyvolávají spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="972a9-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="972a9-107">Vrácená hodnota `Main` z je považována za ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="972a9-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="972a9-108">Pokud `void` je `Main`vrácena z , ukončovací kód bude implicitně `0`.</span><span class="sxs-lookup"><span data-stu-id="972a9-108">If `void` is returned from `Main`, the exit code will be implicitly `0`.</span></span> <span data-ttu-id="972a9-109">Následující příklad ukazuje, jak `Main` lze získat přístup k vrácené hodnotě z.</span><span class="sxs-lookup"><span data-stu-id="972a9-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="972a9-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="972a9-110">Example</span></span>

<span data-ttu-id="972a9-111">Tento příklad používá nástroje příkazového řádku [.NET Core.](../../../core/index.yml)</span><span class="sxs-lookup"><span data-stu-id="972a9-111">This example uses [.NET Core](../../../core/index.yml) command-line tools.</span></span> <span data-ttu-id="972a9-112">Pokud nejste obeznámeni s nástroji příkazového řádku .NET Core, můžete se o nich dozvědět v tomto [článku s informacemi](../../../core/tutorials/cli-create-console-app.md)o začátku .</span><span class="sxs-lookup"><span data-stu-id="972a9-112">If you are unfamiliar with .NET Core command-line tools, you can learn about them in this [get-started article](../../../core/tutorials/cli-create-console-app.md).</span></span>

<span data-ttu-id="972a9-113">Metodu `Main` v *program.cs* upravte takto:</span><span class="sxs-lookup"><span data-stu-id="972a9-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="972a9-114">Při spuštění programu v systému Windows je `Main` jakákoli hodnota vrácená z funkce uložena v proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="972a9-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="972a9-115">Tuto proměnnou prostředí lze `ERRORLEVEL` načíst pomocí `$LastExitCode` dávkového souboru nebo z prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="972a9-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="972a9-116">Aplikaci můžete sestavit pomocí příkazu [dotnet CLI.](../../../core/tools/dotnet.md) `dotnet build`</span><span class="sxs-lookup"><span data-stu-id="972a9-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="972a9-117">Dále vytvořte skript Powershellu pro spuštění aplikace a zobrazení výsledku.</span><span class="sxs-lookup"><span data-stu-id="972a9-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="972a9-118">Vložte následující kód do textového `test.ps1` souboru a uložte jej jako ve složce, která obsahuje projekt.</span><span class="sxs-lookup"><span data-stu-id="972a9-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="972a9-119">Spusťte skript powershellu zadáním `test.ps1` na výzvu powershellu.</span><span class="sxs-lookup"><span data-stu-id="972a9-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="972a9-120">Vzhledem k tomu, že kód vrátí nulu, dávkový soubor bude hlásit úspěch.</span><span class="sxs-lookup"><span data-stu-id="972a9-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="972a9-121">Pokud však změníte MainReturnValTest.cs vrátíte nenulovou hodnotu a potom program znovu zkompilujete, následné spuštění skriptu prostředí PowerShell nahlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="972a9-121">However, if you change MainReturnValTest.cs to return a non-zero value and then recompile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="972a9-122">Ukázkový výstup</span><span class="sxs-lookup"><span data-stu-id="972a9-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="972a9-123">Asynchronní hlavní vrácené hodnoty</span><span class="sxs-lookup"><span data-stu-id="972a9-123">Async Main return values</span></span>

<span data-ttu-id="972a9-124">Asynchronní hlavní vrácené hodnoty přesunout často používaný kód `Main` potřebný pro volání asynchronní metody v kódu generovanékompilátorem.</span><span class="sxs-lookup"><span data-stu-id="972a9-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="972a9-125">Dříve budete muset napsat tuto konstrukci volat asynchronní kód a ujistěte se, že program běžel, dokud asynchronní operace dokončena:</span><span class="sxs-lookup"><span data-stu-id="972a9-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="972a9-126">Nyní může být nahrazen:</span><span class="sxs-lookup"><span data-stu-id="972a9-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="972a9-127">Výhodou nové syntaxe je, že kompilátor vždy generuje správný kód.</span><span class="sxs-lookup"><span data-stu-id="972a9-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="972a9-128">Kód generovaný kompilátorem</span><span class="sxs-lookup"><span data-stu-id="972a9-128">Compiler-generated code</span></span>

<span data-ttu-id="972a9-129">Pokud vstupní bod aplikace `Task` `Task<int>`vrátí a , kompilátor vygeneruje nový vstupní bod, který volá metodu vstupního bodu deklarovanou v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="972a9-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="972a9-130">Za předpokladu, že `$GeneratedMain`je tento vstupní bod volán , kompilátor generuje následující kód pro tyto vstupní body:</span><span class="sxs-lookup"><span data-stu-id="972a9-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="972a9-131">`static Task Main()`výsledkem je, že kompilátor vyzařuje ekvivalent`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="972a9-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="972a9-132">`static Task Main(string[])`výsledkem je, že kompilátor vyzařuje ekvivalent`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="972a9-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="972a9-133">`static Task<int> Main()`výsledkem je, že kompilátor vyzařuje ekvivalent`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="972a9-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="972a9-134">`static Task<int> Main(string[])`výsledkem je, že kompilátor vyzařuje ekvivalent`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="972a9-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="972a9-135">Pokud jsou použity `async` příklady `Main` modifikátor u metody, kompilátor by generovat stejný kód.</span><span class="sxs-lookup"><span data-stu-id="972a9-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="972a9-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="972a9-136">See also</span></span>

- [<span data-ttu-id="972a9-137">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="972a9-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="972a9-138">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="972a9-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="972a9-139">Hlavní() a Argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="972a9-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="972a9-140">Jak zobrazit argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="972a9-140">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
