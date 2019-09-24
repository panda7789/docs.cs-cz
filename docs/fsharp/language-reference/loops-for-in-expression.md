---
title: 'Smyčky: Výraz for...in'
description: Podívejte se, F# jak pro... v konstruktoru smyčky výrazů se používá k iteraci přes shody vzoru ve vyčíslitelné kolekci.
ms.date: 05/16/2016
ms.openlocfilehash: 5a2ca59ca4199ece5d78010ff780e86ae2b25181
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216456"
---
# <a name="loops-forin-expression"></a><span data-ttu-id="1e42d-103">Smyčky: Výraz for...in</span><span class="sxs-lookup"><span data-stu-id="1e42d-103">Loops: for...in Expression</span></span>

<span data-ttu-id="1e42d-104">Tato konstrukce smyčky se používá k iteraci přes shody vzoru ve vyčíslitelné kolekci, jako je například výraz rozsahu, sekvence, seznam, pole nebo jiná konstrukce, která podporuje výčet.</span><span class="sxs-lookup"><span data-stu-id="1e42d-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>

## <a name="syntax"></a><span data-ttu-id="1e42d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e42d-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="1e42d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e42d-106">Remarks</span></span>

<span data-ttu-id="1e42d-107">Výraz může být porovnán `for each` s příkazem v jiných jazycích .NET, protože se používá k překonání hodnot ve vyčíslitelné kolekci. `for...in`</span><span class="sxs-lookup"><span data-stu-id="1e42d-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="1e42d-108">Nicméně podporuje `for...in` také porovnávání vzorů přes kolekci namísto pouze iterace v celé kolekci.</span><span class="sxs-lookup"><span data-stu-id="1e42d-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="1e42d-109">Vyčíslitelné výrazy lze zadat jako vyčíslitelné kolekce nebo pomocí `..` operátoru jako rozsahu pro celočíselný typ.</span><span class="sxs-lookup"><span data-stu-id="1e42d-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="1e42d-110">Vyčíslitelné kolekce obsahují seznamy, sekvence, pole, sady, mapy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="1e42d-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="1e42d-111">Lze použít jakýkoli typ `System.Collections.IEnumerable` , který implementuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="1e42d-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="1e42d-112">Při vyjádření rozsahu pomocí `..` operátoru můžete použít následující syntaxi.</span><span class="sxs-lookup"><span data-stu-id="1e42d-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="1e42d-113">*Spustit* ...</span><span class="sxs-lookup"><span data-stu-id="1e42d-113">*start* ..</span></span> <span data-ttu-id="1e42d-114">*skončit*</span><span class="sxs-lookup"><span data-stu-id="1e42d-114">*finish*</span></span>

<span data-ttu-id="1e42d-115">Můžete také použít verzi, která obsahuje přírůstek s názvem *Skip*, jak je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1e42d-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="1e42d-116">*Spustit* ...</span><span class="sxs-lookup"><span data-stu-id="1e42d-116">*start* ..</span></span> <span data-ttu-id="1e42d-117">*Přeskočit* ...</span><span class="sxs-lookup"><span data-stu-id="1e42d-117">*skip* ..</span></span> <span data-ttu-id="1e42d-118">*skončit*</span><span class="sxs-lookup"><span data-stu-id="1e42d-118">*finish*</span></span>

<span data-ttu-id="1e42d-119">Když použijete celočíselné rozsahy a jednoduchou proměnnou čítače jako vzor, typické chování je zvýšit proměnnou čítače o 1 u každé iterace, ale pokud rozsah obsahuje hodnotu Skip, čítač se zvýší o hodnotu přeskočení.</span><span class="sxs-lookup"><span data-stu-id="1e42d-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="1e42d-120">Hodnoty odpovídající vzoru lze také použít ve výrazu body.</span><span class="sxs-lookup"><span data-stu-id="1e42d-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="1e42d-121">Následující příklady kódu ilustrují použití `for...in` výrazu.</span><span class="sxs-lookup"><span data-stu-id="1e42d-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="1e42d-122">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="1e42d-122">The output is as follows.</span></span>

```console
1
5
100
450
788
```

<span data-ttu-id="1e42d-123">Následující příklad ukazuje, jak vytvořit smyčku přes sekvenci a jak použít vzor řazené kolekce členů namísto jednoduché proměnné.</span><span class="sxs-lookup"><span data-stu-id="1e42d-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="1e42d-124">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="1e42d-124">The output is as follows.</span></span>

```console
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

<span data-ttu-id="1e42d-125">Následující příklad ukazuje, jak vytvořit smyčku přes jednoduchý celočíselný rozsah.</span><span class="sxs-lookup"><span data-stu-id="1e42d-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="1e42d-126">Výstup Function1 je následující.</span><span class="sxs-lookup"><span data-stu-id="1e42d-126">The output of function1 is as follows.</span></span>

```console
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="1e42d-127">Následující příklad ukazuje, jak vytvořit smyčku v rámci rozsahu s vynecháním 2, který obsahuje všechny ostatní prvky rozsahu.</span><span class="sxs-lookup"><span data-stu-id="1e42d-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="1e42d-128">Výstup `function2` je následující:</span><span class="sxs-lookup"><span data-stu-id="1e42d-128">The output of `function2` is as follows.</span></span>

```console
1 3 5 7 9
```

<span data-ttu-id="1e42d-129">Následující příklad ukazuje, jak použít rozsah znaků.</span><span class="sxs-lookup"><span data-stu-id="1e42d-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="1e42d-130">Výstup `function3` je následující:</span><span class="sxs-lookup"><span data-stu-id="1e42d-130">The output of `function3` is as follows.</span></span>

```console
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="1e42d-131">Následující příklad ukazuje, jak použít pro reverzní iteraci zápornou hodnotu Skip.</span><span class="sxs-lookup"><span data-stu-id="1e42d-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="1e42d-132">Výstup `function4` je následující:</span><span class="sxs-lookup"><span data-stu-id="1e42d-132">The output of `function4` is as follows.</span></span>

```console
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="1e42d-133">Začátek a konec rozsahu může být také výrazy, například funkce, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1e42d-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="1e42d-134">Výstup `function5` tohoto vstupu je následující.</span><span class="sxs-lookup"><span data-stu-id="1e42d-134">The output of `function5` with this input is as follows.</span></span>

```console
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="1e42d-135">Následující příklad ukazuje použití zástupného znaku (\_), pokud element není ve smyčce potřeba.</span><span class="sxs-lookup"><span data-stu-id="1e42d-135">The next example shows the use of a wildcard character (\_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="1e42d-136">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="1e42d-136">The output is as follows.</span></span>

```console
Number of elements in list1: 5
```

<span data-ttu-id="1e42d-137">`Note`Můžete použít `for...in` ve výrazech pořadí a dalších výrazech výpočtu. v takovém případě se používá přizpůsobená verze `for...in` výrazu.</span><span class="sxs-lookup"><span data-stu-id="1e42d-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="1e42d-138">Další informace najdete v tématu [sekvence](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md)a [výpočetní výrazy](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1e42d-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e42d-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e42d-139">See also</span></span>

- [<span data-ttu-id="1e42d-140">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="1e42d-140">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1e42d-141">Smyčky `for...to`Vyjádření</span><span class="sxs-lookup"><span data-stu-id="1e42d-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
- [<span data-ttu-id="1e42d-142">Smyčky `while...do`Vyjádření</span><span class="sxs-lookup"><span data-stu-id="1e42d-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
