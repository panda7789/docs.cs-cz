---
title: Výrazy shody (F#)
description: Zjistěte, jak výrazu porovnání F# poskytuje větvení ovládací prvek, který je založena na porovnávání výrazů sadu vzorů.
ms.date: 04/19/2018
ms.openlocfilehash: e4cb82f20fe82bff562736557c2346562c557f59
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44221841"
---
# <a name="match-expressions"></a><span data-ttu-id="b826e-103">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="b826e-103">Match expressions</span></span>

<span data-ttu-id="b826e-104">`match` Výraz poskytuje větvení ovládací prvek, který je založena na porovnávání výrazů sadu vzorů.</span><span class="sxs-lookup"><span data-stu-id="b826e-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="b826e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b826e-105">Syntax</span></span>

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a><span data-ttu-id="b826e-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b826e-106">Remarks</span></span>

<span data-ttu-id="b826e-107">Vzor odpovídající výrazy umožňují na základě porovnání výrazu testovací sadu vzorů komplexní větvení.</span><span class="sxs-lookup"><span data-stu-id="b826e-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="b826e-108">V `match` výrazu, *výrazu testu* se porovná se každý vzorek, v důsledku, a když je nalezena shoda, odpovídající *výsledek výrazu* je vyhodnocen a je výsledná hodnota Vrátí jako hodnota výrazu match.</span><span class="sxs-lookup"><span data-stu-id="b826e-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="b826e-109">Porovnávání vzorů funkce je znázorněno v předchozí syntaxi je výraz lambda, který vzoru porovnávání je okamžitě na argumentu provedeno.</span><span class="sxs-lookup"><span data-stu-id="b826e-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="b826e-110">Porovnávání vzorů funkce je znázorněno v předchozí syntaxi je ekvivalentní následujícímu zápisu.</span><span class="sxs-lookup"><span data-stu-id="b826e-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="b826e-111">Další informace o výrazech lambda naleznete v tématu [výrazy Lambda: `fun` – klíčové slovo](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="b826e-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="b826e-112">Možných shod je vstupní proměnná by měla zahrnovat celou sadu vzorů.</span><span class="sxs-lookup"><span data-stu-id="b826e-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="b826e-113">Často, použijte vzor zástupných znaků (`_`) jako poslední vzorek tak, aby odpovídaly všechny dříve bezkonkurenční vstupní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b826e-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="b826e-114">Následující kód ukazuje několik způsobů jak, ve kterém `match` výraz je použit.</span><span class="sxs-lookup"><span data-stu-id="b826e-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="b826e-115">Odkaz a příklady možných vzory, které lze použít, naleznete v tématu [porovnávání vzorů](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="b826e-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="b826e-116">Výrazy guard na vzory</span><span class="sxs-lookup"><span data-stu-id="b826e-116">Guards on patterns</span></span>

<span data-ttu-id="b826e-117">Můžete použít `when` klauzule zadat další podmínku, která proměnná musí splňovat odpovídající vzorku.</span><span class="sxs-lookup"><span data-stu-id="b826e-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="b826e-118">Tato klauzule se označuje jako *guard*.</span><span class="sxs-lookup"><span data-stu-id="b826e-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="b826e-119">Následující výraz `when` – klíčové slovo není vyhodnocen, pokud není shoda vzoru přidružené k této guard.</span><span class="sxs-lookup"><span data-stu-id="b826e-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="b826e-120">Následující příklad ukazuje použití ochranného zařízení můžete určit číselný rozsah pro vzor proměnné.</span><span class="sxs-lookup"><span data-stu-id="b826e-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="b826e-121">Všimněte si, že jsou více podmínek kombinovat pomocí logické operátory.</span><span class="sxs-lookup"><span data-stu-id="b826e-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="b826e-122">Mějte na paměti, protože hodnoty jiné než literály nelze použít ve vzoru, je nutné použít `when` klauzule, pokud máte k porovnání některá část vstup podle dokumentu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b826e-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="b826e-123">To je ukázáno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="b826e-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="b826e-124">Všimněte si, že pokud vzor sjednocení se bude vztahovat ochranu, ochranného zařízení platí pro **všechny** vzorů, ne jenom poslední z nich.</span><span class="sxs-lookup"><span data-stu-id="b826e-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="b826e-125">Mějme například následující kód, ochranného zařízení `when a > 12` platí jak `A a` a `B a`:</span><span class="sxs-lookup"><span data-stu-id="b826e-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a><span data-ttu-id="b826e-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b826e-126">See also</span></span>

- [<span data-ttu-id="b826e-127">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="b826e-127">F# Language Reference</span></span>](index.md)  
- [<span data-ttu-id="b826e-128">Aktivní vzory</span><span class="sxs-lookup"><span data-stu-id="b826e-128">Active Patterns</span></span>](active-patterns.md)  
- [<span data-ttu-id="b826e-129">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="b826e-129">Pattern Matching</span></span>](pattern-matching.md)  
