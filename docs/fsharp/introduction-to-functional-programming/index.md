---
title: Úvod do funkčního programování v F#
description: Seznamte se se základy funkčního programování v F#.
ms.date: 10/29/2018
ms.openlocfilehash: d4a9bb0cd826b41aca96e12e2bcb5aab80c18eb4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "25863840"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="141a4-103">Úvod do funkčního programování v F#</span><span class="sxs-lookup"><span data-stu-id="141a4-103">Introduction to Functional Programming in F#</span></span> #

<span data-ttu-id="141a4-104">Funkční programování je styl programování, které klade důraz na použití funkcí a neměnnými daty.</span><span class="sxs-lookup"><span data-stu-id="141a4-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="141a4-105">Je zadaný funkční programování kombinaci funkční programování je pomocí statické typy, například s F#.</span><span class="sxs-lookup"><span data-stu-id="141a4-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="141a4-106">Obecně tyto koncepty jsou zvýrazněny do funkčního programování:</span><span class="sxs-lookup"><span data-stu-id="141a4-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="141a4-107">Funkce jako primární konstrukce, které používáte</span><span class="sxs-lookup"><span data-stu-id="141a4-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="141a4-108">Výrazy místo příkazů</span><span class="sxs-lookup"><span data-stu-id="141a4-108">Expressions instead of statements</span></span>
* <span data-ttu-id="141a4-109">Neměnné hodnoty v proměnné</span><span class="sxs-lookup"><span data-stu-id="141a4-109">Immutable values over variables</span></span>
* <span data-ttu-id="141a4-110">Deklarativní programování přes imperativní programování</span><span class="sxs-lookup"><span data-stu-id="141a4-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="141a4-111">V celé této sérii prozkoumáte koncepty a vzory v funkční programování pomocí F#.</span><span class="sxs-lookup"><span data-stu-id="141a4-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="141a4-112">Cestou se dozvíte některé F# příliš.</span><span class="sxs-lookup"><span data-stu-id="141a4-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="141a4-113">Terminologie</span><span class="sxs-lookup"><span data-stu-id="141a4-113">Terminology</span></span>

<span data-ttu-id="141a4-114">Funkční programování, jako jsou jiné programovací modely obsahuje slovník, který bude časem nutné další informace.</span><span class="sxs-lookup"><span data-stu-id="141a4-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="141a4-115">Tady jsou některé běžné podmínky zobrazí celou dobu:</span><span class="sxs-lookup"><span data-stu-id="141a4-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="141a4-116">**Funkce** – funkce je konstrukce, která vytvoří výstup, když vstup.</span><span class="sxs-lookup"><span data-stu-id="141a4-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="141a4-117">Více formálně ho _mapuje_ položky z jednoho nastavena na jinou sadu.</span><span class="sxs-lookup"><span data-stu-id="141a4-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="141a4-118">Tato formalism je zrušeno do konkrétní mnoha způsoby, zvláště při použití funkce, které pracují na kolekce dat.</span><span class="sxs-lookup"><span data-stu-id="141a4-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="141a4-119">Je nejvíce základní (a důležité) koncept v funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="141a4-119">It is the most basic (and important) concept in functional programming.</span></span> 
* <span data-ttu-id="141a4-120">**Výraz** -výrazu je konstrukce v kódu, který vytváří hodnotu.</span><span class="sxs-lookup"><span data-stu-id="141a4-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="141a4-121">V F#, tato hodnota musí být svázán nebo explicitně ignorovány.</span><span class="sxs-lookup"><span data-stu-id="141a4-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="141a4-122">Výraz lze snadno nahradit volání funkce.</span><span class="sxs-lookup"><span data-stu-id="141a4-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="141a4-123">**Čistota** -čistoty je vlastnost funkce tak, že vrácená hodnota je vždy stejný pro stejné argumenty a že jeho vyhodnocení nemá žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="141a4-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="141a4-124">Čistě funkci zcela závisí na jeho argumenty.</span><span class="sxs-lookup"><span data-stu-id="141a4-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="141a4-125">**Referenční transparentnosti** – referenční transparentnosti je vlastnost výrazů tak, že se dá nahradit výrazem jejich výstup bez ovlivnění chování programu.</span><span class="sxs-lookup"><span data-stu-id="141a4-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="141a4-126">**Neměnnost** -neměnnosti znamená, že hodnota nemůže být změněna na místě.</span><span class="sxs-lookup"><span data-stu-id="141a4-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="141a4-127">To je rozdíl od proměnné, které můžete změnit na místě.</span><span class="sxs-lookup"><span data-stu-id="141a4-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="141a4-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="141a4-128">Examples</span></span>

