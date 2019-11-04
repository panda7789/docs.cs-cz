---
title: Úvod do funkčního programování v F#
description: Seznamte se se základy funkčního programování F#v nástroji.
ms.date: 10/29/2018
ms.openlocfilehash: e1a0edc61dbe13012c48e166d490e22ebc70d6a0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424700"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="583c2-103">Úvod do funkčního programování v F\#</span><span class="sxs-lookup"><span data-stu-id="583c2-103">Introduction to Functional Programming in F\#</span></span>

<span data-ttu-id="583c2-104">Funkční programování je styl programování, který zdůrazňuje použití funkcí a neměnných dat.</span><span class="sxs-lookup"><span data-stu-id="583c2-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="583c2-105">Typované funkční programování je v případě, že je funkční programování kombinováno se statickými F#typy, například s.</span><span class="sxs-lookup"><span data-stu-id="583c2-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="583c2-106">Obecně platí, že následující pojmy jsou zvýrazněny v části funkční programování:</span><span class="sxs-lookup"><span data-stu-id="583c2-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="583c2-107">Funguje jako primární konstrukce, které používáte.</span><span class="sxs-lookup"><span data-stu-id="583c2-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="583c2-108">Výrazy místo příkazů</span><span class="sxs-lookup"><span data-stu-id="583c2-108">Expressions instead of statements</span></span>
* <span data-ttu-id="583c2-109">Neměnné hodnoty nad proměnnými</span><span class="sxs-lookup"><span data-stu-id="583c2-109">Immutable values over variables</span></span>
* <span data-ttu-id="583c2-110">Deklarativní programování v rámci imperativního programování</span><span class="sxs-lookup"><span data-stu-id="583c2-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="583c2-111">V celé této sérii budete zkoumat koncepty a vzory v rámci funkčního F#programování pomocí.</span><span class="sxs-lookup"><span data-stu-id="583c2-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="583c2-112">V takovém případě se naučíte F# také.</span><span class="sxs-lookup"><span data-stu-id="583c2-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="583c2-113">Terminologie</span><span class="sxs-lookup"><span data-stu-id="583c2-113">Terminology</span></span>

<span data-ttu-id="583c2-114">Funkční programování, podobně jako jiné programovací paradigma, je dodáváno se slovníkem, který budete nakonec potřebovat vědět.</span><span class="sxs-lookup"><span data-stu-id="583c2-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="583c2-115">Tady jsou některé běžné výrazy, které se zobrazí po celou dobu:</span><span class="sxs-lookup"><span data-stu-id="583c2-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="583c2-116">**Funkce** – funkce je konstrukce, která při zadání vstupu vytvoří výstup.</span><span class="sxs-lookup"><span data-stu-id="583c2-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="583c2-117">V tuto dobu _namapuje_ položku z jedné sady na jinou sadu.</span><span class="sxs-lookup"><span data-stu-id="583c2-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="583c2-118">Tento formální způsob se přenese do konkrétního množství způsobů, zejména při použití funkcí, které pracují s kolekcemi dat.</span><span class="sxs-lookup"><span data-stu-id="583c2-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="583c2-119">Je to nejzákladnější koncept (a důležité) v rámci funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="583c2-119">It is the most basic (and important) concept in functional programming.</span></span>
* <span data-ttu-id="583c2-120">**Expression** – výraz je konstruktor v kódu, který vytváří hodnotu.</span><span class="sxs-lookup"><span data-stu-id="583c2-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="583c2-121">V F#nástroji musí být tato hodnota svázaná nebo explicitně ignorována.</span><span class="sxs-lookup"><span data-stu-id="583c2-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="583c2-122">Výraz může být triviálním nahrazen voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="583c2-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="583c2-123">**Čistota** -čistota je vlastnost funkce tak, že vrácená hodnota je vždy stejná pro stejné argumenty a že její vyhodnocení nemá žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="583c2-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="583c2-124">Funkce Pure závisí výhradně na svých argumentech.</span><span class="sxs-lookup"><span data-stu-id="583c2-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="583c2-125">**Referenční** transparentnost – referenční transparentnost je vlastnost výrazů, jako je například, že mohou být nahrazeny jejich výstupem, aniž by to ovlivnilo chování programu.</span><span class="sxs-lookup"><span data-stu-id="583c2-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="583c2-126">**Neměnnosti** -neměnnosti znamená, že hodnotu nelze změnit na místě.</span><span class="sxs-lookup"><span data-stu-id="583c2-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="583c2-127">To je v kontrastu s proměnnými, které se mohou změnit na místě.</span><span class="sxs-lookup"><span data-stu-id="583c2-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="583c2-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="583c2-128">Examples</span></span>

