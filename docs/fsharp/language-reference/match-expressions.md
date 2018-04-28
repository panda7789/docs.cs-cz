---
title: 'Výrazy shody (F #)'
description: 'Zjistěte, jak výrazu shody F # poskytuje větvení ovládací prvek, který je založena na porovnávání výrazu sadu vzory.'
author: cartermp
ms.author: phcart
ms.date: 04/19/2018
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f6930f782384464f0d44b205ea77cbaf43898213
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="match-expressions"></a><span data-ttu-id="6b56a-103">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="6b56a-103">Match expressions</span></span>

<span data-ttu-id="6b56a-104">`match` Výraz poskytuje větvení ovládací prvek, který je založena na porovnávání výrazu sadu vzory.</span><span class="sxs-lookup"><span data-stu-id="6b56a-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b56a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b56a-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="6b56a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b56a-106">Remarks</span></span>

<span data-ttu-id="6b56a-107">Výrazy odpovídající vzor umožňují komplexní vytvoření větve na základě porovnání výraz testovací sadu vzory.</span><span class="sxs-lookup"><span data-stu-id="6b56a-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="6b56a-108">V `match` výrazu *testovací výraz* se porovná se každý vzor zapnout, a pokud je nalezena shoda, odpovídající *výsledek výrazu* vyhodnotí a výsledná hodnota je Vrátí hodnotu výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="6b56a-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="6b56a-109">Funkce uvedené v předchozí syntaxe pro porovnávání je v které vzor odpovídající provádí okamžitě v argumentu výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="6b56a-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="6b56a-110">Funkce uvedené v předchozí syntaxe pro porovnávání je stejná jako následující.</span><span class="sxs-lookup"><span data-stu-id="6b56a-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="6b56a-111">Další informace o výrazy lambda najdete v tématu [výrazy Lambda: `fun` – klíčové slovo](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="6b56a-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="6b56a-112">Celou sadu vzory by mělo zahrnovat všechny možné shody vstupní proměnné.</span><span class="sxs-lookup"><span data-stu-id="6b56a-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="6b56a-113">Často používají vzorec zástupný znak (`_`) jako poslední vzorek tak, aby odpovídaly všechny dříve neodpovídající vstupní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6b56a-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="6b56a-114">Následující kód ukazuje některé způsoby, ve kterém `match` použit výraz.</span><span class="sxs-lookup"><span data-stu-id="6b56a-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="6b56a-115">Odkaz a příklady možných vzorů, které lze použít, najdete v části [porovnávání vzorů](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="6b56a-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="6b56a-116">Chrání vzory</span><span class="sxs-lookup"><span data-stu-id="6b56a-116">Guards on patterns</span></span>

<span data-ttu-id="6b56a-117">Můžete použít `when` klauzule zadejte další podmínky, které proměnnou, musí vyhovovat tak, aby odpovídaly vzor.</span><span class="sxs-lookup"><span data-stu-id="6b56a-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="6b56a-118">Tato klauzule odkazuje jako *ochrana*.</span><span class="sxs-lookup"><span data-stu-id="6b56a-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="6b56a-119">Následující výraz `when` – klíčové slovo, nebude hodnocen pouze tehdy, pokud shoda se se vzorem přidružené k této ochrana.</span><span class="sxs-lookup"><span data-stu-id="6b56a-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="6b56a-120">Následující příklad ukazuje použití ochranu k určení číselný rozsah pro proměnné vzor.</span><span class="sxs-lookup"><span data-stu-id="6b56a-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="6b56a-121">Všimněte si, že více podmínek jsou spojeny použitím logické operátory.</span><span class="sxs-lookup"><span data-stu-id="6b56a-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="6b56a-122">Všimněte si, že vzhledem k tomu, že hodnoty než literály nelze použít ve vzoru, musíte použít `when` klauzule, pokud máte k porovnání některé části vstup pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6b56a-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="6b56a-123">To je ukázáno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6b56a-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="6b56a-124">Všimněte si, že když union vzor je předmětem ochranu, ochranného zařízení aplikuje na **všechny** schémat, ne jenom tu poslední.</span><span class="sxs-lookup"><span data-stu-id="6b56a-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="6b56a-125">Například následující kód, ochranného zařízení uděleno `when a > 12` platí pro obě `A a` a `B a`:</span><span class="sxs-lookup"><span data-stu-id="6b56a-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6b56a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b56a-126">See also</span></span>

[<span data-ttu-id="6b56a-127">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="6b56a-127">F# Language Reference</span></span>](index.md)  
[<span data-ttu-id="6b56a-128">Aktivní vzory</span><span class="sxs-lookup"><span data-stu-id="6b56a-128">Active Patterns</span></span>](active-patterns.md)  
[<span data-ttu-id="6b56a-129">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="6b56a-129">Pattern Matching</span></span>](pattern-matching.md)  
