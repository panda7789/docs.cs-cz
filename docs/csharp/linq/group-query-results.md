---
title: Výsledky dotazu skupiny (LINQ v C#)
description: Přečtěte si, jak seskupit výsledky pomocí LINQ v C#.
ms.date: 12/01/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 577a358c31fcf5346e7aab7a2e2b6be10fd1beff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688459"
---
# <a name="group-query-results"></a><span data-ttu-id="fd282-103">Seskupení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="fd282-103">Group query results</span></span>

<span data-ttu-id="fd282-104">Seskupení je jednou z nejvýkonnějších funkcí LINQ.</span><span class="sxs-lookup"><span data-stu-id="fd282-104">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="fd282-105">Následující příklady ukazují, jak seskupit data různými způsoby:</span><span class="sxs-lookup"><span data-stu-id="fd282-105">The following examples show how to group data in various ways:</span></span>

- <span data-ttu-id="fd282-106">Jedinou vlastností.</span><span class="sxs-lookup"><span data-stu-id="fd282-106">By a single property.</span></span>

- <span data-ttu-id="fd282-107">Prvním písmenem vlastnosti string.</span><span class="sxs-lookup"><span data-stu-id="fd282-107">By the first letter of a string property.</span></span>

- <span data-ttu-id="fd282-108">Podle vypočítaného číselného rozsahu.</span><span class="sxs-lookup"><span data-stu-id="fd282-108">By a computed numeric range.</span></span>

- <span data-ttu-id="fd282-109">Podle logického predikátu nebo jiného výrazu.</span><span class="sxs-lookup"><span data-stu-id="fd282-109">By Boolean predicate or other expression.</span></span>

- <span data-ttu-id="fd282-110">Složeným klíčem.</span><span class="sxs-lookup"><span data-stu-id="fd282-110">By a compound key.</span></span>

<span data-ttu-id="fd282-111">Kromě toho poslední dva dotazy promítnou své výsledky do nového anonymního typu, který obsahuje pouze křestní jméno a příjmení studenta.</span><span class="sxs-lookup"><span data-stu-id="fd282-111">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="fd282-112">Další informace naleznete v [klauzuli group .](../language-reference/keywords/group-clause.md)</span><span class="sxs-lookup"><span data-stu-id="fd282-112">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="fd282-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd282-113">Example</span></span>

<span data-ttu-id="fd282-114">Všechny příklady v tomto tématu používají následující pomocné třídy a zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="fd282-114">All the examples in this topic use the following helper classes and data sources.</span></span>

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a><span data-ttu-id="fd282-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd282-115">Example</span></span>

<span data-ttu-id="fd282-116">Následující příklad ukazuje, jak seskupit zdrojové prvky pomocí jedné vlastnosti prvku jako klíče skupiny.</span><span class="sxs-lookup"><span data-stu-id="fd282-116">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="fd282-117">V tomto případě je `string`klíčem , příjmení studenta.</span><span class="sxs-lookup"><span data-stu-id="fd282-117">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="fd282-118">Je také možné použít podřetězec pro klíč.</span><span class="sxs-lookup"><span data-stu-id="fd282-118">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="fd282-119">Operace seskupení používá výchozí porovnávání rovnosti pro typ.</span><span class="sxs-lookup"><span data-stu-id="fd282-119">The grouping operation uses the default equality comparer for the type.</span></span>

<span data-ttu-id="fd282-120">Do třídy vložte následující metodu. `StudentClass`</span><span class="sxs-lookup"><span data-stu-id="fd282-120">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="fd282-121">Změňte příkaz volání `Main` v `sc.GroupBySingleProperty()`metodě na .</span><span class="sxs-lookup"><span data-stu-id="fd282-121">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a><span data-ttu-id="fd282-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd282-122">Example</span></span>

<span data-ttu-id="fd282-123">Následující příklad ukazuje, jak seskupit zdrojové prvky pomocí něčeho jiného než vlastnost objektu pro klíč skupiny.</span><span class="sxs-lookup"><span data-stu-id="fd282-123">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="fd282-124">V tomto příkladu je klíčem první písmeno příjmení studenta.</span><span class="sxs-lookup"><span data-stu-id="fd282-124">In this example, the key is the first letter of the student's last name.</span></span>

<span data-ttu-id="fd282-125">Do třídy vložte následující metodu. `StudentClass`</span><span class="sxs-lookup"><span data-stu-id="fd282-125">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="fd282-126">Změňte příkaz volání `Main` v `sc.GroupBySubstring()`metodě na .</span><span class="sxs-lookup"><span data-stu-id="fd282-126">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a><span data-ttu-id="fd282-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd282-127">Example</span></span>

<span data-ttu-id="fd282-128">Následující příklad ukazuje, jak seskupit zdrojové prvky pomocí číselné oblasti jako klíče skupiny.</span><span class="sxs-lookup"><span data-stu-id="fd282-128">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="fd282-129">Dotaz pak promítne výsledky do anonymního typu, který obsahuje pouze křestní jméno a příjmení a rozsah percentilu, do kterého student patří.</span><span class="sxs-lookup"><span data-stu-id="fd282-129">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="fd282-130">Anonymní typ se používá, protože není nutné `Student` použít celý objekt k zobrazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="fd282-130">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="fd282-131">`GetPercentile`je pomocná funkce, která vypočítá percentil na základě průměrného skóre studenta.</span><span class="sxs-lookup"><span data-stu-id="fd282-131">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="fd282-132">Metoda vrátí celé číslo mezi 0 a 10.</span><span class="sxs-lookup"><span data-stu-id="fd282-132">The method returns an integer between 0 and 10.</span></span>

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

<span data-ttu-id="fd282-133">Do třídy vložte následující metodu. `StudentClass`</span><span class="sxs-lookup"><span data-stu-id="fd282-133">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="fd282-134">Změňte příkaz volání `Main` v `sc.GroupByRange()`metodě na .</span><span class="sxs-lookup"><span data-stu-id="fd282-134">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a><span data-ttu-id="fd282-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd282-135">Example</span></span>

<span data-ttu-id="fd282-136">Následující příklad ukazuje, jak seskupit zdrojové prvky pomocí logického porovnání výrazu.</span><span class="sxs-lookup"><span data-stu-id="fd282-136">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="fd282-137">V tomto příkladu logický výraz testuje, zda je průměrné skóre zkoušky studenta větší než 75.</span><span class="sxs-lookup"><span data-stu-id="fd282-137">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="fd282-138">Stejně jako v předchozích příkladech jsou výsledky promítány do anonymního typu, protože není potřeba celý zdrojový prvek.</span><span class="sxs-lookup"><span data-stu-id="fd282-138">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="fd282-139">Všimněte si, že vlastnosti v `Key` anonymní typ stanou vlastnosti na člena a lze přistupovat podle názvu při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="fd282-139">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>

<span data-ttu-id="fd282-140">Do třídy vložte následující metodu. `StudentClass`</span><span class="sxs-lookup"><span data-stu-id="fd282-140">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="fd282-141">Změňte příkaz volání `Main` v `sc.GroupByBoolean()`metodě na .</span><span class="sxs-lookup"><span data-stu-id="fd282-141">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a><span data-ttu-id="fd282-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd282-142">Example</span></span>

<span data-ttu-id="fd282-143">Následující příklad ukazuje, jak použít anonymní typ zapouzdřit klíč, který obsahuje více hodnot.</span><span class="sxs-lookup"><span data-stu-id="fd282-143">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="fd282-144">V tomto příkladu je první hodnota klíče první písmeno příjmení studenta.</span><span class="sxs-lookup"><span data-stu-id="fd282-144">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="fd282-145">Druhá hodnota klíče je logická hodnota, která určuje, zda student skóroval nad 85 při první zkoušce.</span><span class="sxs-lookup"><span data-stu-id="fd282-145">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="fd282-146">Skupiny můžete objednat podle libovolné vlastnosti v klíči.</span><span class="sxs-lookup"><span data-stu-id="fd282-146">You can order the groups by any property in the key.</span></span>

<span data-ttu-id="fd282-147">Do třídy vložte následující metodu. `StudentClass`</span><span class="sxs-lookup"><span data-stu-id="fd282-147">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="fd282-148">Změňte příkaz volání `Main` v `sc.GroupByCompositeKey()`metodě na .</span><span class="sxs-lookup"><span data-stu-id="fd282-148">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a><span data-ttu-id="fd282-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd282-149">See also</span></span>

- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.IGrouping%602>
- [<span data-ttu-id="fd282-150">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="fd282-150">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="fd282-151">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="fd282-151">group clause</span></span>](../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="fd282-152">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="fd282-152">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="fd282-153">Provedení poddotazu na operaci seskupení</span><span class="sxs-lookup"><span data-stu-id="fd282-153">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="fd282-154">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="fd282-154">Create a Nested Group</span></span>](create-a-nested-group.md)
- [<span data-ttu-id="fd282-155">Seskupování dat</span><span class="sxs-lookup"><span data-stu-id="fd282-155">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
