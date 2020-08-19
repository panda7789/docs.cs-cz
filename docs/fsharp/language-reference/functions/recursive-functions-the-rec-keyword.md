---
title: 'Rekurzivní funkce: Klíčové slovo rec'
description: Zjistěte, jak se klíčové slovo REC používá s klíčovým slovem let k definování rekurzivní funkce.
ms.date: 08/12/2020
ms.openlocfilehash: 389357bd13cef39b1d07972c1a3167320b61612b
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558709"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="44e6f-103">Rekurzivní funkce: Klíčové slovo rec</span><span class="sxs-lookup"><span data-stu-id="44e6f-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="44e6f-104">`rec`Klíčové slovo se používá společně s `let` klíčovým slovem k definování rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="44e6f-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="44e6f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="44e6f-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
    function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
    function1-body

and function2-nameparameter-list =
    function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="44e6f-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44e6f-106">Remarks</span></span>

<span data-ttu-id="44e6f-107">Rekurzivní funkce – funkce, které volají samy – jsou identifikovány explicitně v jazyce F # s `rec` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="44e6f-107">Recursive functions - functions that call themselves - are identified explicitly in the F# language with the `rec` keyword.</span></span> <span data-ttu-id="44e6f-108">`rec`Klíčové slovo vytvoří název vazby, která je `let` k dispozici v těle.</span><span class="sxs-lookup"><span data-stu-id="44e6f-108">The `rec` keyword makes the name of the `let` binding available in its body.</span></span>

<span data-ttu-id="44e6f-109">Následující příklad ukazuje rekurzivní funkci, která vypočítá *n*-<sup>tý</sup> Fibonacci číslo pomocí matematické definice.</span><span class="sxs-lookup"><span data-stu-id="44e6f-109">The following example shows a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