<span data-ttu-id="141a4-129">Následující příklady ukazují těmito základními koncepty.</span><span class="sxs-lookup"><span data-stu-id="141a4-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="141a4-130">Funkce</span><span class="sxs-lookup"><span data-stu-id="141a4-130">Functions</span></span>

<span data-ttu-id="141a4-131">Nejvíce běžné a základní konstrukcí funkčního programování je funkce.</span><span class="sxs-lookup"><span data-stu-id="141a4-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="141a4-132">Tady je jednoduchou funkci, která se přičte 1 k celým číslem:</span><span class="sxs-lookup"><span data-stu-id="141a4-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="141a4-133">Typ podpisu je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="141a4-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="141a4-134">Podpis může číst jako "`addOne` přijímá `int` s názvem `x` a vytvoří `int`".</span><span class="sxs-lookup"><span data-stu-id="141a4-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="141a4-135">Více formálně `addOne` je _mapování_ hodnotu ze sady celých čísel na sadu celých čísel.</span><span class="sxs-lookup"><span data-stu-id="141a4-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="141a4-136">`->` Token označuje, že toto mapování.</span><span class="sxs-lookup"><span data-stu-id="141a4-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="141a4-137">V F#, obvykle můžete se podívat na podpis funkce získali povědomí o co to dělá.</span><span class="sxs-lookup"><span data-stu-id="141a4-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="141a4-138">Ano, proč je podpis důležité?</span><span class="sxs-lookup"><span data-stu-id="141a4-138">So, why is the signature important?</span></span> <span data-ttu-id="141a4-139">V typu funkčního programování, implementace funkce je často méně důležitá než podpis skutečný typ!</span><span class="sxs-lookup"><span data-stu-id="141a4-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="141a4-140">Fakt, který `addOne` přidá hodnoty 1 na celé číslo je zajímavé za běhu, ale jsou při sestavování programu, skutečnost, že přijímá a vrací `int` je co informuje o tom, jak bude ve skutečnosti používat tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="141a4-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="141a4-141">Kromě toho po použití této funkce správně (s ohledem na její typ podpis), diagnostice potíží lze provést pouze v těle `addOne` funkce.</span><span class="sxs-lookup"><span data-stu-id="141a4-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="141a4-142">Toto je tak za zadaný funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="141a4-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="141a4-143">Výrazy</span><span class="sxs-lookup"><span data-stu-id="141a4-143">Expressions</span></span>

