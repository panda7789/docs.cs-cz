---
title: 'Rekurzivní funkce: Klíčové slovo rec'
description: Zjistěte, jak se klíčové slovo REC používá s klíčovým slovem let k definování rekurzivní funkce.
ms.date: 05/16/2016
ms.openlocfilehash: c9a3b7dc27f4ed86948a08b7783d7e8e8b60e57f
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2020
ms.locfileid: "87426973"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="58bcc-103">Rekurzivní funkce: Klíčové slovo rec</span><span class="sxs-lookup"><span data-stu-id="58bcc-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="58bcc-104">`rec`Klíčové slovo se používá společně s `let` klíčovým slovem k definování rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="58bcc-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="58bcc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58bcc-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="58bcc-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58bcc-106">Remarks</span></span>

<span data-ttu-id="58bcc-107">Rekurzivní funkce, funkce, které volají samy sebe, jsou identifikovány explicitně v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="58bcc-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="58bcc-108">Tím se identifikátorem, které je definováno v oboru funkce.</span><span class="sxs-lookup"><span data-stu-id="58bcc-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="58bcc-109">Následující kód ilustruje rekurzivní funkci, která vypočítá n- *n*<sup>tý</sup> Fibonacci číslo pomocí matematické definice.</span><span class="sxs-lookup"><span data-stu-id="58bcc-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="58bcc-110">V praxi není kód podobný předchozí ukázce ideální, protože unecessarily přepočítá hodnoty, které již byly vypočítány.</span><span class="sxs-lookup"><span data-stu-id="58bcc-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="58bcc-111">Důvodem je to, že není rekurzivní, což je vysvětleno dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="58bcc-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="58bcc-112">Metody jsou implicitně rekurzivní v rámci typu; není nutné přidávat `rec` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="58bcc-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="58bcc-113">Umožňuje, aby vazby v rámci tříd nebyly implicitně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="58bcc-113">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="58bcc-114">Koncová rekurze</span><span class="sxs-lookup"><span data-stu-id="58bcc-114">Tail recursion</span></span>

<span data-ttu-id="58bcc-115">U některých rekurzivních funkcí je nutné Refaktorovat více "čisté" definice na hodnotu, která je [argumentem rekurzivně](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span><span class="sxs-lookup"><span data-stu-id="58bcc-115">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="58bcc-116">Tím zabráníte reunecessarym recompute.</span><span class="sxs-lookup"><span data-stu-id="58bcc-116">This prevents unecessary recomputations.</span></span> <span data-ttu-id="58bcc-117">Například může přepsat předchozí generátor čísel Fibonacci takto:</span><span class="sxs-lookup"><span data-stu-id="58bcc-117">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

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

<span data-ttu-id="58bcc-118">Toto je složitější implementace.</span><span class="sxs-lookup"><span data-stu-id="58bcc-118">This is a more complicated implementation.</span></span> <span data-ttu-id="58bcc-119">Generování Fibonacci čísla je skvělým příkladem algoritmu "Naive", který je matematicky čistý, ale v praxi je neefektivní.</span><span class="sxs-lookup"><span data-stu-id="58bcc-119">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="58bcc-120">Několik aspektů je efektivní v F #, ale stále ještě zbývá rekurzivně definovat:</span><span class="sxs-lookup"><span data-stu-id="58bcc-120">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="58bcc-121">Rekurzivní vnitřní funkce s názvem `loop` , což je vzor Idiomatickou F #.</span><span class="sxs-lookup"><span data-stu-id="58bcc-121">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="58bcc-122">Dva parametry akumulátoru, které předají hodnoty do rekurzivních volání.</span><span class="sxs-lookup"><span data-stu-id="58bcc-122">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="58bcc-123">Kontrolu hodnoty `n` pro vrácení konkrétního hromadění.</span><span class="sxs-lookup"><span data-stu-id="58bcc-123">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="58bcc-124">Pokud byl tento příklad napsán cyklicky se smyčkou, kód by vypadal podobně jako dvě různé hodnoty nahromadění čísel, dokud nebyla splněna určitá podmínka.</span><span class="sxs-lookup"><span data-stu-id="58bcc-124">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="58bcc-125">Důvod, proč je to zakončené – rekurzivní je, protože rekurzivní volání nemusí ukládat žádné hodnoty do zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="58bcc-125">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="58bcc-126">Všechny vypočtené mezilehlé hodnoty jsou shromažďovány prostřednictvím vstupů do vnitřní funkce.</span><span class="sxs-lookup"><span data-stu-id="58bcc-126">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="58bcc-127">To také umožňuje kompilátoru F # optimalizovat kód tak, aby byl přesně tak rychle, jako kdyby byl napsán jako `while` smyčka.</span><span class="sxs-lookup"><span data-stu-id="58bcc-127">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="58bcc-128">Je běžné psát kód F #, který rekurzivně zpracovává něco s vnitřní a vnější funkcí, jak ukazuje předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="58bcc-128">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="58bcc-129">Vnitřní funkce používá funkci Tail s koncovou rekurzí, zatímco vnější funkce má lepší rozhraní pro volající.</span><span class="sxs-lookup"><span data-stu-id="58bcc-129">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="58bcc-130">Vzájemně rekurzivní funkce</span><span class="sxs-lookup"><span data-stu-id="58bcc-130">Mutually Recursive Functions</span></span>

<span data-ttu-id="58bcc-131">Funkce jsou někdy *vzájemně rekurzivní*, což znamená, že volání tvoří kruh, kde jedna funkce volá metodu, která zavolá první, s libovolným počtem volání mezi.</span><span class="sxs-lookup"><span data-stu-id="58bcc-131">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="58bcc-132">Tyto funkce musíte definovat společně v jedné `let` vazbě pomocí `and` klíčového slova k jejich propojení.</span><span class="sxs-lookup"><span data-stu-id="58bcc-132">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="58bcc-133">Následující příklad ukazuje dvě vzájemně rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="58bcc-133">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="58bcc-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58bcc-134">See also</span></span>

- [<span data-ttu-id="58bcc-135">Functions</span><span class="sxs-lookup"><span data-stu-id="58bcc-135">Functions</span></span>](index.md)
