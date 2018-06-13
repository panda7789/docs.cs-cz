---
title: 'Smyčky: Výraz for...in (F#)'
description: 'V tématu Jak F # for... ve výrazu opakování ve smyčce konstrukce je použít k iteraci nad na odpovídá vzoru v kolekci vyčíslitelná.'
ms.date: 05/16/2016
ms.openlocfilehash: 926f0a9940021b3dc0deefc12ea158c35975e949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564071"
---
# <a name="loops-forin-expression"></a><span data-ttu-id="26ef0-103">Smyčky: Výraz for...in</span><span class="sxs-lookup"><span data-stu-id="26ef0-103">Loops: for...in Expression</span></span>

<span data-ttu-id="26ef0-104">Tato opakování konstrukce se používá k iteraci nad na odpovídá vzoru v kolekci vyčíslitelná například výraz rozsahu, pořadí, seznam, pole nebo jiné konstrukce, která podporuje – výčet.</span><span class="sxs-lookup"><span data-stu-id="26ef0-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>


## <a name="syntax"></a><span data-ttu-id="26ef0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26ef0-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="26ef0-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26ef0-106">Remarks</span></span>
<span data-ttu-id="26ef0-107">`for...in` Výraz může být ve srovnání s `for each` příkaz v jiných jazycích .NET protože se používá k vytvoření smyčky přes hodnoty v kolekci vyčíslitelná.</span><span class="sxs-lookup"><span data-stu-id="26ef0-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="26ef0-108">Ale `for...in` také podporuje vzor odpovídající nad shromažďováním místo jenom iteraci přes celou kolekci.</span><span class="sxs-lookup"><span data-stu-id="26ef0-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="26ef0-109">Vyčíslitelná výraz lze zadat jako kolekci výčtové nebo pomocí `..` operátor jako rozsah celočíselných typu.</span><span class="sxs-lookup"><span data-stu-id="26ef0-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="26ef0-110">Vyčíslitelná kolekce zahrnují seznamy, pořadí, pole, sady, mapy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="26ef0-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="26ef0-111">Žádný typ, který implementuje `System.Collections.IEnumerable` lze použít.</span><span class="sxs-lookup"><span data-stu-id="26ef0-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="26ef0-112">Když express rozsah pomocí `..` operátor, můžete použít následující syntaxi.</span><span class="sxs-lookup"><span data-stu-id="26ef0-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="26ef0-113">*Spustit* ...</span><span class="sxs-lookup"><span data-stu-id="26ef0-113">*start* ..</span></span> <span data-ttu-id="26ef0-114">*Dokončit*</span><span class="sxs-lookup"><span data-stu-id="26ef0-114">*finish*</span></span>

<span data-ttu-id="26ef0-115">Můžete také na verzi, která zahrnuje přírůstek volat *přeskočit*, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="26ef0-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="26ef0-116">*Spustit* ...</span><span class="sxs-lookup"><span data-stu-id="26ef0-116">*start* ..</span></span> <span data-ttu-id="26ef0-117">*Přeskočit* ...</span><span class="sxs-lookup"><span data-stu-id="26ef0-117">*skip* ..</span></span> <span data-ttu-id="26ef0-118">*Dokončit*</span><span class="sxs-lookup"><span data-stu-id="26ef0-118">*finish*</span></span>

<span data-ttu-id="26ef0-119">Použijete-li jako vzor integrální rozsahy a jednoduchý čítač proměnnou, je typické chování se zvýší o 1 na každé iteraci proměnnou čítače, ale pokud rozsahu obsahuje hodnotu přeskočit, hodnota čítače se zvýší místo hodnotou přeskočit.</span><span class="sxs-lookup"><span data-stu-id="26ef0-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="26ef0-120">Hodnoty shodná ve vzoru mohou sloužit také ve výrazu textu.</span><span class="sxs-lookup"><span data-stu-id="26ef0-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="26ef0-121">Následující příklady kódu ilustrují použití `for...in` výraz.</span><span class="sxs-lookup"><span data-stu-id="26ef0-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="26ef0-122">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="26ef0-122">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="26ef0-123">Následující příklad ukazuje, jak smyčku sekvenci a způsob použití vzoru řazené kolekce členů místo jednoduché proměnné.</span><span class="sxs-lookup"><span data-stu-id="26ef0-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="26ef0-124">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="26ef0-124">The output is as follows.</span></span>

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

<span data-ttu-id="26ef0-125">Následující příklad ukazuje, jak smyčku rozsah jednoduché celé číslo.</span><span class="sxs-lookup"><span data-stu-id="26ef0-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="26ef0-126">Výstup function1 je následující.</span><span class="sxs-lookup"><span data-stu-id="26ef0-126">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="26ef0-127">Následující příklad ukazuje, jak na rozsah s přeskočením 2, která zahrnuje každý element, rozsahu opakovací smyčku.</span><span class="sxs-lookup"><span data-stu-id="26ef0-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="26ef0-128">Výstup `function2` je následující.</span><span class="sxs-lookup"><span data-stu-id="26ef0-128">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="26ef0-129">Následující příklad ukazuje, jak používat rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="26ef0-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="26ef0-130">Výstup `function3` je následující.</span><span class="sxs-lookup"><span data-stu-id="26ef0-130">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="26ef0-131">Následující příklad ukazuje, jak chcete použít hodnotu s záporné přeskočit pro zpětné iterací.</span><span class="sxs-lookup"><span data-stu-id="26ef0-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="26ef0-132">Výstup `function4` je následující.</span><span class="sxs-lookup"><span data-stu-id="26ef0-132">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="26ef0-133">Na začátek a konec rozsahu může být také výrazy, jako je například funkce, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="26ef0-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="26ef0-134">Výstup `function5` s tímto vstupem je následující.</span><span class="sxs-lookup"><span data-stu-id="26ef0-134">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="26ef0-135">Další příklad ukazuje použití zástupný znak (_), když element není potřeba ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="26ef0-135">The next example shows the use of a wildcard character (_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="26ef0-136">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="26ef0-136">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="26ef0-137">`Note` Můžete použít `for...in` v pořadí výrazy a další výpočetní výrazy v takovém případě přizpůsobená verze `for...in` použit výraz.</span><span class="sxs-lookup"><span data-stu-id="26ef0-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="26ef0-138">Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výpočetní výrazy](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="26ef0-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="26ef0-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="26ef0-139">See Also</span></span>
[<span data-ttu-id="26ef0-140">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="26ef0-140">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="26ef0-141">Smyčky: `for...to` výraz</span><span class="sxs-lookup"><span data-stu-id="26ef0-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)

[<span data-ttu-id="26ef0-142">Smyčky: `while...do` výraz</span><span class="sxs-lookup"><span data-stu-id="26ef0-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