<span data-ttu-id="141a4-144">Výrazy jsou konstrukce, která se vyhodnotí na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="141a4-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="141a4-145">Na rozdíl od příkazů, které provádějí akci, výrazy můžete představit provést akci, která poskytuje vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="141a4-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="141a4-146">Výrazy se téměř vždy používají ve prospěch příkazy do funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="141a4-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="141a4-147">Zvažte předchozí funkci `addOne`.</span><span class="sxs-lookup"><span data-stu-id="141a4-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="141a4-148">Tělo `addOne` je výraz:</span><span class="sxs-lookup"><span data-stu-id="141a4-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="141a4-149">Výsledek tohoto výrazu, který definuje typ výsledku `addOne` funkce.</span><span class="sxs-lookup"><span data-stu-id="141a4-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="141a4-150">Například výraz, který tvoří tuto funkci, můžete ho změnit na jiný typ, například `string`:</span><span class="sxs-lookup"><span data-stu-id="141a4-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="141a4-151">Signatura funkce je teď:</span><span class="sxs-lookup"><span data-stu-id="141a4-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="141a4-152">Od libovolného typu v F# může mít `ToString()` volá v něm typ `x` byl proveden obecný (volá [Automatická generalizace](../language-reference/generics/automatic-generalization.md)), a výsledný typ je `string`.</span><span class="sxs-lookup"><span data-stu-id="141a4-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="141a4-153">Výrazy nejsou právě těla funkce.</span><span class="sxs-lookup"><span data-stu-id="141a4-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="141a4-154">Můžete použít výrazy, které vytvoří hodnotu, kterou můžete použít na jiném místě.</span><span class="sxs-lookup"><span data-stu-id="141a4-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="141a4-155">Běžný je `if`:</span><span class="sxs-lookup"><span data-stu-id="141a4-155">A common one is `if`:</span></span>

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

