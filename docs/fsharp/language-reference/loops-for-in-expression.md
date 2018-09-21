---
title: 'Smyčky: Výraz for...in (F#)'
description: 'V tématu Jak F # for... ve výrazu konstrukce opakování ve smyčce se používá k iteraci přes odpovídá vzoru v vyčíslitelné kolekce.'
ms.date: 05/16/2016
ms.openlocfilehash: c4fba1f1dea3993cafa2e37ad0f32d9fb2eed85a
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540382"
---
# <a name="loops-forin-expression"></a><span data-ttu-id="4311e-103">Smyčky: Výraz for...in</span><span class="sxs-lookup"><span data-stu-id="4311e-103">Loops: for...in Expression</span></span>

<span data-ttu-id="4311e-104">Tato uvozuje konstruktor cyklu se používá k iteraci přes odpovídá vzoru v vyčíslitelné kolekce jako výraz rozsahu, pořadí, seznam, pole nebo jiné konstrukce, která podporuje výčtu.</span><span class="sxs-lookup"><span data-stu-id="4311e-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>

## <a name="syntax"></a><span data-ttu-id="4311e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4311e-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="4311e-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4311e-106">Remarks</span></span>

<span data-ttu-id="4311e-107">`for...in` Výrazu je možné porovnat s `for each` příkaz v jiných jazycích rozhraní .NET protože se používá k vytvoření smyčky přes hodnoty v vyčíslitelné kolekce.</span><span class="sxs-lookup"><span data-stu-id="4311e-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="4311e-108">Ale `for...in` také podporuje porovnávání vzorů přes kolekce místo pouze iterace v celé kolekci.</span><span class="sxs-lookup"><span data-stu-id="4311e-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="4311e-109">Vyčíslitelná výraz se dá nastavit jako vyčíslitelné kolekce nebo pomocí `..` operátor jako oblast celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="4311e-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="4311e-110">Vyčíslitelné kolekce zahrnout seznamy, pořadí, pole, sady, mapy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="4311e-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="4311e-111">Libovolný typ, který implementuje `System.Collections.IEnumerable` lze použít.</span><span class="sxs-lookup"><span data-stu-id="4311e-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="4311e-112">Když vyjádřit rozsahu pomocí `..` operátoru, můžete použít následující syntaxi.</span><span class="sxs-lookup"><span data-stu-id="4311e-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="4311e-113">*Spustit* ...</span><span class="sxs-lookup"><span data-stu-id="4311e-113">*start* ..</span></span> <span data-ttu-id="4311e-114">*Dokončit*</span><span class="sxs-lookup"><span data-stu-id="4311e-114">*finish*</span></span>

<span data-ttu-id="4311e-115">Můžete také použít verzi, která zahrnuje přírůstek volána *přeskočit*, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4311e-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="4311e-116">*Spustit* ...</span><span class="sxs-lookup"><span data-stu-id="4311e-116">*start* ..</span></span> <span data-ttu-id="4311e-117">*Přeskočit* ...</span><span class="sxs-lookup"><span data-stu-id="4311e-117">*skip* ..</span></span> <span data-ttu-id="4311e-118">*Dokončit*</span><span class="sxs-lookup"><span data-stu-id="4311e-118">*finish*</span></span>

<span data-ttu-id="4311e-119">Při použití integrální rozsahy a jednoduchý čítač proměnné jako vzor je obvyklé chování se zvýší o 1 při každé iteraci proměnná čítače, ale pokud rozsahu obsahuje hodnotu, přeskočit, hodnota čítače se zvýší místo toho podle hodnoty přeskočit.</span><span class="sxs-lookup"><span data-stu-id="4311e-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="4311e-120">Hodnoty odpovídající vzoru můžete použít také v těle výrazu.</span><span class="sxs-lookup"><span data-stu-id="4311e-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="4311e-121">Následující příklady kódu znázorňují použití `for...in` výrazu.</span><span class="sxs-lookup"><span data-stu-id="4311e-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="4311e-122">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="4311e-122">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="4311e-123">Následující příklad ukazuje, jak k vytvoření smyčky přes sekvenci a způsob použití vzoru n-tice místo jednoduchá proměnná.</span><span class="sxs-lookup"><span data-stu-id="4311e-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="4311e-124">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="4311e-124">The output is as follows.</span></span>

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

<span data-ttu-id="4311e-125">Následující příklad ukazuje, jak ve smyčce rozsah jednoduché celých čísel.</span><span class="sxs-lookup"><span data-stu-id="4311e-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="4311e-126">Výstup function1 vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="4311e-126">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="4311e-127">Následující příklad ukazuje, jak ve smyčce rozsah s přeskočením 2, který obsahuje každý jiného elementu rozsahu.</span><span class="sxs-lookup"><span data-stu-id="4311e-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="4311e-128">Výstup `function2` vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="4311e-128">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="4311e-129">Následující příklad ukazuje, jak použít rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="4311e-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="4311e-130">Výstup `function3` vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="4311e-130">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="4311e-131">Následující příklad ukazuje, jak použít zápornou přeskočit hodnotu pro reverzní iteraci.</span><span class="sxs-lookup"><span data-stu-id="4311e-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="4311e-132">Výstup `function4` vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="4311e-132">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="4311e-133">Na začátek a konec rozsahu může být také výrazy, jako je například funkce, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4311e-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="4311e-134">Výstup `function5` tento vstup je následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="4311e-134">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="4311e-135">Následující příklad ukazuje použití zástupných znaků (\_) Pokud prvek není nutná ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="4311e-135">The next example shows the use of a wildcard character (\_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="4311e-136">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="4311e-136">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="4311e-137">`Note` Můžete použít `for...in` ve výrazech pořadí a jiných výrazech výpočtu se v takovém případě přizpůsobenou verzi `for...in` výraz je použit.</span><span class="sxs-lookup"><span data-stu-id="4311e-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="4311e-138">Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výrazech výpočtu](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4311e-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4311e-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4311e-139">See also</span></span>

- [<span data-ttu-id="4311e-140">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="4311e-140">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4311e-141">Smyčky: `for...to` výraz</span><span class="sxs-lookup"><span data-stu-id="4311e-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
- [<span data-ttu-id="4311e-142">Smyčky: `while...do` výraz</span><span class="sxs-lookup"><span data-stu-id="4311e-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