<span data-ttu-id="583c2-129">Následující příklady znázorňují tyto základní koncepty.</span><span class="sxs-lookup"><span data-stu-id="583c2-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="583c2-130">Funkce</span><span class="sxs-lookup"><span data-stu-id="583c2-130">Functions</span></span>

<span data-ttu-id="583c2-131">Nejběžnější a základní konstrukce v funkčním programování je funkce.</span><span class="sxs-lookup"><span data-stu-id="583c2-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="583c2-132">Tady je jednoduchá funkce, která přidá 1 k celému číslu:</span><span class="sxs-lookup"><span data-stu-id="583c2-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="583c2-133">Jeho signatura typu je následující:</span><span class="sxs-lookup"><span data-stu-id="583c2-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="583c2-134">Podpis lze číst jako, "`addOne` přijímá `int` s názvem `x` a vytvoří `int`".</span><span class="sxs-lookup"><span data-stu-id="583c2-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="583c2-135">`addOne` je _mapována_ hodnota ze sady celých čísel na sadu celých čísel.</span><span class="sxs-lookup"><span data-stu-id="583c2-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="583c2-136">Token `->` znamená toto mapování.</span><span class="sxs-lookup"><span data-stu-id="583c2-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="583c2-137">V F#nástroji se můžete obvykle podívat na signaturu funkce, abyste získali představu o tom, co dělá.</span><span class="sxs-lookup"><span data-stu-id="583c2-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="583c2-138">Proč je podpis důležitý?</span><span class="sxs-lookup"><span data-stu-id="583c2-138">So, why is the signature important?</span></span> <span data-ttu-id="583c2-139">V psaní funkčního programování je implementace funkce často méně důležitá než skutečný podpis typu!</span><span class="sxs-lookup"><span data-stu-id="583c2-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="583c2-140">Skutečnost, že `addOne` přidá hodnotu 1 k celému číslu, je zajímavá za běhu, ale při sestavování programu je fakt, že přijímá a vrací `int` je to, co informuje o tom, jak tuto funkci skutečně používáte.</span><span class="sxs-lookup"><span data-stu-id="583c2-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="583c2-141">Navíc po správném použití této funkce (s ohledem na signaturu jejího typu) je možné diagnostikovat jakékoli problémy pouze v těle funkce `addOne`.</span><span class="sxs-lookup"><span data-stu-id="583c2-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="583c2-142">Jedná se o podněty za psaní funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="583c2-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="583c2-143">Výrazy</span><span class="sxs-lookup"><span data-stu-id="583c2-143">Expressions</span></span>