<span data-ttu-id="141a4-156">`if` Výraz vytvoří hodnotu s názvem `result`.</span><span class="sxs-lookup"><span data-stu-id="141a4-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="141a4-157">Všimněte si, že by mohla vynechat `result` úplně, aby `if` výraz text z `addOneIfOdd` funkce.</span><span class="sxs-lookup"><span data-stu-id="141a4-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="141a4-158">Nejdůležitější informace o výrazech je, že vytvářejí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="141a4-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="141a4-159">Je speciální typ `unit`, který se používá při není nutné nic vrátit.</span><span class="sxs-lookup"><span data-stu-id="141a4-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="141a4-160">Představte si třeba tato jednoduchá funkce:</span><span class="sxs-lookup"><span data-stu-id="141a4-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn "String is: %s" s
```

<span data-ttu-id="141a4-161">Podpis vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="141a4-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="141a4-162">`unit` Označuje, že neexistuje žádná skutečná hodnota se vrací.</span><span class="sxs-lookup"><span data-stu-id="141a4-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="141a4-163">To je užitečné, když máte rutinu, která musí "pracovní" bez ohledu na žádnou hodnotu vrátit jako výsledek, které pracují s.</span><span class="sxs-lookup"><span data-stu-id="141a4-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="141a4-164">Toto je sharp oproti imperativní programování, kde ekvivalent `if` konstrukce je příkaz a vytváření hodnoty se často provádí pomocí mutace proměnné.</span><span class="sxs-lookup"><span data-stu-id="141a4-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="141a4-165">Například v C#, kód může být napsán takto:</span><span class="sxs-lookup"><span data-stu-id="141a4-165">For example, in C#, the code might be written like this:</span></span>

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

<span data-ttu-id="141a4-166">Je vhodné poznamenat, že C# a podpora jiných jazyků C-style [Ternární výraz](../../csharp/language-reference/operators/conditional-operator.md), což umožňuje založené na výrazu podmíněné programování.</span><span class="sxs-lookup"><span data-stu-id="141a4-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="141a4-167">Funkční programování v zřídka dochází k mutovat hodnoty s příkazy.</span><span class="sxs-lookup"><span data-stu-id="141a4-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="141a4-168">I když některé funkční jazyky podporují příkazy a mutace, není běžné použití těchto konceptů v funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="141a4-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="141a4-169">Čistě funkce</span><span class="sxs-lookup"><span data-stu-id="141a4-169">Pure functions</span></span>

<span data-ttu-id="141a4-170">Dříve jsme už zmínili, čistě funkce jsou funkce:</span><span class="sxs-lookup"><span data-stu-id="141a4-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="141a4-171">Vždy vyhodnoťte na stejnou hodnotu pro stejný vstup.</span><span class="sxs-lookup"><span data-stu-id="141a4-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="141a4-172">Mít žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="141a4-172">Have no side effects.</span></span>

<span data-ttu-id="141a4-173">Je vhodné si můžete představit matematické funkce v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="141a4-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="141a4-174">Funkce v matematice, záviset pouze na jejich argumenty a nemá žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="141a4-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="141a4-175">V matematické funkce `f(x) = x + 1`, hodnota `f(x)` závisí jenom na základě hodnoty `x`.</span><span class="sxs-lookup"><span data-stu-id="141a4-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="141a4-176">Čistě funkce do funkčního programování se stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="141a4-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="141a4-177">Při zápisu čistě funkce, funkce musí záviset pouze na jeho argumenty a nebude provádět žádnou akci, která má za následek vedlejší účinek.</span><span class="sxs-lookup"><span data-stu-id="141a4-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="141a4-178">Tady je příklad-čistě funkce, protože závisí na globální, proměnlivý stav:</span><span class="sxs-lookup"><span data-stu-id="141a4-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="141a4-179">`addOneToValue` Funkce je jasně znečištěná, protože `value` lze změnit kdykoli mít jinou hodnotu než 1.</span><span class="sxs-lookup"><span data-stu-id="141a4-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="141a4-180">V závislosti na globální hodnoty tohoto vzoru je třeba se vyhnout do funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="141a4-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="141a4-181">Tady je další příklad – čistě funkce, protože vykonává vedlejší účinek:</span><span class="sxs-lookup"><span data-stu-id="141a4-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="141a4-182">I když tato funkce není závislý na globální hodnoty, zapíše hodnoty `x` do výstupu programu.</span><span class="sxs-lookup"><span data-stu-id="141a4-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="141a4-183">I když není nic špatného ze své podstaty s tím, znamená, že funkce není čistě.</span><span class="sxs-lookup"><span data-stu-id="141a4-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span>

<span data-ttu-id="141a4-184">Odebírá `printfn` příkazu finally díky funkci čistě:</span><span class="sxs-lookup"><span data-stu-id="141a4-184">Removing the `printfn` statement finally makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="141a4-185">I když tato funkce není ze své podstaty _lepší_ než předchozí verze s `printfn` příkazu, to zaručit, že všechny této funkce je vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="141a4-185">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="141a4-186">Toto volání funkce jednou nebo 1 miliardu dobu bude stále výsledkem stejnou věc: stačí vytváření hodnotu.</span><span class="sxs-lookup"><span data-stu-id="141a4-186">Calling this function once or 1 billion times will still result in the same thing: just producing a value.</span></span> <span data-ttu-id="141a4-187">Tato předvídatelnost je důležité v funkčního programování, protože to znamená, že všechny čistě funkce je referentially transparentní.</span><span class="sxs-lookup"><span data-stu-id="141a4-187">This predictability is valuable in functional programming, as it means that any pure function is referentially transparent.</span></span>

### <a name="referential-transparency"></a><span data-ttu-id="141a4-188">Referenční transparentnosti</span><span class="sxs-lookup"><span data-stu-id="141a4-188">Referential Transparency</span></span>

<span data-ttu-id="141a4-189">Referenční transparentnosti je vlastnost výrazy a funkce.</span><span class="sxs-lookup"><span data-stu-id="141a4-189">Referential transparency is a property of expressions and functions.</span></span> <span data-ttu-id="141a4-190">Pro výraz referentially transparentní musí mít možnost nahradit jeho výsledná hodnota beze změny chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="141a4-190">For an expression to be referentially transparent, it must be able to be replaced with its resulting value without changing the program's behavior.</span></span> <span data-ttu-id="141a4-191">Všechny čistě funkce jsou referentially transparentní.</span><span class="sxs-lookup"><span data-stu-id="141a4-191">All pure functions are referentially transparent.</span></span>

<span data-ttu-id="141a4-192">Stejně jako u čistě funkce, může být užitečné si můžete představit referenční transparentnost z hlediska matematické.</span><span class="sxs-lookup"><span data-stu-id="141a4-192">As with pure functions, it can be helpful to think of referential transparency from a mathematical perspective.</span></span> <span data-ttu-id="141a4-193">V matematickém výrazu `y = f(x)`, `f(x)` lze nahradit výsledek funkce a stále bude rovnat `y`.</span><span class="sxs-lookup"><span data-stu-id="141a4-193">In the mathematical expression `y = f(x)`, `f(x)` can be replaced by the result of the function and it will still be equal to `y`.</span></span> <span data-ttu-id="141a4-194">To platí stejně pro referenční transparentnosti funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="141a4-194">This is equally true for referential transparency in functional programming.</span></span>

<span data-ttu-id="141a4-195">Zvažte možnost volání dříve definované `addOneIfOdd` funkce dvakrát:</span><span class="sxs-lookup"><span data-stu-id="141a4-195">Consider calling the previously defined `addOneIfOdd` function twice:</span></span>

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

let res1 = addOneIffOdd 1 // Produces 2
let res2 = addOneIffOdd 2 // Produces 2
```

