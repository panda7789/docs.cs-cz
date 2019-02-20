---
title: Co je nového v .NET Core 3.0
description: Informace o nových funkcích v rozhraní .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/31/2018
ms.openlocfilehash: 47a5ae3e81b0320a094ecc79e6b08035de66e785
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56443072"
---
# <a name="whats-new-in-net-core-30-preview-2"></a><span data-ttu-id="45914-103">Co je nového v .NET Core 3.0 (ve verzi Preview 2)</span><span class="sxs-lookup"><span data-stu-id="45914-103">What's new in .NET Core 3.0 (Preview 2)</span></span>

<span data-ttu-id="45914-104">Tento článek popisuje, co je nového v .NET Core 3.0 (ve verzi preview 2).</span><span class="sxs-lookup"><span data-stu-id="45914-104">This article describes what is new in .NET Core 3.0 (preview 2).</span></span> <span data-ttu-id="45914-105">Jedním z největších vylepšení je podpora aplikací klasické pracovní plochy Windows (jenom Windows).</span><span class="sxs-lookup"><span data-stu-id="45914-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="45914-106">S využitím .NET Core 3.0 SDK komponenty s názvem Windows Desktop, můžete port formulářů Windows a aplikace Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="45914-106">By utilizing a .NET Core 3.0 SDK component called Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="45914-107">Jasno, komponenta Windows Desktop pouze podporované a součástí Windows.</span><span class="sxs-lookup"><span data-stu-id="45914-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="45914-108">Další informace najdete v části [Windows desktop](#windows-desktop) níže.</span><span class="sxs-lookup"><span data-stu-id="45914-108">For more information, see the section [Windows desktop](#windows-desktop) below.</span></span>

<span data-ttu-id="45914-109">Přidává podporu pro .NET core 3.0 C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="45914-109">.NET Core 3.0 adds support for C# 8.0.</span></span>

<span data-ttu-id="45914-110">[Stáhnout a začít pracovat s .NET Core 3.0 ve verzi Preview 2](https://aka.ms/netcore3download) teď na Windows, Mac a Linux.</span><span class="sxs-lookup"><span data-stu-id="45914-110">[Download and get started with .NET Core 3.0 Preview 2](https://aka.ms/netcore3download) right now on Windows, Mac and Linux.</span></span> <span data-ttu-id="45914-111">Zobrazí se podrobné informace o verzi v [poznámky k verzi .NET Core 3.0 ve verzi Preview 2](https://aka.ms/netcore3releasenotes).</span><span class="sxs-lookup"><span data-stu-id="45914-111">You can see complete details of the release in the [.NET Core 3.0 Preview 2 release notes](https://aka.ms/netcore3releasenotes).</span></span>

<span data-ttu-id="45914-112">Další informace o co bylo vydáno se sadou jednotlivé verze najdete v následující oznámení:</span><span class="sxs-lookup"><span data-stu-id="45914-112">For more information about what was released with each version, see the following announcements:</span></span>

- [<span data-ttu-id="45914-113">.NET core 3.0 ve verzi Preview 1 oznámení</span><span class="sxs-lookup"><span data-stu-id="45914-113">.NET Core 3.0 Preview 1 announcement</span></span>](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)
- [<span data-ttu-id="45914-114">.NET core 3.0 ve verzi Preview 2 oznámení</span><span class="sxs-lookup"><span data-stu-id="45914-114">.NET Core 3.0 Preview 2 announcement</span></span>](https://blogs.msdn.microsoft.com/dotnet/2019/01/29/announcing-net-core-3-preview-2/)

## <a name="c-8"></a><span data-ttu-id="45914-115">C# 8</span><span class="sxs-lookup"><span data-stu-id="45914-115">C# 8</span></span>

<span data-ttu-id="45914-116">.NET core 3.0 podporuje C# 8 a od .NET Core 3.0 ve verzi Preview 2 podporuje tyto nové funkce.</span><span class="sxs-lookup"><span data-stu-id="45914-116">.NET Core 3.0 supports C# 8, and as of .NET Core 3.0 Preview 2, supports these new features.</span></span> <span data-ttu-id="45914-117">Další informace o C# 8.0 funkce, najdete v těchto příspěvcích na blogu:</span><span class="sxs-lookup"><span data-stu-id="45914-117">For more information about C# 8.0 features, see the following blog posts:</span></span>

- [<span data-ttu-id="45914-118">Lepší využití vzorů v C# 8.0</span><span class="sxs-lookup"><span data-stu-id="45914-118">Do more with patterns in C# 8.0</span></span>](https://blogs.msdn.microsoft.com/dotnet/2019/01/24/do-more-with-patterns-in-c-8-0/)
- [<span data-ttu-id="45914-119">Využijte C# 8.0 pro typu číselník</span><span class="sxs-lookup"><span data-stu-id="45914-119">Take C# 8.0 for a spin</span></span>](https://blogs.msdn.microsoft.com/dotnet/2018/12/05/take-c-8-0-for-a-spin/)
- [<span data-ttu-id="45914-120">Vytváření C# 8.0</span><span class="sxs-lookup"><span data-stu-id="45914-120">Building C# 8.0</span></span>](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/)


### <a name="ranges-and-indices"></a><span data-ttu-id="45914-121">Rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="45914-121">Ranges and indices</span></span>

<span data-ttu-id="45914-122">Nové `Index` typ lze použít k indexování.</span><span class="sxs-lookup"><span data-stu-id="45914-122">The new `Index` type can be used for indexing.</span></span> <span data-ttu-id="45914-123">Můžete je vytvořit z `int` , které se počítá od začátku, nebo s předponou `^` – operátor (C#), které se počítá od konce:</span><span class="sxs-lookup"><span data-stu-id="45914-123">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="45914-124">K dispozici je také `Range` typ, který se skládá ze dvou `Index` hodnoty, jeden pro spuštění a jeden pro ukončení a může být zapsaný s `x..y` výrazu v rozsahu (C#).</span><span class="sxs-lookup"><span data-stu-id="45914-124">There is also a `Range` type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="45914-125">Potom můžete index s využitím `Range` aby vytvářela řez:</span><span class="sxs-lookup"><span data-stu-id="45914-125">You can then index with a `Range` in order to produce a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

### <a name="async-streams"></a><span data-ttu-id="45914-126">Asynchronní datové proudy</span><span class="sxs-lookup"><span data-stu-id="45914-126">Async streams</span></span>

<span data-ttu-id="45914-127">`IAsyncEnumerable<T>` Typ je nový asynchronní verze `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="45914-127">The `IAsyncEnumerable<T>` type is a new asynchronous version of `IEnumerable<T>`.</span></span> <span data-ttu-id="45914-128">Jazyk umožňuje `await foreach` přes `IAsyncEnumerable<T>` využívat jejich prvky a použití `yield return` k nim pro produkci prvků.</span><span class="sxs-lookup"><span data-stu-id="45914-128">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="45914-129">Následující příklad ukazuje produkční scénáře i využití asynchronních streamů.</span><span class="sxs-lookup"><span data-stu-id="45914-129">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="45914-130">`foreach` Příkaz je asynchronní a sama používá `yield return` vytvoří na asynchronní datový proud pro volající.</span><span class="sxs-lookup"><span data-stu-id="45914-130">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="45914-131">Tento model (pomocí `yield return`) je doporučený model pro vytváření asynchronních streamů.</span><span class="sxs-lookup"><span data-stu-id="45914-131">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="45914-132">Kromě toho, že možnost `await foreach`, můžete také vytvořit asynchronní iterátory, například iterátoru, který vrátí `IAsyncEnumerable/IAsyncEnumerator` , můžete obě `await` a `yield` v.</span><span class="sxs-lookup"><span data-stu-id="45914-132">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="45914-133">Pro objekty, které je potřeba se dá uvolnit, můžete použít `IAsyncDisposable`, které různé typy BCL implementovat jako `Stream` a `Timer`.</span><span class="sxs-lookup"><span data-stu-id="45914-133">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

>[!NOTE]
><span data-ttu-id="45914-134">Je třeba .NET Core 3.0 ve verzi Preview 2 použít asynchronní datové proudy, pokud chcete vyvíjet pomocí sady Visual Studio. 2019 ve verzi Preview 2 nebo verzi preview [ C# rozšíření pro Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5).</span><span class="sxs-lookup"><span data-stu-id="45914-134">You need .NET Core 3.0 Preview 2 to use async streams if you want to develop with either Visual Studio 2019 Preview 2 or the latest preview of the [C# extension for Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5).</span></span> <span data-ttu-id="45914-135">Pokud používáte .NET Core 3.0 ve verzi Preview 2 na příkazovém řádku, pak vše, co bude fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="45914-135">If you are using .NET Core 3.0 Preview 2 at the command line, then everything will work as expected.</span></span>

### <a name="using-declarations"></a><span data-ttu-id="45914-136">Pomocí deklarace</span><span class="sxs-lookup"><span data-stu-id="45914-136">Using Declarations</span></span>

<span data-ttu-id="45914-137">*Pomocí deklarace* jsou nový způsob, jak zajistit objektu řádně vyřazen.</span><span class="sxs-lookup"><span data-stu-id="45914-137">*Using declarations* are a new way to ensure your object is properly disposed.</span></span> <span data-ttu-id="45914-138">A *using – deklarace* zachová objektu aktivní, i když je stále v oboru.</span><span class="sxs-lookup"><span data-stu-id="45914-138">A *using declaration* keeps the object alive while it is still in scope.</span></span> <span data-ttu-id="45914-139">Jakmile se objekt stane mimo rozsah, je automaticky uvolněn.</span><span class="sxs-lookup"><span data-stu-id="45914-139">Once the object becomes out of scope, it is automatically disposed.</span></span> <span data-ttu-id="45914-140">Tím se sníží vnořené *příkazy using* a ujistěte se, váš kód čistější.</span><span class="sxs-lookup"><span data-stu-id="45914-140">This will reduce nested *using statements* and make your code cleaner.</span></span>

```csharp
static void Main(string[] args)
{
    using var options = Parse(args);
    if (options["verbose"]) { WriteLine("Logging..."); }

} // options disposed here
```

### <a name="switch-expressions"></a><span data-ttu-id="45914-141">Přepnout výrazy</span><span class="sxs-lookup"><span data-stu-id="45914-141">Switch Expressions</span></span>

<span data-ttu-id="45914-142">*Přepnout výrazy* čistší způsob, jak to uděláte *switch – příkaz* ale, protože se jedná výraz vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="45914-142">*Switch expressions* are a cleaner way of doing a *switch statement* but, since it's an expression, returns a value.</span></span> <span data-ttu-id="45914-143">*Přepnout výrazy* jsou také plně integrované s porovnáváním vzorů a použití vzoru zahození `_`, znázornit `default` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="45914-143">*Switch expressions* are also fully integrated with pattern matching, and use the discard pattern, `_`, to represent the `default` value.</span></span>

<span data-ttu-id="45914-144">Zobrazí se syntaxe *přepnout výrazy* v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="45914-144">You can see the syntax for *switch expressions* in the following example:</span></span>

```csharp
static string Display(object o) => o switch
{
    Point { X: 0, Y: 0 }         => "origin",
    Point { X: var x, Y: var y } => $"({x}, {y})",
    _                            => "unknown"
};
```

<span data-ttu-id="45914-145">Existují dva způsoby hrají v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="45914-145">There are two patterns at play in this example.</span></span> <span data-ttu-id="45914-146">`o` nejprve odpovídá `Point` *vzorek typu* a pak se *vzor pro vlastnost* uvnitř *{složených závorek}*.</span><span class="sxs-lookup"><span data-stu-id="45914-146">`o` first matches with the `Point` *type pattern* and then with the *property pattern* inside the *{curly braces}*.</span></span> <span data-ttu-id="45914-147">`_` Popisuje `discard pattern`, což je stejná jako `default` pro *příkazy switch*.</span><span class="sxs-lookup"><span data-stu-id="45914-147">The `_` describes the `discard pattern`, which is the same as `default` for *switch statements*.</span></span>

<span data-ttu-id="45914-148">Vzorky umožňují napsat deklarativního kódu, který zachycuje máte v úmyslu namísto kódu procedury, která implementuje testy pro něj.</span><span class="sxs-lookup"><span data-stu-id="45914-148">Patterns enable you to write declarative code that captures your intent instead of procedural code that implements tests for it.</span></span> <span data-ttu-id="45914-149">Kompilátoru je zodpovědný za implementace tohoto kódu nudné procedury a je zaručeno, že vždy provést správně.</span><span class="sxs-lookup"><span data-stu-id="45914-149">The compiler becomes responsible for implementing that boring procedural code and is guaranteed to always do it correctly.</span></span>

<span data-ttu-id="45914-150">Nadále bude případů kde *příkazy switch* bude vhodnější než *přepnout výrazy* a vzorky lze použít s obou stylů syntaxe.</span><span class="sxs-lookup"><span data-stu-id="45914-150">There will still be cases where *switch statements* will be a better choice than *switch expressions* and patterns can be used with both syntax styles.</span></span>

<span data-ttu-id="45914-151">Další informace najdete v tématu [udělat více s vzory v C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2019/01/24/do-more-with-patterns-in-c-8-0/).</span><span class="sxs-lookup"><span data-stu-id="45914-151">For more information, see [Do more with patterns in C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2019/01/24/do-more-with-patterns-in-c-8-0/).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="45914-152">Vylepšení plovoucí desetinné čárky IEEE</span><span class="sxs-lookup"><span data-stu-id="45914-152">IEEE Floating-point improvements</span></span>

<span data-ttu-id="45914-153">Číslo s plovoucí čárkou bodu rozhraní API se právě aktualizují dodržovat [IEEE 754-2008 revize](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="45914-153">Floating point APIs are in the process of being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="45914-154">Cílem těchto změn je vystavit všechny operace "povinné" a ujistěte se, že jsou behaviorally kompatibilní s specifikace IEEE.</span><span class="sxs-lookup"><span data-stu-id="45914-154">The goal of these changes is to expose all "required" operations and ensure that they are behaviorally compliant with the IEEE spec.</span></span>

<span data-ttu-id="45914-155">Analýza a formátování opravy:</span><span class="sxs-lookup"><span data-stu-id="45914-155">Parsing and formatting fixes:</span></span>

* <span data-ttu-id="45914-156">Správně analyzovat a zaokrouhlit vstupů o libovolné délce.</span><span class="sxs-lookup"><span data-stu-id="45914-156">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="45914-157">Správně analyzovat a formátování záporná nula.</span><span class="sxs-lookup"><span data-stu-id="45914-157">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="45914-158">Díky kontrole velkých a malých písmen a povolení volitelné předcházející správně analyzovat nekonečno a NaN `+` kde je to možné.</span><span class="sxs-lookup"><span data-stu-id="45914-158">Correctly parse Infinity and NaN by performing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="45914-159">Mají nového rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="45914-159">New Math APIs have:</span></span>

* `BitIncrement/BitDecrement`\
<span data-ttu-id="45914-160">Odpovídá `nextUp` a `nextDown` IEEE operace.</span><span class="sxs-lookup"><span data-stu-id="45914-160">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="45914-161">Vrátí nejmenší s plovoucí desetinnou čárkou čísla, která porovnává větší nebo menší než vstup (v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="45914-161">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="45914-162">Například `Math.BitIncrement(0.0)` vracel `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="45914-162">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* `MaxMagnitude/MinMagnitude`\
<span data-ttu-id="45914-163">Odpovídá `maxNumMag` a `minNumMag` IEEE operace, vrátí hodnotu, která je větší nebo menší řádově dva vstupy (v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="45914-163">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="45914-164">Například `Math.MaxMagnitude(2.0, -3.0)` vracel `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="45914-164">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* `ILogB`\
<span data-ttu-id="45914-165">Odpovídá `logB` IEEE operace, která vrátí celé číslo, vrátí integrální protokolu základu 2 vstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="45914-165">Corresponds to the `logB` IEEE operation which returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="45914-166">To je v podstatě totéž jako `floor(log2(x))`, ale ukončili minimální zaokrouhlovací chyby.</span><span class="sxs-lookup"><span data-stu-id="45914-166">This is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* `ScaleB`\
<span data-ttu-id="45914-167">Odpovídá `scaleB` IEEE operace, která přebírá celé číslo, vrátí efektivně `x * pow(2, n)`, ale se provádí s minimálními zaokrouhlovací chyby.</span><span class="sxs-lookup"><span data-stu-id="45914-167">Corresponds to the `scaleB` IEEE operation which takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* `Log2`\
<span data-ttu-id="45914-168">Odpovídá `log2` IEEE operace Vrátí logaritmus o základu 2.</span><span class="sxs-lookup"><span data-stu-id="45914-168">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="45914-169">Minimalizuje zaokrouhlovací chyby.</span><span class="sxs-lookup"><span data-stu-id="45914-169">It minimizes rounding error.</span></span>

* `FusedMultiplyAdd`\
<span data-ttu-id="45914-170">Odpovídá `fma` IEEE operace provádí roztaveného vynásobit sčítanec.</span><span class="sxs-lookup"><span data-stu-id="45914-170">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="45914-171">To znamená, že nemá `(x * y) + z` jako jediná operace, existuje-minimalizací zaokrouhlovací chyby.</span><span class="sxs-lookup"><span data-stu-id="45914-171">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="45914-172">Příkladem může být `FusedMultiplyAdd(1e308, 2.0, -1e308)` která vrací `1e308`.</span><span class="sxs-lookup"><span data-stu-id="45914-172">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="45914-173">Standardní `(1e308 * 2.0) - 1e308` vrátí `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="45914-173">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* `CopySign`\
<span data-ttu-id="45914-174">Odpovídá `copySign` IEEE operace, vrátí hodnotu `x`, ale s znaménko `y`.</span><span class="sxs-lookup"><span data-stu-id="45914-174">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="45914-175">Závislé vnitřní funkce platformy .NET</span><span class="sxs-lookup"><span data-stu-id="45914-175">.NET Platform Dependent Intrinsics</span></span>

<span data-ttu-id="45914-176">Rozhraní API nepřidali, která umožňují přístup k určité pokyny orientované výkonu procesoru, jako **SIMD** nebo **Bit zpracování instrukcí** nastaví.</span><span class="sxs-lookup"><span data-stu-id="45914-176">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="45914-177">Tyto pokyny mohou pomoci dosáhnout zvýšení výkonu velkých objemů v některých scénářích, jako je zpracování dat, efektivně paralelně.</span><span class="sxs-lookup"><span data-stu-id="45914-177">These instructions can help achieve big performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> <span data-ttu-id="45914-178">Kromě zpřístupnění k použití rozhraní API pro vaše programy, jste začali na knihovny .NET, podle těchto pokynů ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="45914-178">In addition to exposing the APIs for your programs to use, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="45914-179">Následující žádosti o přijetí změn CoreCLR ukazují některé vnitřní objekty, buď prostřednictvím implementace nebo použijte:</span><span class="sxs-lookup"><span data-stu-id="45914-179">The following CoreCLR PRs demonstrate a few of the intrinsics, either via implementation or use:</span></span>

* [<span data-ttu-id="45914-180">Implementujte jednoduchý vnitřní objekty SSE2 hardwaru</span><span class="sxs-lookup"><span data-stu-id="45914-180">Implement simple SSE2 hardware intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/15585)
* [<span data-ttu-id="45914-181">Implementace vnitřní objekty SSE hardwaru</span><span class="sxs-lookup"><span data-stu-id="45914-181">Implement the SSE hardware intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/15538)
* [<span data-ttu-id="45914-182">Arm64 základního hardwaru vnitřních objektů</span><span class="sxs-lookup"><span data-stu-id="45914-182">Arm64 Base HW Intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/16822)
* [<span data-ttu-id="45914-183">Použijte TZCNT a LZCNT pro vyhledání {první | Poslední} nalezen {bajtů | Znak}</span><span class="sxs-lookup"><span data-stu-id="45914-183">Use TZCNT and LZCNT for Locate{First|Last}Found{Byte|Char}</span></span>](https://github.com/dotnet/coreclr/pull/21073)

<span data-ttu-id="45914-184">Další informace najdete v tématu [závislé vnitřní funkce platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), který definuje metodu pro definování této hardwarové infrastruktury, což Microsoft, dodavatelé čip TPM, nebo jakékoli jiné společnosti nebo jednotlivých definovat hardware/čip TPM Rozhraní API, která by měla být vystavená pro kód .NET.</span><span class="sxs-lookup"><span data-stu-id="45914-184">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), which defines an approach for defining this hardware infrastructure, allowing Microsoft, chip vendors, or any other company or individual to define hardware/chip APIs that should be exposed to .NET code.</span></span>

## <a name="default-executables"></a><span data-ttu-id="45914-185">Výchozí spustitelné soubory</span><span class="sxs-lookup"><span data-stu-id="45914-185">Default executables</span></span>

<span data-ttu-id="45914-186">.NET core se teď sestavení [závisí na architektuře spustitelných souborů](../deploying/index.md#framework-dependent-executables-fde) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="45914-186">.NET Core will now build [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="45914-187">Toto je nová pro aplikace, které používají globálně nainstalovanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45914-187">This is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="45914-188">Až doteď jenom [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) vytvoří spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="45914-188">Until now, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="45914-189">Během `dotnet build` nebo `dotnet publish`, spustitelný soubor je vytvořen, za předpokladu, který odpovídá prostředí a platforma sady SDK, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="45914-189">During `dotnet build` or `dotnet publish`, an executable is created provided that matches the environment and platform of the SDK you are using.</span></span> <span data-ttu-id="45914-190">Můžete očekávat, že stejné operace tyto spustitelné soubory stejně jako další nativní spustitelné soubory, jako například:</span><span class="sxs-lookup"><span data-stu-id="45914-190">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="45914-191">Můžete dvakrát kliknout na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="45914-191">You can double-click on the executable.</span></span>
* <span data-ttu-id="45914-192">Aplikace z příkazového řádku můžete spustit přímo, jako například `myapp.exe` na Windows, a `./myapp` v Linuxu a macOS.</span><span class="sxs-lookup"><span data-stu-id="45914-192">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="45914-193">Vytvoření kopie závislosti</span><span class="sxs-lookup"><span data-stu-id="45914-193">Build copies dependencies</span></span>

<span data-ttu-id="45914-194">`dotnet build` Nyní zkopíruje závislostí NuGet pro vaši aplikaci z mezipaměti NuGet k výstupní složce sestavení.</span><span class="sxs-lookup"><span data-stu-id="45914-194">`dotnet build` now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="45914-195">Dříve byly závislosti pouze zkopírovány jako součást `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="45914-195">Previously, dependencies were only copied as part of `dotnet publish`.</span></span> 

<span data-ttu-id="45914-196">Existují některé operace, jako je stránka propojení a razor publikování, který se stále vyžadují publikování.</span><span class="sxs-lookup"><span data-stu-id="45914-196">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>


## <a name="local-dotnet-tools"></a><span data-ttu-id="45914-197">Nástroje pro místní dotnet</span><span class="sxs-lookup"><span data-stu-id="45914-197">Local dotnet tools</span></span>

>[!WARNING]
><span data-ttu-id="45914-198">Došlo ke změně v .NET Core místní nástroje .NET Core 3.0 ve verzi Preview 1 až .NET Core 3.0 ve verzi Preview 2.</span><span class="sxs-lookup"><span data-stu-id="45914-198">There was a change in .NET Core Local Tools between .NET Core 3.0 Preview 1 and .NET Core 3.0 Preview 2.</span></span>  <span data-ttu-id="45914-199">Pokud jste si vyzkoušeli místní nástroje ve verzi Preview 1 spuštěním příkazu jako `dotnet tool restore` nebo `dotnet tool install`, musíte odstranit složky mezipaměti místního nástroje před místní nástroje bude správně fungovat ve verzi Preview 2.</span><span class="sxs-lookup"><span data-stu-id="45914-199">If you tried out local tools in Preview 1 by running a command like `dotnet tool restore` or `dotnet tool install`, you need to delete your local tools cache folder before local tools will work correctly in Preview 2.</span></span> <span data-ttu-id="45914-200">Tato složka nachází tady:</span><span class="sxs-lookup"><span data-stu-id="45914-200">This folder is located at:</span></span>
>
><span data-ttu-id="45914-201">Na počítači mac, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="45914-201">On mac, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
><span data-ttu-id="45914-202">Ve Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="45914-202">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>
>
><span data-ttu-id="45914-203">Pokud tato složka neodstraníte, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="45914-203">If you do not delete this folder, you will receive an error.</span></span>

<span data-ttu-id="45914-204">I když .NET Core 2.1 podporuje globální nástroje, .NET Core 3.0 teď má místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="45914-204">While .NET Core 2.1 supported global tools, .NET Core 3.0 now has local tools.</span></span> <span data-ttu-id="45914-205">Místní nástroje se podobají globální nástroje, ale jsou spojeny s konkrétní umístění na disku.</span><span class="sxs-lookup"><span data-stu-id="45914-205">Local tools are similar to global tools but are associated with a particular location on disk.</span></span> <span data-ttu-id="45914-206">Díky tomu jednotlivých projektů a nástrojů na úložiště.</span><span class="sxs-lookup"><span data-stu-id="45914-206">This enables per-project and per-repository tooling.</span></span> <span data-ttu-id="45914-207">Libovolný nástroj nainstalovaný místně není k dispozici globálně.</span><span class="sxs-lookup"><span data-stu-id="45914-207">Any tool installed locally isn't available globally.</span></span> <span data-ttu-id="45914-208">Nástroje se distribuují jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="45914-208">Tools are distributed as NuGet packages.</span></span>

<span data-ttu-id="45914-209">Místní nástroje spoléhají na název souboru manifestu `dotnet-tools.json` v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="45914-209">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="45914-210">Tento soubor manifestu definuje nástroje k dispozici v této složce a níže.</span><span class="sxs-lookup"><span data-stu-id="45914-210">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="45914-211">Vytvořením tento soubor manifestu v kořenovém adresáři vašeho úložiště, zajistíte všem uživatelům klonování kódu obnovit a použít nástroje, které jsou potřeba k úspěšné práci s kódem.</span><span class="sxs-lookup"><span data-stu-id="45914-211">By creating this manifest file at the root of your repository, you ensure anyone cloning your code can restore and use the tools that are needed to successfully work with your code.</span></span>

<span data-ttu-id="45914-212">Chcete-li vytvořit `dotnet-tools.json` soubor manifestu, použijte:</span><span class="sxs-lookup"><span data-stu-id="45914-212">To create a `dotnet-tools.json` manifest file, use:</span></span>

```console
dotnet new tool-manifest
```

<span data-ttu-id="45914-213">Přidejte nový nástroj manifest místní pomocí:</span><span class="sxs-lookup"><span data-stu-id="45914-213">Add a new tool to the local manifest with:</span></span>

```console
dotnet tool install <packageId>
```

<span data-ttu-id="45914-214">Můžete také zařadit nástroje v místní manifestu pomocí:</span><span class="sxs-lookup"><span data-stu-id="45914-214">You can also list the tools in the local manifest with:</span></span>

```console
dotnet tool list
```

<span data-ttu-id="45914-215">Pokud chcete zobrazit, jaké nástroje jsou nainstalovány globálně, použijte:</span><span class="sxs-lookup"><span data-stu-id="45914-215">To see what tools are installed globally, use:</span></span>

```console
dotnet tool list -g
```

<span data-ttu-id="45914-216">Když místní nástroje manifest soubor je k dispozici, ale nebyly nainstalovány nástroje definované v manifestu, použijte následující příkaz automaticky stáhnout a nainstalovat tyto nástroje:</span><span class="sxs-lookup"><span data-stu-id="45914-216">When the local tools manifest file is available, but the tools defined in the manifest have not been installed, use the following command to automatically download and install those tools:</span></span>

```console
dotnet tool restore
```

<span data-ttu-id="45914-217">Místní nástroj spusťte pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="45914-217">Run a local tool with the following command:</span></span>

```console
dotnet tool run <tool-command-name>
```

<span data-ttu-id="45914-218">Při spuštění místní nástroj vyhledá dotnet manifestu do aktuální adresářovou strukturu.</span><span class="sxs-lookup"><span data-stu-id="45914-218">When a local tool is run, dotnet searches for a manifest up the current directory structure.</span></span> <span data-ttu-id="45914-219">Když je nalezen soubor manifestu nástroj, se hledá požadovaný nástroj.</span><span class="sxs-lookup"><span data-stu-id="45914-219">When a tool manifest file is found, it is searched for the requested tool.</span></span> <span data-ttu-id="45914-220">Pokud nástroj je nalezena v manifestu, ale ne do mezipaměti, uživateli se zobrazí chyba a je potřeba spustit `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="45914-220">If the tool is found in the manifest, but not the cache, the user receives an error and needs to run `dotnet tool restore`.</span></span>

<span data-ttu-id="45914-221">Nástroj pro odebrání souboru manifestu místní nástroje, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="45914-221">To remove a tool from the local tool manifest file, run the following command:</span></span>

```console
dotnet tool uninstall <packageId>
```

<span data-ttu-id="45914-222">Soubor manifestu nástroje je navržena k umožnění ruční úpravě – které můžete využít k aktualizaci požadovaná verze pro práci s úložištěm.</span><span class="sxs-lookup"><span data-stu-id="45914-222">The tool manifest file is designed to allow hand editing – which you might do to update the required version for working with the repository.</span></span> <span data-ttu-id="45914-223">Tady je příklad `dotnet-tools.json` souboru:</span><span class="sxs-lookup"><span data-stu-id="45914-223">Here is an example `dotnet-tools.json` file:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

<span data-ttu-id="45914-224">Pro globální a místní nástroje se vyžaduje kompatibilní verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="45914-224">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="45914-225">Mnoho nástrojů aktuálně na NuGet.org cílit na .NET Core Runtime 2.1.</span><span class="sxs-lookup"><span data-stu-id="45914-225">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="45914-226">Instalovat ty, globálně nebo místně, je stále třeba k instalaci [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="45914-226">To install those globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="45914-227">Plocha Windows</span><span class="sxs-lookup"><span data-stu-id="45914-227">Windows desktop</span></span>

<span data-ttu-id="45914-228">Od verze rozhraní .NET Core 3.0 ve verzi Preview 1, můžete vytvářet aplikace klasické pracovní plochy Windows pomocí technologií WPF a Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="45914-228">Starting with .NET Core 3.0 Preview 1, you can build Windows desktop applications using WPF and Windows Forms.</span></span> <span data-ttu-id="45914-229">Tyto architektury podporují také pomocí moderních ovládací prvky a Fluent stylů v knihovně Windows uživatelského rozhraní XAML (WinUI) prostřednictvím [XAML ostrovy](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="45914-229">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="45914-230">Komponenta Windows Desktop je součástí Windows .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="45914-230">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="45914-231">Můžete vytvořit novou aplikaci WPF nebo Windows Forms s následujícími `dotnet` příkazy:</span><span class="sxs-lookup"><span data-stu-id="45914-231">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="45914-232">Visual Studio. 2019 ve verzi Preview 2 přidá **nový projekt** šablon pro .NET Core 3.0 Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="45914-232">Visual Studio 2019 Preview 2 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span> <span data-ttu-id="45914-233">Návrháři se stále ještě není podporována.</span><span class="sxs-lookup"><span data-stu-id="45914-233">Designers are still not yet supported.</span></span> <span data-ttu-id="45914-234">A můžete otevřít, spuštění a ladění těchto projektů v aplikaci Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="45914-234">And you can open, launch, and debug these projects in Visual Studio 2019.</span></span>

<span data-ttu-id="45914-235">Visual Studio 2017 15.9 přidává možnost [povolit náhledy .NET Core](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/), ale budete muset zapnout tuto funkci a není podporováno.</span><span class="sxs-lookup"><span data-stu-id="45914-235">Visual Studio 2017 15.9 adds the ability to [enable .NET Core previews](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/), but you need to turn that feature on, and it's not a supported scenario.</span></span>

<span data-ttu-id="45914-236">Nové projekty jsou stejné jako existující projekty .NET Core, s několika doplňky.</span><span class="sxs-lookup"><span data-stu-id="45914-236">The new projects are the same as existing .NET Core projects, with a couple additions.</span></span> <span data-ttu-id="45914-237">Tady je porovnání základní projekt konzoly .NET Core a základního projektu Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="45914-237">Here is the comparison of the basic .NET Core console project and a basic Windows Forms and WPF project.</span></span>

<span data-ttu-id="45914-238">V projektu aplikace konzoly .NET Core, že projekt používá `Microsoft.NET.Sdk` sady SDK a deklaruje závislost na rozhraní .NET Core 3.0 prostřednictvím `netcoreapp3.0` cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="45914-238">In a .NET Core console project, the project uses the `Microsoft.NET.Sdk` SDK and declares a dependency on .NET Core 3.0 via the `netcoreapp3.0` target framework.</span></span> <span data-ttu-id="45914-239">K vytvoření aplikace pro Windows Desktop, použijte `Microsoft.NET.Sdk.WindowsDesktop` sady SDK a zvolte který uživatelského rozhraní framework použít:</span><span class="sxs-lookup"><span data-stu-id="45914-239">To create a Windows Desktop app, use the `Microsoft.NET.Sdk.WindowsDesktop` SDK and choose which UI framework to use:</span></span>

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="45914-240">Chcete-li tlačítko Windows Forms přes WPF, nastavte `UseWindowsForms` místo `UseWPF`:</span><span class="sxs-lookup"><span data-stu-id="45914-240">To choose Windows Forms over WPF, set `UseWindowsForms` instead of `UseWPF`:</span></span>

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="45914-241">Obě `UseWPF` a `UseWindowsForms` může být nastaven na `true` Pokud aplikace používá obě architektury, například když dialogové okno Windows Forms je hostování ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="45914-241">Both `UseWPF` and `UseWindowsForms` can be set to `true` if the app uses both frameworks, for example when a Windows Forms dialog is hosting a WPF control.</span></span>

<span data-ttu-id="45914-242">Podělte se prosím o svůj názor na [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) a [dotnet/jádro](https://github.com/dotnet/core/issues) úložišť.</span><span class="sxs-lookup"><span data-stu-id="45914-242">Please share your feedback on the [dotnet/winforms](https://github.com/dotnet/winforms/issues),  [dotnet/wpf](https://github.com/dotnet/wpf/issues) and [dotnet/core](https://github.com/dotnet/core/issues) repos.</span></span>

## <a name="msix-deployment-for-windows-desktop"></a><span data-ttu-id="45914-243">Nasazení MSIX for Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="45914-243">MSIX Deployment for Windows Desktop</span></span>

<span data-ttu-id="45914-244">[MSIX](https://docs.microsoft.com/windows/msix/) je nový formát balíčku aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="45914-244">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows app package format.</span></span> <span data-ttu-id="45914-245">Slouží k nasazení rozhraní .NET Core 3.0 desktopové aplikace pro Windows 10.</span><span class="sxs-lookup"><span data-stu-id="45914-245">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="45914-246">[Projekt Windows Application Packaging](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), k dispozici v sadě Visual Studio. 2019 ve verzi Preview 2, vám umožní vytvořit MSIX balíčky s [samostatná](../deploying/index.md#self-contained-deployments-scd) aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45914-246">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019 Preview 2, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

><span data-ttu-id="45914-247">Poznámka: Soubor projektu .NET Core, musíte zadat podporované moduly Runtime v `<RuntimeIdentifiers>` vlastnost:</span><span class="sxs-lookup"><span data-stu-id="45914-247">Note: The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>
```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="fast-built-in-json-support"></a><span data-ttu-id="45914-248">Rychlé integrovanou podporou JSON</span><span class="sxs-lookup"><span data-stu-id="45914-248">Fast built-in JSON support</span></span>

<span data-ttu-id="45914-249">Má spoléhat ekosystému .NET [ **Json.NET** ](https://www.newtonsoft.com/json) a dalších oblíbených knihoven JSON, které dál vhodná rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="45914-249">The .NET ecosystem has relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="45914-250">**Json.NET** používá .NET řetězce jako jeho základní datový typ, které jsou pod pokličkou UTF-16.</span><span class="sxs-lookup"><span data-stu-id="45914-250">**Json.NET** uses .NET strings as its base datatype, which are UTF-16 under the hood.</span></span>

<span data-ttu-id="45914-251">Nové integrované podpoře JSON je vysoce výkonné, nízká přidělení a na základě `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="45914-251">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="45914-252">Tři nové hlavní JSON související typy byly přidány pro .NET Core 3.0 `System.Text.Json` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="45914-252">Three new main JSON-related types have been added to .NET Core 3.0 the `System.Text.Json` namespace.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="45914-253">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="45914-253">Utf8JsonReader</span></span>

<span data-ttu-id="45914-254">`System.Text.Json.Utf8JsonReader` je vysoce výkonné, s nízkou přidělení, dopředné čtecí modul pro kódování UTF-8 kódovaný JSON čtení z textu `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="45914-254">`System.Text.Json.Utf8JsonReader` is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="45914-255">`Utf8JsonReader` Je nízké úrovně, základní typ, který můžete využít k vytváření vlastních analyzátorů a deserializers.</span><span class="sxs-lookup"><span data-stu-id="45914-255">The `Utf8JsonReader` is a foundational, low-level type, that can be leveraged to build custom parsers and deserializers.</span></span> <span data-ttu-id="45914-256">Přečtení datovou část JSON pomocí nového `Utf8JsonReader` je 2 × rychleji než při použití reader od **Json.NET**.</span><span class="sxs-lookup"><span data-stu-id="45914-256">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="45914-257">Nástroj nepřidělí dokud budete muset actualize tokeny JSON jako řetězce (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="45914-257">It does not allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="45914-258">Toto nové rozhraní API bude zahrnovat následující součásti:</span><span class="sxs-lookup"><span data-stu-id="45914-258">This new API will include the following components:</span></span>

* <span data-ttu-id="45914-259">Ve verzi Preview 1: Čtečka JSON (sekvenční přístup)</span><span class="sxs-lookup"><span data-stu-id="45914-259">In Preview 1: JSON reader (sequential access)</span></span>
* <span data-ttu-id="45914-260">Chystá: Zápis JSON, modelu DOM (RAM) objektů poco serializátor, objektů poco deserializátor</span><span class="sxs-lookup"><span data-stu-id="45914-260">Coming next: JSON writer, DOM (random access), poco serializer, poco deserializer</span></span>

<span data-ttu-id="45914-261">Tady je smyčka čtečku pro `Utf8JsonReader` , který může sloužit jako výchozí bod:</span><span class="sxs-lookup"><span data-stu-id="45914-261">Here is the basic reader loop for the `Utf8JsonReader` that can be used as a starting point:</span></span>

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

### <a name="utf8jsonwriter"></a><span data-ttu-id="45914-262">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="45914-262">Utf8JsonWriter</span></span>

<span data-ttu-id="45914-263">`System.Text.Json.Utf8JsonWriter` poskytuje vysoce výkonné, bez mezipaměti, dopředné až po zápisu kódování UTF-8, jako je JSON textu z běžných typů .NET `String`, `Int32`, a `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="45914-263">`System.Text.Json.Utf8JsonWriter` provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="45914-264">Podobně jako čtenář je modul pro zápis nízké úrovně, základní typ, který můžete využít k vytvoření vlastní serializátory.</span><span class="sxs-lookup"><span data-stu-id="45914-264">Like the reader, the writer is a foundational, low-level type, that can be leveraged to build custom serializers.</span></span> <span data-ttu-id="45914-265">Zápis datové části JSON pomocí nového `Utf8JsonWriter` je 30 80 % rychlejší než při použití modulu pro zápis z **Json.NET** a nepřidělí.</span><span class="sxs-lookup"><span data-stu-id="45914-265">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and does not allocate.</span></span>

<span data-ttu-id="45914-266">Tady je ukázkový používání `Utf8JsonWriter` , který může sloužit jako výchozí bod:</span><span class="sxs-lookup"><span data-stu-id="45914-266">Here is a sample usage of the `Utf8JsonWriter` that can be used as a starting point:</span></span>

```csharp
static int WriteJson(IBufferWriter<byte> output, long[] extraData)
{
    var json = new Utf8JsonWriter(output, state: default);

    json.WriteStartObject();

    json.WriteNumber("age", 15, escape: false);
    json.WriteString("date", DateTime.Now);
    json.WriteString("first", "John");
    json.WriteString("last", "Smith");

    json.WriteStartArray("phoneNumbers", escape: false);
    json.WriteStringValue("425-000-1212", escape: false);
    json.WriteStringValue("425-000-1213");
    json.WriteEndArray();

    json.WriteStartObject("address");
    json.WriteString("street", "1 Microsoft Way");
    json.WriteString("city", "Redmond");
    json.WriteNumber("zip", 98052);
    json.WriteEndObject();

    json.WriteStartArray("ExtraArray");
    for (var i = 0; i < extraData.Length; i++)
    {
        json.WriteNumberValue(extraData[i]);
    }
    json.WriteEndArray();

    json.WriteEndObject();

    json.Flush(isFinalBlock: true);

    return (int)json.BytesWritten;
}
```

<span data-ttu-id="45914-267">`Utf8JsonWriter` Přijímá `IBufferWriter<byte>` jako umístění výstupu synchronně zapisovat json data a abyste jako volající musí poskytnout konkrétní implementaci.</span><span class="sxs-lookup"><span data-stu-id="45914-267">The `Utf8JsonWriter` accepts `IBufferWriter<byte>` as the output location to synchronously write the json data into, and you as the caller need to provide a concrete implementation.</span></span> <span data-ttu-id="45914-268">Platformu současnosti nezahrnuje implementace tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="45914-268">The platform does not currently include an implementation of this interface.</span></span> <span data-ttu-id="45914-269">Příklad `IBufferWriter<byte>`, naleznete v tématu [https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35](https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35)</span><span class="sxs-lookup"><span data-stu-id="45914-269">For an example of `IBufferWriter<byte>`, see [https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35](https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35)</span></span>

### <a name="jsondocument"></a><span data-ttu-id="45914-270">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="45914-270">JsonDocument</span></span>

<span data-ttu-id="45914-271">`System.Text.Json.JsonDocument` je postavený na `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="45914-271">`System.Text.Json.JsonDocument` is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="45914-272">`JsonDocument` Poskytuje schopnost analyzovat JSON data a sestavení jen pro čtení Document Object Model (DOM), který může být dotazována k podporují náhodný přístup a výčet.</span><span class="sxs-lookup"><span data-stu-id="45914-272">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="45914-273">Elementy JSON, které tvoří dat přístupné prostřednictvím `JsonElement` typ, který je zveřejněný prostřednictvím `JsonDocument` jako vlastnost s názvem `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="45914-273">The JSON elements that compose the data can be accessed via the `JsonElement` type which is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="45914-274">`JsonElement` Obsahuje čítačů, společně s rozhraním API pro převod textu JSON na běžné typy .NET pole a objektu JSON.</span><span class="sxs-lookup"><span data-stu-id="45914-274">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="45914-275">Parsování typické datová část JSON a přístup k všechny její členy pomocí `JsonDocument` je 2 až 3 x rychlejší než **Json.NET** s velmi málo přidělení pro data, která jsou přiměřeně velikosti (například < 1 MB).</span><span class="sxs-lookup"><span data-stu-id="45914-275">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with very little allocations for data that is reasonably sized (i.e. < 1 MB).</span></span>

<span data-ttu-id="45914-276">Tady je ukázkový používání `JsonDocument` a `JsonElement` , který může sloužit jako výchozí bod:</span><span class="sxs-lookup"><span data-stu-id="45914-276">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

```csharp
static double ParseJson()
{
    const string json = " [ { \"name\": \"John\" }, [ \"425-000-1212\", 15 ], { \"grades\": [ 90, 80, 100, 75 ] } ]";

    double average = -1;

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        JsonElement root = doc.RootElement;
        JsonElement info = root[1];

        string phoneNumber = info[0].GetString();
        int age = info[1].GetInt32();

        JsonElement grades = root[2].GetProperty("grades");

        double sum = 0;
        foreach (JsonElement grade in grades.EnumerateArray())
        {
            sum += grade.GetInt32();
        }

        int numberOfCourses = grades.GetArrayLength();
        average = sum / numberOfCourses;
    }

    return average;
}
```

## <a name="assembly-unloadability"></a><span data-ttu-id="45914-277">Unloadability sestavení</span><span class="sxs-lookup"><span data-stu-id="45914-277">Assembly Unloadability</span></span>

<span data-ttu-id="45914-278">Unloadability sestavení je nová funkce `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="45914-278">Assembly unloadability is a new capability of `AssemblyLoadContext`.</span></span> <span data-ttu-id="45914-279">Tato nová funkce je z velké části transparentní z hlediska rozhraní API, vystavena s několika nových rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="45914-279">This new feature is largely transparent from an API perspective, exposed with just a few new APIs.</span></span> <span data-ttu-id="45914-280">Umožňuje kontext načítání uvolnila, uvolňování paměti všechny instance typů, statická pole a samotného sestavení.</span><span class="sxs-lookup"><span data-stu-id="45914-280">It enables a loader context to be unloaded, releasing all memory for instantiated types, static fields and for the assembly itself.</span></span> <span data-ttu-id="45914-281">Aplikace by měla moct načtení a uvolnění sestavení přes tento mechanismus navždy bez nevrácené paměti.</span><span class="sxs-lookup"><span data-stu-id="45914-281">An application should be able to load and unload assemblies via this mechanism forever without experiencing a memory leak.</span></span>

<span data-ttu-id="45914-282">Tato nová funkce je možné pro podobné scénáře:</span><span class="sxs-lookup"><span data-stu-id="45914-282">This new capability can be used for scenarios similar to:</span></span>

* <span data-ttu-id="45914-283">Modul plug-in scénáře, ve kterém jsou vyžadována dynamických modulů plug-in, načítání a uvolňování.</span><span class="sxs-lookup"><span data-stu-id="45914-283">Plugin scenarios where dynamic plugin loading and unloading is required.</span></span> 
* <span data-ttu-id="45914-284">Dynamická kompilace, spouštění a pak vyprazdňování kódu.</span><span class="sxs-lookup"><span data-stu-id="45914-284">Dynamically compiling, running and then flushing code.</span></span> <span data-ttu-id="45914-285">Užitečné pro webové servery, skriptovací moduly atd.</span><span class="sxs-lookup"><span data-stu-id="45914-285">Useful for web sites, scripting engines, etc.</span></span>
* <span data-ttu-id="45914-286">Načítání sestavení pro introspekce (např. ReflectionOnlyLoad), i když [MetadataLoadContext](#type-metadataloadcontext) (všeobecně dostupné ve verzi Preview 1) bude vhodnější použít v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="45914-286">Loading assemblies for introspection (like ReflectionOnlyLoad), although [MetadataLoadContext](#type-metadataloadcontext) (released in Preview 1) will be a better choice in many cases.</span></span>

<span data-ttu-id="45914-287">Další informace najdete v tématu [pomocí Unloadability](https://github.com/dotnet/coreclr/pull/22221) dokumentu.</span><span class="sxs-lookup"><span data-stu-id="45914-287">For more information, see the [Using Unloadability](https://github.com/dotnet/coreclr/pull/22221) document.</span></span>

<span data-ttu-id="45914-288">Sestavení uvolnění vyžaduje významné péče zajistit, že jsou všechny odkazy na spravované objekty z mimo kontext načítání porozuměl jsem jim a spravované.</span><span class="sxs-lookup"><span data-stu-id="45914-288">Assembly unloading requires significant care to ensure that all references to managed objects from outside a loader context are understood and managed.</span></span> <span data-ttu-id="45914-289">Při vyžádání kontextu zavaděče uvolnila všechny vnější odkazy muset neodkazovaná tak, aby kontext načítání celistvý pouze na sebe sama.</span><span class="sxs-lookup"><span data-stu-id="45914-289">When the loader context is requested to be unloaded, any outside references need to have been unreferenced so that the loader context is self-consistent only to itself.</span></span>

<span data-ttu-id="45914-290">Sestavení unloadability byl zadaný v rozhraní .NET Framework podle domény aplikace (AppDomains), které nejsou podporované s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45914-290">Assembly unloadability was provided in the .NET Framework by Application Domains (AppDomains), which are not supported with .NET Core.</span></span> <span data-ttu-id="45914-291">Objektů třídy AppDomains měl výhody a omezení v porovnání s Tento nový model.</span><span class="sxs-lookup"><span data-stu-id="45914-291">AppDomains had both benefits and limitations compared to this new model.</span></span> <span data-ttu-id="45914-292">Vezměte v úvahu tento nový model zavaděč, aby bylo flexibilní a vyšší výkonné ve srovnání s objektů třídy AppDomains.</span><span class="sxs-lookup"><span data-stu-id="45914-292">Consider this new loader model to be more flexible and higher performant when compared to AppDomains.</span></span>

## <a name="windows-native-interop"></a><span data-ttu-id="45914-293">Windows nativní interoperabilita</span><span class="sxs-lookup"><span data-stu-id="45914-293">Windows Native Interop</span></span>

<span data-ttu-id="45914-294">Windows nabízí bohaté nativní rozhraní API, v podobě bez stromové struktury rozhraní API jazyka C, COM a WinRT.</span><span class="sxs-lookup"><span data-stu-id="45914-294">Windows offers a rich native API, in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="45914-295">Od .NET Core 1.0 **P/Invoke** se podporuje.</span><span class="sxs-lookup"><span data-stu-id="45914-295">Since .NET Core 1.0, **P/Invoke** has been supported.</span></span> <span data-ttu-id="45914-296">Nyní s .NET Core 3.0, podporu pro možnost **souběžné vytvoření součásti COM API** a **aktivovat rozhraní API WinRT** byla přidána.</span><span class="sxs-lookup"><span data-stu-id="45914-296">Now with .NET Core 3.0, support for the ability to **CoCreate COM APIs** and **Activate WinRT APIs** has been added.</span></span>

<span data-ttu-id="45914-297">Vidíte příklad použití modelu COM s [zdrojový kód ukázkové aplikace Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="45914-297">You can see an example of using COM with the [Excel Demo source code](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>


## <a name="type-sequencereader"></a><span data-ttu-id="45914-298">Zadejte: SequenceReader</span><span class="sxs-lookup"><span data-stu-id="45914-298">Type: SequenceReader</span></span>

<span data-ttu-id="45914-299">V rozhraní .NET Core 3.0 `System.Buffers.SequenceReader` se přidala, který může sloužit jako čtečku `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="45914-299">In .NET Core 3.0, `System.Buffers.SequenceReader` has been added which can be used as a reader for `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="45914-300">To umožňuje snadné, vysoký výkon s nízkou přidělení parsování `System.IO.Pipelines` data, která lze napříč více vyrovnávacích pamětí zálohování.</span><span class="sxs-lookup"><span data-stu-id="45914-300">This allows easy, high performance, low allocation parsing of `System.IO.Pipelines` data that can cross multiple backing buffers.</span></span> 

<span data-ttu-id="45914-301">Následující příklad přeruší vstup `Sequence` do platné `CR/LF` oddělených řádky:</span><span class="sxs-lookup"><span data-stu-id="45914-301">The following example breaks an input `Sequence` into valid `CR/LF` delimited lines:</span></span>

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a><span data-ttu-id="45914-302">Zadejte: MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="45914-302">Type: MetadataLoadContext</span></span>

<span data-ttu-id="45914-303">`MetadataLoadContext` Byl přidán typ, který umožňuje čtení sestavení metadat, aniž by to ovlivnilo doméně aplikace volajícího.</span><span class="sxs-lookup"><span data-stu-id="45914-303">The `MetadataLoadContext` type has been added that enables reading assembly metadata without affecting the caller’s application domain.</span></span> <span data-ttu-id="45914-304">Sestavení se číst jako data, včetně sestavení vytvořená pro rozdílné architektury a platformy než aktuální běhové prostředí.</span><span class="sxs-lookup"><span data-stu-id="45914-304">Assemblies are read as data, including assemblies built for different architectures and platforms than the current runtime environment.</span></span> <span data-ttu-id="45914-305">`MetadataLoadContext` se překrývá s <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, který je k dispozici pouze v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45914-305">`MetadataLoadContext` overlaps with the <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, which is only available in the .NET Framework.</span></span>

<span data-ttu-id="45914-306">`MetdataLoadContext` je k dispozici v [System.Reflection.MetadataLoadContext balíčku](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span><span class="sxs-lookup"><span data-stu-id="45914-306">`MetdataLoadContext` is available in the [System.Reflection.MetadataLoadContext package](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span></span> <span data-ttu-id="45914-307">Jedná se o balíček rozhraní .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="45914-307">It is a .NET Standard 2.0 package.</span></span>

<span data-ttu-id="45914-308">`MetadataLoadContext` Zveřejňuje rozhraní API, podobně jako <xref:System.Runtime.Loader.AssemblyLoadContext> typu, ale není na základě tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="45914-308">The `MetadataLoadContext` exposes APIs similar to the <xref:System.Runtime.Loader.AssemblyLoadContext> type, but is not based on that type.</span></span> <span data-ttu-id="45914-309">Podobně jako <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` povolí načítání sestavení v rámci izolovaného sestavení načítání universe.</span><span class="sxs-lookup"><span data-stu-id="45914-309">Much like <xref:System.Runtime.Loader.AssemblyLoadContext>, the `MetadataLoadContext` enables loading assemblies within an isolated assembly loading universe.</span></span> <span data-ttu-id="45914-310">`MetdataLoadContext` Rozhraní API vrací <xref:System.Reflection.Assembly> objekty povoluje použití známých reflexe rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="45914-310">`MetdataLoadContext` APIs return <xref:System.Reflection.Assembly> objects, enabling the use of familiar reflection APIs.</span></span> <span data-ttu-id="45914-311">Spuštění orientované rozhraní API, jako například [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), nejsou povoleny a vyvolá výjimku InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="45914-311">Execution-oriented APIs, such as [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), are not allowed and will throw InvalidOperationException.</span></span>

<span data-ttu-id="45914-312">Následující příklad ukazuje, jak najít konkrétní typy v sestavení, který implementuje v příslušném rozhraní:</span><span class="sxs-lookup"><span data-stu-id="45914-312">The following sample demonstrates how to find concrete types in an assembly that implements a given interface:</span></span>

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

<span data-ttu-id="45914-313">Scénáře pro `MetadataLoadContext` obsahují funkce návrhu, nástrojů, čas sestavení a funkce modulu runtime vytáčené světla, které je potřeba zkontrolovat sadu sestavení jako data a mít všech zámků souboru a probíhá po kontrole uvolněná paměť.</span><span class="sxs-lookup"><span data-stu-id="45914-313">Scenarios for `MetadataLoadContext` include design-time features, build-time tooling, and runtime light-up features that need to inspect a set of assemblies as data and have all file locks and memory freed after inspection is performed.</span></span>

<span data-ttu-id="45914-314">`MetadataLoadContext` Má třídu překladač předaný konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="45914-314">The `MetadataLoadContext` has a resolver class passed to its constructor.</span></span> <span data-ttu-id="45914-315">Úlohy překladače je načtení `Assembly` zadaný jeho `AssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="45914-315">The resolver's job is to load an `Assembly` given its `AssemblyName`.</span></span> <span data-ttu-id="45914-316">Překladač třída je odvozena z abstraktní `MetadataAssemblyResolver` třídy.</span><span class="sxs-lookup"><span data-stu-id="45914-316">The resolver class derives from the abstract `MetadataAssemblyResolver` class.</span></span> <span data-ttu-id="45914-317">Je součástí implementace překladače pro scénáře na základě cest `PathAssemblyResolver`.</span><span class="sxs-lookup"><span data-stu-id="45914-317">An implementation of the resolver for path-based scenarios is provided with `PathAssemblyResolver`.</span></span>

<span data-ttu-id="45914-318">[MetadataLoadContext testy](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) ukazují, případy použití, mnoho.</span><span class="sxs-lookup"><span data-stu-id="45914-318">The [MetadataLoadContext tests](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstrate many use cases.</span></span> <span data-ttu-id="45914-319">[Sestavení testů](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) jsou dobrým začátkem.</span><span class="sxs-lookup"><span data-stu-id="45914-319">The [Assembly tests](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) are a good place to start.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="45914-320">TLS verze 1.3 & OpenSSL 1.1.1 v Linuxu</span><span class="sxs-lookup"><span data-stu-id="45914-320">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="45914-321">.NET core se nově využít výhod [podpora protokolu TLS 1.3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), až bude k dispozici v daném prostředí.</span><span class="sxs-lookup"><span data-stu-id="45914-321">.NET Core will now take advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it is available in a given environment.</span></span> <span data-ttu-id="45914-322">Existuje více výhod TLS 1,3 za [OpenSSL týmu](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span><span class="sxs-lookup"><span data-stu-id="45914-322">There are multiple benefits of TLS 1.3, per the [OpenSSL team](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span></span>

* <span data-ttu-id="45914-323">Čas vylepšené připojení z důvodu snížení počet zpátečních cest vyžaduje mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="45914-323">Improved connection times due to a reduction in the number of round trips required between the client and server.</span></span>

* <span data-ttu-id="45914-324">Vyšší úroveň zabezpečení z důvodu odstranění různých zastaralé a nezabezpečené kryptografické algoritmy a šifrování větší metoda handshake připojení.</span><span class="sxs-lookup"><span data-stu-id="45914-324">Improved security due to the removal of various obsolete and insecure cryptographic algorithms and encryption of more of the connection handshake.</span></span>

<span data-ttu-id="45914-325">.NET core 3.0 ve verzi Preview 1 je schopen využitím **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, nebo **OpenSSL 1.0.2** (cokoli, co nejlepší nalezená verze se v systému Linux).</span><span class="sxs-lookup"><span data-stu-id="45914-325">.NET Core 3.0 Preview 1 is capable of utilizing **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** (whatever the best version found is, on a Linux system).</span></span>  <span data-ttu-id="45914-326">Při **OpenSSL 1.1.1** je k dispozici bude používat typy SslStream a HttpClient **TLS 1.3** při použití `SslProtocols.None` (protokoly systému výchozí), za předpokladu, že klient i server podpory **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="45914-326">When **OpenSSL 1.1.1** is available the SslStream and HttpClient types will use **TLS 1.3** when using `SslProtocols.None` (system default protocols), assuming both the client and server support **TLS 1.3**.</span></span>

<span data-ttu-id="45914-327">Následující příklad ukazuje .NET Core 3.0 ve verzi Preview 1 na Ubuntu 18.10 propojíte <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="45914-327">The following sample demonstrates .NET Core 3.0 Preview 1 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
><span data-ttu-id="45914-328">Windows a macOS zatím ještě nepodporují **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="45914-328">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="45914-329">Bude podporovat .NET core 3.0 **TLS 1.3** v těchto operačních systémech, jakmile je k dispozici podpora.</span><span class="sxs-lookup"><span data-stu-id="45914-329">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

## <a name="cryptography"></a><span data-ttu-id="45914-330">Cryptography</span><span class="sxs-lookup"><span data-stu-id="45914-330">Cryptography</span></span>

<span data-ttu-id="45914-331">Byla přidána podpora pro **AES-GCM** a **AES-CCM** šifry, prostřednictvím rozhraní `System.Security.Cryptography.AesGcm` a `System.Security.Cryptography.AesCcm`.</span><span class="sxs-lookup"><span data-stu-id="45914-331">Support has been added for **AES-GCM** and **AES-CCM** ciphers, implemented via `System.Security.Cryptography.AesGcm` and `System.Security.Cryptography.AesCcm`.</span></span> <span data-ttu-id="45914-332">Tyto algoritmy jsou obě [ověření šifrování pomocí algoritmů přidružení dat (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption)a první ověření šifrování (AE) algoritmy přidané do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45914-332">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption), and the first Authenticated Encryption (AE) algorithms added to .NET Core.</span></span>

<span data-ttu-id="45914-333">Následující kód ukazuje použití **AesGcm** šifer k šifrování a dešifrování náhodná data.</span><span class="sxs-lookup"><span data-stu-id="45914-333">The following code demonstrates using **AesGcm** cipher to encrypt and decrypt random data.</span></span>

<span data-ttu-id="45914-334">Kód pro **AesCcm** by vypadalo téměř identické (pouze názvy tříd, které proměnné by lišit).</span><span class="sxs-lookup"><span data-stu-id="45914-334">The code for **AesCcm** would look almost identical (only the class variable names would be different).</span></span>

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="45914-335">Kryptografické klíče Import/Export</span><span class="sxs-lookup"><span data-stu-id="45914-335">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="45914-336">.NET core 3.0 ve verzi Preview 1 podporuje import a export asymetrického veřejné a soukromé klíče ze standardní formáty, aniž by bylo nutné použít certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="45914-336">.NET Core 3.0 Preview 1 supports the import and export of asymmetric public and private keys from standard formats, without needing to use an X.509 certificate.</span></span>

<span data-ttu-id="45914-337">Všechny klíče podpora typy (RSA, DSA, ECDsa, ECDiffieHellman) **X.509 SubjectPublicKeyInfo** formát pro veřejné klíče a **PKCS #8 PrivateKeyInfo** a **PKCS #8 EncryptedPrivateKeyInfo**  formáty pro privátní klíče.</span><span class="sxs-lookup"><span data-stu-id="45914-337">All key types (RSA, DSA, ECDsa, ECDiffieHellman) support the **X.509 SubjectPublicKeyInfo** format for public keys, and the **PKCS#8 PrivateKeyInfo** and **PKCS#8 EncryptedPrivateKeyInfo** formats for private keys.</span></span> <span data-ttu-id="45914-338">Kromě toho podporuje RSA **PKCS #1 RSAPublicKey** a **PKCS #1 RSAPrivateKey**.</span><span class="sxs-lookup"><span data-stu-id="45914-338">RSA additionally supports **PKCS#1 RSAPublicKey** and **PKCS#1 RSAPrivateKey**.</span></span> <span data-ttu-id="45914-339">Všechny metody export vytvářejí kódování DER binární data, a metod importu očekávají, že stejné.</span><span class="sxs-lookup"><span data-stu-id="45914-339">The export methods all produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="45914-340">Pokud je klíč uložený ve formátu PEM popisný text, volajícího bude nutné base64 – dekódování obsahu před voláním metody importu.</span><span class="sxs-lookup"><span data-stu-id="45914-340">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

<span data-ttu-id="45914-341">Soubory PKCS č. 8 můžete prozkoumat pomocí `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` třídy.</span><span class="sxs-lookup"><span data-stu-id="45914-341">PKCS#8 files can be inspected with the `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` class.</span></span>

<span data-ttu-id="45914-342">Soubory PFX/PKCS #12, můžete ho zkontrolovat a manipulovat s `System.Security.Cryptography.Pkcs.Pkcs12Info` a `System.Security.Cryptography.Pkcs.Pkcs12Builder`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="45914-342">PFX/PKCS#12 files can be inspected and manipulated with `System.Security.Cryptography.Pkcs.Pkcs12Info` and `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectively.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="45914-343">SerialPort pro Linux</span><span class="sxs-lookup"><span data-stu-id="45914-343">SerialPort for Linux</span></span>

<span data-ttu-id="45914-344">.NET core 3.0 nyní podporuje <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> v Linuxu.</span><span class="sxs-lookup"><span data-stu-id="45914-344">.NET Core 3.0 now supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="45914-345">Dříve, .NET Core, které jsou podporovány pouze při použití `SerialPort` typu na Windows.</span><span class="sxs-lookup"><span data-stu-id="45914-345">Previously, .NET Core only supported using the `SerialPort` type on Windows.</span></span>

## <a name="more-bcl-improvements"></a><span data-ttu-id="45914-346">Další vylepšení BCL</span><span class="sxs-lookup"><span data-stu-id="45914-346">More BCL Improvements</span></span>

<span data-ttu-id="45914-347">`Span<T>`, `Memory<T>`, A souvisejících typů, které byly zavedeny v .NET Core 2.1, byly optimalizovány odstraněním v .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="45914-347">The `Span<T>`, `Memory<T>`, and related types that were introduced in .NET Core 2.1, have been optimized in .NET Core 3.0.</span></span> <span data-ttu-id="45914-348">Běžné operace, jako span konstrukce, dělení, analýzy a formátování nyní líp fungovat.</span><span class="sxs-lookup"><span data-stu-id="45914-348">Common operations such as span construction, slicing, parsing, and formatting now perform better.</span></span> 

<span data-ttu-id="45914-349">Kromě toho, jako jsou typy `String` viděli v rámci titulní vylepšení je zefektivňují při použití jako klíče s `Dictionary<TKey, TValue>` i další kolekce.</span><span class="sxs-lookup"><span data-stu-id="45914-349">Additionally, types like `String` have seen under-the-cover improvements to make them more efficient when used as keys with `Dictionary<TKey, TValue>` and other collections.</span></span> <span data-ttu-id="45914-350">Abyste využili výhod těchto vylepšení nevyžaduje žádné změny kódu.</span><span class="sxs-lookup"><span data-stu-id="45914-350">No code changes are required to benefit from these improvements.</span></span>

<span data-ttu-id="45914-351">Tato vylepšení jsou také nové v rozhraní .NET Core 3 Preview 1:</span><span class="sxs-lookup"><span data-stu-id="45914-351">The following improvements are also new in .NET Core 3 Preview 1:</span></span>

* <span data-ttu-id="45914-352">Podpora Brotli součástí HttpClient</span><span class="sxs-lookup"><span data-stu-id="45914-352">Brotli support built in to HttpClient</span></span>
* <span data-ttu-id="45914-353">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span><span class="sxs-lookup"><span data-stu-id="45914-353">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span></span>
* <span data-ttu-id="45914-354">Unsafe.Unbox</span><span class="sxs-lookup"><span data-stu-id="45914-354">Unsafe.Unbox</span></span>
* <span data-ttu-id="45914-355">CancellationToken.Unregister</span><span class="sxs-lookup"><span data-stu-id="45914-355">CancellationToken.Unregister</span></span>
* <span data-ttu-id="45914-356">Komplexní aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="45914-356">Complex arithmetic operators</span></span>
* <span data-ttu-id="45914-357">Zachování soketu rozhraní API pro protokol TCP</span><span class="sxs-lookup"><span data-stu-id="45914-357">Socket APIs for TCP keep alive</span></span>
* <span data-ttu-id="45914-358">StringBuilder.GetChunks</span><span class="sxs-lookup"><span data-stu-id="45914-358">StringBuilder.GetChunks</span></span>
* <span data-ttu-id="45914-359">IPEndPoint analýza kódu</span><span class="sxs-lookup"><span data-stu-id="45914-359">IPEndPoint parsing</span></span>
* <span data-ttu-id="45914-360">RandomNumberGenerator.GetInt32</span><span class="sxs-lookup"><span data-stu-id="45914-360">RandomNumberGenerator.GetInt32</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="45914-361">Vrstvené kompilace</span><span class="sxs-lookup"><span data-stu-id="45914-361">Tiered compilation</span></span>

<span data-ttu-id="45914-362">[Vrstvené kompilace](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) je ve výchozím s .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="45914-362">[Tiered compilation](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="45914-363">To je funkce, která umožňuje modulu runtime více Adaptivně pomocí kompilátor za běhu (JIT), můžete dosáhnout lepšího výkonu, jak při spuštění a maximalizuje propustnost.</span><span class="sxs-lookup"><span data-stu-id="45914-363">It is a feature that enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance, both at startup and to maximize throughput.</span></span>

<span data-ttu-id="45914-364">Tato funkce byla přidána jako funkce opt-in v [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) a potom byla povolená ve výchozím nastavení v [.NET Core 2.2 ve verzi Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="45914-364">This feature was added as an opt-in feature in [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) and then was enabled by default in [.NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span></span> <span data-ttu-id="45914-365">Následně ji byl vrácen zpět do optimalizované pomocí verze rozhraní .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="45914-365">Subsequently, it has been reverted back to opt in with the .NET Core 2.2 release.</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="45914-366">Podpora Linuxu ARM64</span><span class="sxs-lookup"><span data-stu-id="45914-366">ARM64 Linux support</span></span>

<span data-ttu-id="45914-367">Byla přidána podpora pro ARM64 pro Linux.</span><span class="sxs-lookup"><span data-stu-id="45914-367">Support has been added for ARM64 for Linux.</span></span> <span data-ttu-id="45914-368">Případem primárního použití pro ARM64 je aktuálně s scénáře IoT.</span><span class="sxs-lookup"><span data-stu-id="45914-368">The primary use case for ARM64 is currently with IoT scenarios.</span></span>

<span data-ttu-id="45914-369">Nástroj Alpine, Debian a Ubuntu [imagí Dockeru, které jsou dostupné pro .NET Core pro ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="45914-369">Alpine, Debian and Ubuntu [Docker images are available for .NET Core for ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

<span data-ttu-id="45914-370">Zkontrolujte prosím [.NET Core ARM64 stav](https://github.com/dotnet/announcements/issues/82) Další informace.</span><span class="sxs-lookup"><span data-stu-id="45914-370">Please check [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) for more information.</span></span>

>[!NOTE]
> <span data-ttu-id="45914-371">**ARM64** podporu Windows ještě není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="45914-371">**ARM64** Windows support isn't yet available.</span></span>

## <a name="install-net-core-30-previews-on-linux-with-snap"></a><span data-ttu-id="45914-372">Instalace .NET Core 3.0 náhledy v Linuxu pomocí modulu Snap</span><span class="sxs-lookup"><span data-stu-id="45914-372">Install .NET Core 3.0 Previews on Linux with Snap</span></span>

<span data-ttu-id="45914-373">Modul snap je preferovaný způsob, jak nainstalovat a vyzkoušejte .NET Core náhledy na [Linuxových distribucích podporujících Snap](https://docs.snapcraft.io/installing-snapd/6735).</span><span class="sxs-lookup"><span data-stu-id="45914-373">Snap is the preferred way to install and try .NET Core previews on [Linux distributions that support Snap](https://docs.snapcraft.io/installing-snapd/6735).</span></span>

<span data-ttu-id="45914-374">Po dokončení konfigurace Snap ve vašem systému, spusťte následující příkaz k instalaci [.NET Core SDK 3.0 ve verzi Preview SDK](https://snapcraft.io/dotnet-sdk).</span><span class="sxs-lookup"><span data-stu-id="45914-374">After configuring Snap on your system, run the following command to install the [.NET Core SDK 3.0 Preview SDK](https://snapcraft.io/dotnet-sdk).</span></span>

```console
sudo snap install dotnet-sdk --beta --classic
```
 
<span data-ttu-id="45914-375">Když .NET Core v nainstalovaných pomocí modulu Snap balíčku, výchozí příkaz .NET Core je `dotnet-sdk.dotnet`, na rozdíl od jenom `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="45914-375">When .NET Core in installed using the Snap package, the default .NET Core command is `dotnet-sdk.dotnet`, as opposed to just `dotnet`.</span></span> <span data-ttu-id="45914-376">Výhodou namespaced příkaz je, že to nebude v konfliktu s globálně nainstalovanou verzi .NET Core, které máte uzavřeny.</span><span class="sxs-lookup"><span data-stu-id="45914-376">The benefit of the namespaced command is that it will not conflict with a globally installed .NET Core version you may have.</span></span> <span data-ttu-id="45914-377">Tento příkaz lze použít alias na `dotnet` pomocí:</span><span class="sxs-lookup"><span data-stu-id="45914-377">This command can be aliased to `dotnet` with:</span></span>

```console
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="45914-378">Některé distribuce vyžadovat další krok k povolení přístupu k certifikátu SSL.</span><span class="sxs-lookup"><span data-stu-id="45914-378">Some distros require an additional step to enable access to the SSL certificate.</span></span> <span data-ttu-id="45914-379">Najdete v našich [instalace v systému Linux](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="45914-379">See our [Linux Setup](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) for details.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="45914-380">Podpora GPIO Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="45914-380">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="45914-381">Byly vydány dvě nové balíčky nuget, který vám pomůže GPIO programování.</span><span class="sxs-lookup"><span data-stu-id="45914-381">Two new packages have been released to NuGet that you can use for GPIO programming.</span></span>

* [<span data-ttu-id="45914-382">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="45914-382">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio/0.1.0-prerelease.19078.2)
* [<span data-ttu-id="45914-383">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="45914-383">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings/0.1.0-prerelease.19078.2)

<span data-ttu-id="45914-384">Balíčky GPIO zahrnuje rozhraní API pro zařízení GPIO, SPI, I2C a PWM.</span><span class="sxs-lookup"><span data-stu-id="45914-384">The GPIO Packages includes APIs for GPIO, SPI, I2C and PWM devices.</span></span> <span data-ttu-id="45914-385">Sada IoT vazby zahrnuje [zařízení vazby](https://github.com/dotnet/iot/blob/master/src/devices/README.md) pro různé čipy a senzory, stejné těch, které jsou k dispozici na [dotnet/iot-src/zařízení](https://github.com/dotnet/iot/tree/master/src/devices).</span><span class="sxs-lookup"><span data-stu-id="45914-385">The IoT bindings package includes [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) for various chips and sensors, the same ones available at [dotnet/iot - src/devices](https://github.com/dotnet/iot/tree/master/src/devices).</span></span>

<span data-ttu-id="45914-386">Aktualizované sériového portu rozhraní API, které byly součástí rozhraní .NET Core 3.0 ve verzi Preview 1 oznámili nejsou součástí těchto balíčků, ale jsou k dispozici jako součást platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45914-386">The updated serial port APIs that were announced as part of .NET Core 3.0 Preview 1 are not part of these packages but are available as part of the .NET Core platform.</span></span>


## <a name="platform-support"></a><span data-ttu-id="45914-387">Podpora platformy</span><span class="sxs-lookup"><span data-stu-id="45914-387">Platform Support</span></span>

<span data-ttu-id="45914-388">.NET core 3 bude podporovat v následujících operačních systémech:</span><span class="sxs-lookup"><span data-stu-id="45914-388">.NET Core 3 will be supported on the following operating systems:</span></span>

* <span data-ttu-id="45914-389">Klient Windows: 7, 8.1, 10 (1607+)</span><span class="sxs-lookup"><span data-stu-id="45914-389">Windows Client: 7, 8.1, 10 (1607+)</span></span>
* <span data-ttu-id="45914-390">Windows Server: 2012 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="45914-390">Windows Server: 2012 R2 SP1+</span></span>
* <span data-ttu-id="45914-391">macOS: 10.12+</span><span class="sxs-lookup"><span data-stu-id="45914-391">macOS: 10.12+</span></span>
* <span data-ttu-id="45914-392">RHEL: 6+</span><span class="sxs-lookup"><span data-stu-id="45914-392">RHEL: 6+</span></span>
* <span data-ttu-id="45914-393">Fedora: 26+</span><span class="sxs-lookup"><span data-stu-id="45914-393">Fedora: 26+</span></span>
* <span data-ttu-id="45914-394">Ubuntu: 16.04+</span><span class="sxs-lookup"><span data-stu-id="45914-394">Ubuntu: 16.04+</span></span>
* <span data-ttu-id="45914-395">Debian: 9+</span><span class="sxs-lookup"><span data-stu-id="45914-395">Debian: 9+</span></span>
* <span data-ttu-id="45914-396">SLES: 12+</span><span class="sxs-lookup"><span data-stu-id="45914-396">SLES: 12+</span></span>
* <span data-ttu-id="45914-397">openSUSE: 42.3+</span><span class="sxs-lookup"><span data-stu-id="45914-397">openSUSE: 42.3+</span></span>
* <span data-ttu-id="45914-398">Nástroj Alpine: 3.8+</span><span class="sxs-lookup"><span data-stu-id="45914-398">Alpine: 3.8+</span></span>

<span data-ttu-id="45914-399">Podpora čip TPM takto:</span><span class="sxs-lookup"><span data-stu-id="45914-399">Chip support follows:</span></span>

* <span data-ttu-id="45914-400">x64 ve Windows, macOS a Linuxu</span><span class="sxs-lookup"><span data-stu-id="45914-400">x64 on Windows, macOS, and Linux</span></span>
* <span data-ttu-id="45914-401">x86 na Windows</span><span class="sxs-lookup"><span data-stu-id="45914-401">x86 on Windows</span></span>
* <span data-ttu-id="45914-402">ARM32 ve Windows a Linuxu</span><span class="sxs-lookup"><span data-stu-id="45914-402">ARM32 on Windows and Linux</span></span>
* <span data-ttu-id="45914-403">ARM64 v Linuxu</span><span class="sxs-lookup"><span data-stu-id="45914-403">ARM64 on Linux</span></span>

<span data-ttu-id="45914-404">Pro Linux je podporováno ARM32 na Debian 9 + a Ubuntu 16.04 +.</span><span class="sxs-lookup"><span data-stu-id="45914-404">For Linux, ARM32 is supported on Debian 9+ and Ubuntu 16.04+.</span></span> <span data-ttu-id="45914-405">Pro ARM64 je stejný jako ARM32 a uveďte Alpine 3.8.</span><span class="sxs-lookup"><span data-stu-id="45914-405">For ARM64, it is the same as ARM32 with the addition of Alpine 3.8.</span></span> <span data-ttu-id="45914-406">Jedná se o stejné verze těchto distribuce, jako je podporovaná pro X64.</span><span class="sxs-lookup"><span data-stu-id="45914-406">These are the same versions of those distros as is supported for X64.</span></span>

<span data-ttu-id="45914-407">Image dockeru pro .NET Core 3.0 najdete na adrese [microsoft/dotnet na Docker Hubu](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="45914-407">Docker images for .NET Core 3.0 are available at [microsoft/dotnet on Docker Hub](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="45914-408">Microsoft se právě přijetí [Microsoft Container Registry (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) a očekává se, že finální Image .NET Core 3.0 pouze publikuje do MCR.</span><span class="sxs-lookup"><span data-stu-id="45914-408">Microsoft is currently in the process of adopting [Microsoft Container Registry (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) and it is expected that the final .NET Core 3.0 images will only be published to MCR.</span></span>