```fsharp
let fib n =
    match n with
    | 0 | 1 -> 1
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> <span data-ttu-id="44e6f-110">V praxi není kód podobný předchozí ukázce ideální, protože unecessarily přepočítá hodnoty, které již byly vypočítány.</span><span class="sxs-lookup"><span data-stu-id="44e6f-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="44e6f-111">Důvodem je to, že není rekurzivní, což je vysvětleno dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="44e6f-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="44e6f-112">Metody jsou implicitně rekurzivní v rámci typu, který je definován v, což znamená, že není nutné přidávat `rec` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="44e6f-112">Methods are implicitly recursive within the type they are defined in, meaning there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="44e6f-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="44e6f-113">For example:</span></span>

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> 1
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

<span data-ttu-id="44e6f-114">Umožňuje, aby vazby v rámci tříd nebyly implicitně rekurzivní, ale.</span><span class="sxs-lookup"><span data-stu-id="44e6f-114">Let bindings within classes are not implicitly recursive, though.</span></span> <span data-ttu-id="44e6f-115">Všechny `let` funkce svázané s `rec` klíčovým slovem vyžadují klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="44e6f-115">All `let`-bound functions require the `rec` keyword.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="44e6f-116">Koncová rekurze</span><span class="sxs-lookup"><span data-stu-id="44e6f-116">Tail recursion</span></span>

<span data-ttu-id="44e6f-117">U některých rekurzivních funkcí je nutné Refaktorovat více "čisté" definice na hodnotu, která je [argumentem rekurzivně](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span><span class="sxs-lookup"><span data-stu-id="44e6f-117">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="44e6f-118">To brání zbytečnému přepočítání.</span><span class="sxs-lookup"><span data-stu-id="44e6f-118">This prevents unnecessary recomputations.</span></span> <span data-ttu-id="44e6f-119">Například může přepsat předchozí generátor čísel Fibonacci takto:</span><span class="sxs-lookup"><span data-stu-id="44e6f-119">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

<span data-ttu-id="44e6f-120">Toto je složitější implementace.</span><span class="sxs-lookup"><span data-stu-id="44e6f-120">This is a more complicated implementation.</span></span> <span data-ttu-id="44e6f-121">Generování Fibonacci čísla je skvělým příkladem algoritmu "Naive", který je matematicky čistý, ale v praxi je neefektivní.</span><span class="sxs-lookup"><span data-stu-id="44e6f-121">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="44e6f-122">Několik aspektů je efektivní v F #, ale stále ještě zbývá rekurzivně definovat:</span><span class="sxs-lookup"><span data-stu-id="44e6f-122">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="44e6f-123">Rekurzivní vnitřní funkce s názvem `loop` , což je vzor Idiomatickou F #.</span><span class="sxs-lookup"><span data-stu-id="44e6f-123">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="44e6f-124">Dva parametry akumulátoru, které předají hodnoty do rekurzivních volání.</span><span class="sxs-lookup"><span data-stu-id="44e6f-124">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="44e6f-125">Kontrolu hodnoty `n` pro vrácení konkrétního hromadění.</span><span class="sxs-lookup"><span data-stu-id="44e6f-125">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="44e6f-126">Pokud byl tento příklad napsán cyklicky se smyčkou, kód by vypadal podobně jako dvě různé hodnoty nahromadění čísel, dokud nebyla splněna určitá podmínka.</span><span class="sxs-lookup"><span data-stu-id="44e6f-126">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="44e6f-127">Důvod, proč je to zakončené – rekurzivní je, protože rekurzivní volání nemusí ukládat žádné hodnoty do zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="44e6f-127">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="44e6f-128">Všechny vypočtené mezilehlé hodnoty jsou shromažďovány prostřednictvím vstupů do vnitřní funkce.</span><span class="sxs-lookup"><span data-stu-id="44e6f-128">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="44e6f-129">To také umožňuje kompilátoru F # optimalizovat kód tak, aby byl přesně tak rychle, jako kdyby byl napsán jako `while` smyčka.</span><span class="sxs-lookup"><span data-stu-id="44e6f-129">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="44e6f-130">Je běžné psát kód F #, který rekurzivně zpracovává něco s vnitřní a vnější funkcí, jak ukazuje předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="44e6f-130">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="44e6f-131">Vnitřní funkce používá funkci Tail s koncovou rekurzí, zatímco vnější funkce má lepší rozhraní pro volající.</span><span class="sxs-lookup"><span data-stu-id="44e6f-131">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="44e6f-132">Vzájemně rekurzivní funkce</span><span class="sxs-lookup"><span data-stu-id="44e6f-132">Mutually Recursive Functions</span></span>

<span data-ttu-id="44e6f-133">Funkce jsou někdy *vzájemně rekurzivní*, což znamená, že volání tvoří kruh, kde jedna funkce volá metodu, která zavolá první, s libovolným počtem volání mezi.</span><span class="sxs-lookup"><span data-stu-id="44e6f-133">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="44e6f-134">Tyto funkce musíte definovat společně v jedné `let` vazbě pomocí `and` klíčového slova k jejich propojení.</span><span class="sxs-lookup"><span data-stu-id="44e6f-134">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="44e6f-135">Následující příklad ukazuje dvě vzájemně rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="44e6f-135">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="recursive-values"></a><span data-ttu-id="44e6f-136">Rekurzivní hodnoty</span><span class="sxs-lookup"><span data-stu-id="44e6f-136">Recursive values</span></span>

<span data-ttu-id="44e6f-137">Můžete také definovat `let` hodnotu vazby, která má být rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="44e6f-137">You can also define a `let`-bound value to be recursive.</span></span> <span data-ttu-id="44e6f-138">Tato situace se někdy provádí pro protokolování.</span><span class="sxs-lookup"><span data-stu-id="44e6f-138">This is sometimes done for logging.</span></span> <span data-ttu-id="44e6f-139">V F # 5 a `nameof` funkci to můžete udělat:</span><span class="sxs-lookup"><span data-stu-id="44e6f-139">With F# 5 and the `nameof` function, you can do this:</span></span>

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a><span data-ttu-id="44e6f-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="44e6f-140">See also</span></span>

- [<span data-ttu-id="44e6f-141">Functions</span><span class="sxs-lookup"><span data-stu-id="44e6f-141">Functions</span></span>](index.md)