<span data-ttu-id="141a4-196">Jsme můžete nahradit každé volání funkce tělo funkce nahrazování argument `input` jednotlivé hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="141a4-196">We can replace each function call with the function body, substituting the argument `input` with each value:</span></span>

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

let res1 =
    let result =
        if isOdd 1 then
            1 + 1
        else
            1

    result
let res2 =
    let result =
        if isOdd 2 then
            2 + 1
        else
            2

    result
```

<span data-ttu-id="141a4-197">Obě `res1` a `res2` mají stejnou hodnotu, jako kdyby byla volána funkce, což indikuje, že `addOneIfOdd` je referentially transparentní!</span><span class="sxs-lookup"><span data-stu-id="141a4-197">Both `res1` and `res2` have the same value as if the function was called, indicating that `addOneIfOdd` is referentially transparent!</span></span>

<span data-ttu-id="141a4-198">Kromě toho funkce nemusí být čistě také být referentially transparentní.</span><span class="sxs-lookup"><span data-stu-id="141a4-198">Additionally, a function doesn't have to be pure to also be referentially transparent.</span></span> <span data-ttu-id="141a4-199">Zvažte předchozí definice `addOneTovalue`:</span><span class="sxs-lookup"><span data-stu-id="141a4-199">Consider a previous definition of  `addOneTovalue`:</span></span>

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="141a4-200">Voláním této funkce lze také nahradit jeho textu a stejné dojde pokaždé, když:</span><span class="sxs-lookup"><span data-stu-id="141a4-200">Any call to this function can also be replaced by its body and the same things will happen each time:</span></span>

* <span data-ttu-id="141a4-201">Hodnota před přidáním do, je vytisknout výstup</span><span class="sxs-lookup"><span data-stu-id="141a4-201">The value, prior to being added to, is printed to the output</span></span>
* <span data-ttu-id="141a4-202">Hodnota je 1 přidány do tohoto fondu</span><span class="sxs-lookup"><span data-stu-id="141a4-202">The value has 1 added to it</span></span>

<span data-ttu-id="141a4-203">Při programování v F#, je často referenční transparentnosti, který je cíle, spíše než čistoty.</span><span class="sxs-lookup"><span data-stu-id="141a4-203">When programming in F#, it is often referential transparency that is the goal, rather than purity.</span></span> <span data-ttu-id="141a4-204">Je však stále vhodné k zápisu čistě funkce, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="141a4-204">However, it is still good practice to write pure functions when you can.</span></span>

### <a name="immutability"></a><span data-ttu-id="141a4-205">Neměnnost</span><span class="sxs-lookup"><span data-stu-id="141a4-205">Immutability</span></span>

<span data-ttu-id="141a4-206">Nakonec jednou z nejvíce základní koncepty typu funkční programování je neměnnosti.</span><span class="sxs-lookup"><span data-stu-id="141a4-206">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="141a4-207">V F#, všechny hodnoty jsou neměnné ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="141a4-207">In F#, all values are immutable by default.</span></span> <span data-ttu-id="141a4-208">To znamená, že pokud je explicitně označit jako mutable nemohou být místně měněna.</span><span class="sxs-lookup"><span data-stu-id="141a4-208">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="141a4-209">V praxi práce s hodnotami neměnné znamená, že změníte svůj přístup k programování z "Budu muset něco změnit" k "budu potřebovat k vytvoření nové hodnoty".</span><span class="sxs-lookup"><span data-stu-id="141a4-209">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="141a4-210">Například přidáním 1 na hodnotu znamená, že vytváří novou hodnotu, nikoli mutace stávající:</span><span class="sxs-lookup"><span data-stu-id="141a4-210">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="141a4-211">V F#, následující kód provede **není** mutovat `value` funkce; místo toho provádí kontrolu rovnosti:</span><span class="sxs-lookup"><span data-stu-id="141a4-211">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="141a4-212">Některé funkční programovací jazyky nepodporují mutace vůbec.</span><span class="sxs-lookup"><span data-stu-id="141a4-212">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="141a4-213">V F#, DPM ji podporuje, ale není výchozí chování pro hodnoty.</span><span class="sxs-lookup"><span data-stu-id="141a4-213">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="141a4-214">Tento koncept se rozšiřuje i dál datové struktury.</span><span class="sxs-lookup"><span data-stu-id="141a4-214">This concept extends even further to data structures.</span></span> <span data-ttu-id="141a4-215">Funkční programování v neměnných datové struktury, jako je sad (a mnoho dalších) mají jinou implementaci než může být zpočátku očekávat.</span><span class="sxs-lookup"><span data-stu-id="141a4-215">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="141a4-216">Entity typu přidání položky do sady nedojde ke změně sady, vytváří _nové_ nastavit s přidanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="141a4-216">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="141a4-217">Pod pokličkou to často provádí různé datová struktura, která umožňuje efektivní sledování hodnotu tak, aby odpovídající znázornění dat mohou být zadány ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="141a4-217">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="141a4-218">Tento styl práci s hodnotami a datové struktury je důležité, jak přistupovat ke všem jakoukoli operaci, která upravuje něco, jako kdyby vytvoří novou verzi celou věc nepropojili nutí.</span><span class="sxs-lookup"><span data-stu-id="141a4-218">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="141a4-219">To umožňuje například rovnosti a srovnání být konzistentní vzhledem k aplikacím ve svých programech.</span><span class="sxs-lookup"><span data-stu-id="141a4-219">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="141a4-220">Další kroky</span><span class="sxs-lookup"><span data-stu-id="141a4-220">Next steps</span></span>

<span data-ttu-id="141a4-221">V další části se bude vztahovat důkladně funkce zkoumání různých způsobů, jak lze využít v funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="141a4-221">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="141a4-222">[Funkce první třídy](first-class-functions.md) zkoumá funkce hluboko, zobrazuje, jak je lze využít v různých kontextech.</span><span class="sxs-lookup"><span data-stu-id="141a4-222">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="141a4-223">Další čtení</span><span class="sxs-lookup"><span data-stu-id="141a4-223">Further reading</span></span>

<span data-ttu-id="141a4-224">[Uvažujete funkčně](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series je další informace o funkční programování s dalším skvělým zdrojem F#.</span><span class="sxs-lookup"><span data-stu-id="141a4-224">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="141a4-225">Popisuje základní informace o funkční programování tak pragmatický a snadné čtení pomocí F# funkce pro objasnění konceptů.</span><span class="sxs-lookup"><span data-stu-id="141a4-225">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>