<span data-ttu-id="583c2-144">Výrazy jsou konstrukce, které se vyhodnotí na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="583c2-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="583c2-145">Na rozdíl od příkazů, které provádějí akci, lze výrazy považovat za provedení akce, která vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="583c2-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="583c2-146">Výrazy se téměř vždycky používají ve prospěch příkazů ve funkčním programování.</span><span class="sxs-lookup"><span data-stu-id="583c2-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="583c2-147">Zvažte předchozí funkci `addOne`.</span><span class="sxs-lookup"><span data-stu-id="583c2-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="583c2-148">Text `addOne` je výraz:</span><span class="sxs-lookup"><span data-stu-id="583c2-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="583c2-149">Jedná se o výsledek tohoto výrazu, který definuje typ výsledku funkce `addOne`.</span><span class="sxs-lookup"><span data-stu-id="583c2-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="583c2-150">Například výraz, který tvoří tuto funkci, může být změněn na jiný typ, například `string`:</span><span class="sxs-lookup"><span data-stu-id="583c2-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="583c2-151">Signatura funkce je teď:</span><span class="sxs-lookup"><span data-stu-id="583c2-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="583c2-152">Vzhledem k tomu, F# že kterýkoli typ v může mít `ToString()` volána, byl typ `x` vytvořen jako obecný (tzv. [Automatická generalizace](../language-reference/generics/automatic-generalization.md)) a výsledný typ je `string`.</span><span class="sxs-lookup"><span data-stu-id="583c2-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="583c2-153">Výrazy nejsou jenom orgány funkcí.</span><span class="sxs-lookup"><span data-stu-id="583c2-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="583c2-154">Můžete mít výrazy, které vytvoří hodnotu, kterou použijete jinde.</span><span class="sxs-lookup"><span data-stu-id="583c2-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="583c2-155">Jednou z nich je `if`:</span><span class="sxs-lookup"><span data-stu-id="583c2-155">A common one is `if`:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

<span data-ttu-id="583c2-156">Výraz `if` vytvoří hodnotu nazvanou `result`.</span><span class="sxs-lookup"><span data-stu-id="583c2-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="583c2-157">Všimněte si, že můžete `result` zcela vynechat, což `if` výrazu `addOneIfOdd` funkce.</span><span class="sxs-lookup"><span data-stu-id="583c2-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="583c2-158">Klíčovým aspektem pro zapamatování výrazů je, že vytvoří hodnotu.</span><span class="sxs-lookup"><span data-stu-id="583c2-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="583c2-159">Existuje speciální typ, `unit`, který se používá v případě, že není nic vráceno.</span><span class="sxs-lookup"><span data-stu-id="583c2-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="583c2-160">Zvažte například tuto jednoduchou funkci:</span><span class="sxs-lookup"><span data-stu-id="583c2-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

<span data-ttu-id="583c2-161">Signatura vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="583c2-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="583c2-162">Typ `unit` označuje, že není vrácena žádná skutečná hodnota.</span><span class="sxs-lookup"><span data-stu-id="583c2-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="583c2-163">To je užitečné, když máte rutinu, která musí "dělat práci" Navzdory tomu, že nevrátí hodnotu, která by se měla vrátit jako výsledek této práce.</span><span class="sxs-lookup"><span data-stu-id="583c2-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="583c2-164">To je prudký kontrast vůči imperativnímu programování, kde ekvivalentní `if` konstrukce je příkaz a vytváření hodnot se často provádí s použitím obdobných proměnných.</span><span class="sxs-lookup"><span data-stu-id="583c2-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="583c2-165">Například v C#nástroji může být kód napsán takto:</span><span class="sxs-lookup"><span data-stu-id="583c2-165">For example, in C#, the code might be written like this:</span></span>

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

<span data-ttu-id="583c2-166">Je vhodné poznamenat, C# že a jiné jazyky ve stylu jazyka C podporují [výraz Ternární](../../csharp/language-reference/operators/conditional-operator.md), který umožňuje podmíněné programování založené na výrazu.</span><span class="sxs-lookup"><span data-stu-id="583c2-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="583c2-167">V funkčním programování je zřídka možné hodnoty pomocí příkazů.</span><span class="sxs-lookup"><span data-stu-id="583c2-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="583c2-168">I když některé funkční jazyky podporují příkazy a mutace, není běžné používat tyto koncepty v funkčním programování.</span><span class="sxs-lookup"><span data-stu-id="583c2-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="583c2-169">Čisté funkce</span><span class="sxs-lookup"><span data-stu-id="583c2-169">Pure functions</span></span>

