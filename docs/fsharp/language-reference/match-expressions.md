---
title: "Výrazy shody (F#)"
description: "Zjistěte, jak výrazu shody F # poskytuje větvení ovládací prvek, který je založena na porovnávání výrazu sadu vzory."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8854b713-255a-408d-942a-e80ab52fd2a4
ms.openlocfilehash: c8b9be744cfa7bc76f0d663b12abd66f8757fc56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="match-expressions"></a><span data-ttu-id="04ecb-104">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="04ecb-104">Match Expressions</span></span>

<span data-ttu-id="04ecb-105">`match` Výraz poskytuje větvení ovládací prvek, který je založena na porovnávání výrazu sadu vzory.</span><span class="sxs-lookup"><span data-stu-id="04ecb-105">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="04ecb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04ecb-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="04ecb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04ecb-107">Remarks</span></span>

<span data-ttu-id="04ecb-108">Výrazy odpovídající vzor umožňují komplexní vytvoření větve na základě porovnání výraz testovací sadu vzory.</span><span class="sxs-lookup"><span data-stu-id="04ecb-108">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="04ecb-109">V `match` výrazu *testovací výraz* se porovná se každý vzor zapnout, a pokud je nalezena shoda, odpovídající *výsledek výrazu* vyhodnotí a výsledná hodnota je Vrátí hodnotu výrazu shody.</span><span class="sxs-lookup"><span data-stu-id="04ecb-109">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="04ecb-110">Funkce uvedené v předchozí syntaxe pro porovnávání je v které vzor odpovídající provádí okamžitě v argumentu výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="04ecb-110">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="04ecb-111">Funkce uvedené v předchozí syntaxe pro porovnávání je stejná jako následující.</span><span class="sxs-lookup"><span data-stu-id="04ecb-111">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```    

<span data-ttu-id="04ecb-112">Další informace o výrazy lambda najdete v tématu [výrazy Lambda: `fun` – klíčové slovo](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="04ecb-112">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="04ecb-113">Celou sadu vzory by mělo zahrnovat všechny možné shody vstupní proměnné.</span><span class="sxs-lookup"><span data-stu-id="04ecb-113">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="04ecb-114">Často používají vzorec zástupný znak (`_`) jako poslední vzorek tak, aby odpovídaly všechny dříve neodpovídající vstupní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="04ecb-114">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="04ecb-115">Následující kód ukazuje některé způsoby, ve kterém `match` použit výraz.</span><span class="sxs-lookup"><span data-stu-id="04ecb-115">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="04ecb-116">Odkaz a příklady možných vzorů, které lze použít, najdete v části [porovnávání vzorů](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="04ecb-116">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="04ecb-117">Chrání vzory</span><span class="sxs-lookup"><span data-stu-id="04ecb-117">Guards on Patterns</span></span>

<span data-ttu-id="04ecb-118">Můžete použít `when` klauzule zadejte další podmínky, které proměnnou, musí vyhovovat tak, aby odpovídaly vzor.</span><span class="sxs-lookup"><span data-stu-id="04ecb-118">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="04ecb-119">Tato klauzule odkazuje jako *ochrana*.</span><span class="sxs-lookup"><span data-stu-id="04ecb-119">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="04ecb-120">Následující výraz `when` – klíčové slovo, nebude hodnocen pouze tehdy, pokud shoda se se vzorem přidružené k této ochrana.</span><span class="sxs-lookup"><span data-stu-id="04ecb-120">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="04ecb-121">Následující příklad ukazuje použití ochranu k určení číselný rozsah pro proměnné vzor.</span><span class="sxs-lookup"><span data-stu-id="04ecb-121">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="04ecb-122">Všimněte si, že více podmínek jsou spojeny použitím logické operátory.</span><span class="sxs-lookup"><span data-stu-id="04ecb-122">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="04ecb-123">Všimněte si, že vzhledem k tomu, že hodnoty než literály nelze použít ve vzoru, musíte použít `when` klauzule, pokud máte k porovnání některé části vstup pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="04ecb-123">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="04ecb-124">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="04ecb-124">This is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

## <a name="see-also"></a><span data-ttu-id="04ecb-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="04ecb-125">See Also</span></span>

[<span data-ttu-id="04ecb-126">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="04ecb-126">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="04ecb-127">Aktivní vzorky</span><span class="sxs-lookup"><span data-stu-id="04ecb-127">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="04ecb-128">Shoda vzoru</span><span class="sxs-lookup"><span data-stu-id="04ecb-128">Pattern Matching</span></span>](pattern-matching.md)