<span data-ttu-id="583c2-170">Jak už jsme uvedli, funkce Pure jsou funkce, které:</span><span class="sxs-lookup"><span data-stu-id="583c2-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="583c2-171">Vždy se vyhodnotí na stejnou hodnotu pro stejný vstup.</span><span class="sxs-lookup"><span data-stu-id="583c2-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="583c2-172">Nemají žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="583c2-172">Have no side effects.</span></span>

<span data-ttu-id="583c2-173">Je vhodné si v tomto kontextu představit matematické funkce.</span><span class="sxs-lookup"><span data-stu-id="583c2-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="583c2-174">V matematice jsou funkce závislé jenom na jejich argumentech a nemají žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="583c2-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="583c2-175">V matematické funkci `f(x) = x + 1`, hodnota `f(x)` závisí pouze na hodnotě `x`.</span><span class="sxs-lookup"><span data-stu-id="583c2-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="583c2-176">Čisté funkce v funkčním programování jsou stejné jako.</span><span class="sxs-lookup"><span data-stu-id="583c2-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="583c2-177">Při psaní čistě funkce musí být funkce závislá pouze na jejích argumentech a nesmí provádět žádnou akci, která má za následek vedlejší efekt.</span><span class="sxs-lookup"><span data-stu-id="583c2-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="583c2-178">Tady je příklad nečisté funkce, protože závisí na globálním, proměnlivém stavu:</span><span class="sxs-lookup"><span data-stu-id="583c2-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="583c2-179">Funkce `addOneToValue` je jasně nečistá, protože `value` možné kdykoli změnit tak, aby měla jinou hodnotu než 1.</span><span class="sxs-lookup"><span data-stu-id="583c2-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="583c2-180">Tento model v závislosti na globální hodnotě se vyhne v funkčním programování.</span><span class="sxs-lookup"><span data-stu-id="583c2-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="583c2-181">Tady je další příklad nečisté funkce, protože provádí vedlejší efekt:</span><span class="sxs-lookup"><span data-stu-id="583c2-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x =
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="583c2-182">I když tato funkce není závislá na globální hodnotě, zapíše hodnotu `x` do výstupu programu.</span><span class="sxs-lookup"><span data-stu-id="583c2-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="583c2-183">I když se to nestane nepodstatným chybou, znamená to, že funkce není čistá.</span><span class="sxs-lookup"><span data-stu-id="583c2-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span> <span data-ttu-id="583c2-184">Pokud jiná část programu závisí na něčem externím programu, jako je výstupní vyrovnávací paměť, pak volání této funkce může ovlivnit tuto jinou část programu.</span><span class="sxs-lookup"><span data-stu-id="583c2-184">If another part of your program depends on something external to the program, such as the output buffer, then calling this function can affect that other part of your program.</span></span>

<span data-ttu-id="583c2-185">Odebrání příkazu `printfn` provede čistou funkci:</span><span class="sxs-lookup"><span data-stu-id="583c2-185">Removing the `printfn` statement makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="583c2-186">I když tato funkce není ve své podstatě _lepší_ než předchozí verze s příkazem `printfn`, zaručuje, že všechny této funkce vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="583c2-186">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="583c2-187">Voláním této funkce libovolným počtem opakování vznikne stejný výsledek: pouze vytvoří hodnotu.</span><span class="sxs-lookup"><span data-stu-id="583c2-187">Calling this function any number of times produces the same result: it just produces a value.</span></span> <span data-ttu-id="583c2-188">Předvídatelnost vydaná pomocí čistoty je mnoho funkčních programátorů, které se snaží.</span><span class="sxs-lookup"><span data-stu-id="583c2-188">The predictability given by purity is something many functional programmers strive for.</span></span>

### <a name="immutability"></a><span data-ttu-id="583c2-189">Neměnnosti</span><span class="sxs-lookup"><span data-stu-id="583c2-189">Immutability</span></span>

<span data-ttu-id="583c2-190">Nakonec jedna z nejdůležitějších konceptů typovaného programování je neměnnosti.</span><span class="sxs-lookup"><span data-stu-id="583c2-190">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="583c2-191">Ve F#výchozím nastavení jsou všechny hodnoty neměnné.</span><span class="sxs-lookup"><span data-stu-id="583c2-191">In F#, all values are immutable by default.</span></span> <span data-ttu-id="583c2-192">To znamená, že nemohou být umístěny místně, pokud je explicitně neoznačíte jako proměnlivé.</span><span class="sxs-lookup"><span data-stu-id="583c2-192">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="583c2-193">V praxi pracujete s neproměnlivými hodnotami, protože měníte přístup k programování z, "Potřebuji změnit něco", na "Potřebuji vytvořit novou hodnotu".</span><span class="sxs-lookup"><span data-stu-id="583c2-193">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="583c2-194">Například přidání hodnoty 1 k hodnotě znamená vytvoření nové hodnoty, která nezpůsobuje existující hodnotu:</span><span class="sxs-lookup"><span data-stu-id="583c2-194">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="583c2-195">V F#, následující kód **není** obdobou funkce `value`; místo toho provede kontrolu rovnosti:</span><span class="sxs-lookup"><span data-stu-id="583c2-195">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="583c2-196">Některé funkční programovací jazyky nepodporují mutace vůbec.</span><span class="sxs-lookup"><span data-stu-id="583c2-196">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="583c2-197">V F#je podporováno, ale není to výchozí chování pro hodnoty.</span><span class="sxs-lookup"><span data-stu-id="583c2-197">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="583c2-198">Tento koncept rozšiřuje ještě více datových struktur.</span><span class="sxs-lookup"><span data-stu-id="583c2-198">This concept extends even further to data structures.</span></span> <span data-ttu-id="583c2-199">V funkčním programování mají neměnné datové struktury, jako jsou například sady (a mnoho dalších) odlišnou implementaci, než na začátku očekávat.</span><span class="sxs-lookup"><span data-stu-id="583c2-199">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="583c2-200">V koncepčních případech, například když přidáte položku do sady, se nezmění sada, vytvoří _novou_ sadu s přidanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="583c2-200">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="583c2-201">V rámci pokrývá to často používá jiná datová struktura, která umožňuje efektivně sledovat hodnotu tak, aby se v důsledku mohla předávat odpovídající reprezentace dat.</span><span class="sxs-lookup"><span data-stu-id="583c2-201">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="583c2-202">Tento styl práce s hodnotami a datovými strukturami je kritický, protože se vynutí, aby se pocházela s jakoukoli operací, jako kdyby vytvořila novou verzi této věci.</span><span class="sxs-lookup"><span data-stu-id="583c2-202">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="583c2-203">To umožňuje, aby byly v aplikacích konzistentní, jako je rovnost a srovnatelnost.</span><span class="sxs-lookup"><span data-stu-id="583c2-203">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="583c2-204">Další kroky</span><span class="sxs-lookup"><span data-stu-id="583c2-204">Next steps</span></span>

<span data-ttu-id="583c2-205">V další části najdete funkce, které prozkoumejte různé způsoby, jak je můžete používat při funkčním programování.</span><span class="sxs-lookup"><span data-stu-id="583c2-205">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="583c2-206">[Funkce první třídy](first-class-functions.md) zkoumá funkce a ukazuje, jak je lze použít v různých kontextech.</span><span class="sxs-lookup"><span data-stu-id="583c2-206">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="583c2-207">Další čtení</span><span class="sxs-lookup"><span data-stu-id="583c2-207">Further reading</span></span>

<span data-ttu-id="583c2-208">[Funkce přemýšlení](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) je dalším skvělým zdrojem informací o funkčním programování s F#.</span><span class="sxs-lookup"><span data-stu-id="583c2-208">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="583c2-209">Zabývá se základy funkčního programování v rámci náročného a snadno čitelného způsobu použití F# funkcí k ilustraci konceptů.</span><span class="sxs-lookup"><span data-stu-id="583c2-209">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>
