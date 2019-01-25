---
title: Seskupení výsledků dotazu (LINQ v JAZYKU C#)
description: Zjistěte, jak seskupit výsledky pomocí jazyka LINQ v jazyce C#.
ms.date: 12/01/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 577a358c31fcf5346e7aab7a2e2b6be10fd1beff
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857850"
---
# <a name="group-query-results"></a><span data-ttu-id="4b058-103">Seskupení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="4b058-103">Group query results</span></span>

<span data-ttu-id="4b058-104">Seskupení je jedním z nejúčinnějších funkcí LINQ.</span><span class="sxs-lookup"><span data-stu-id="4b058-104">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="4b058-105">Následující příklady ukazují, jak k seskupení dat různými způsoby:</span><span class="sxs-lookup"><span data-stu-id="4b058-105">The following examples show how to group data in various ways:</span></span>

- <span data-ttu-id="4b058-106">Podle jedné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4b058-106">By a single property.</span></span>

- <span data-ttu-id="4b058-107">Podle první písmeno vlastnosti typu string.</span><span class="sxs-lookup"><span data-stu-id="4b058-107">By the first letter of a string property.</span></span>

- <span data-ttu-id="4b058-108">Pomocí počítaného číselného rozsahu.</span><span class="sxs-lookup"><span data-stu-id="4b058-108">By a computed numeric range.</span></span>

- <span data-ttu-id="4b058-109">Podle typu Boolean predikát nebo jiný výraz.</span><span class="sxs-lookup"><span data-stu-id="4b058-109">By Boolean predicate or other expression.</span></span>

- <span data-ttu-id="4b058-110">Pomocí složeného klíče.</span><span class="sxs-lookup"><span data-stu-id="4b058-110">By a compound key.</span></span>

<span data-ttu-id="4b058-111">Kromě toho poslední dva dotazy projektu jejich výsledky do nové anonymní typ, který obsahuje pouze studenta je první a poslední název.</span><span class="sxs-lookup"><span data-stu-id="4b058-111">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="4b058-112">Další informace najdete v tématu [group – klauzule](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4b058-112">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="4b058-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b058-113">Example</span></span>

<span data-ttu-id="4b058-114">Všechny příklady v tomto tématu použijte následující pomocné rutiny třídy a data zdrojů.</span><span class="sxs-lookup"><span data-stu-id="4b058-114">All the examples in this topic use the following helper classes and data sources.</span></span>

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a><span data-ttu-id="4b058-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b058-115">Example</span></span>

<span data-ttu-id="4b058-116">Následující příklad ukazuje, jak seskupit podle jedné vlastnosti elementu klíč skupiny zdrojové elementy.</span><span class="sxs-lookup"><span data-stu-id="4b058-116">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="4b058-117">V tomto případě je klíč `string`, student získal příjmení.</span><span class="sxs-lookup"><span data-stu-id="4b058-117">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="4b058-118">Je také možné použít dílčí řetězec klíče.</span><span class="sxs-lookup"><span data-stu-id="4b058-118">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="4b058-119">Operaci seskupení pomocí výchozí procedury rovnosti pro typ.</span><span class="sxs-lookup"><span data-stu-id="4b058-119">The grouping operation uses the default equality comparer for the type.</span></span>

<span data-ttu-id="4b058-120">Vložte následující metodu do `StudentClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="4b058-120">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="4b058-121">Změňte volání příkazu v `Main` metodu `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="4b058-121">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a><span data-ttu-id="4b058-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b058-122">Example</span></span>

<span data-ttu-id="4b058-123">Následující příklad ukazuje, jak seskupit zdrojové prvky pomocí jinou hodnotu než vlastnost v objektu pro klíč skupiny.</span><span class="sxs-lookup"><span data-stu-id="4b058-123">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="4b058-124">V tomto příkladu je klíč první písmeno student získal příjmení.</span><span class="sxs-lookup"><span data-stu-id="4b058-124">In this example, the key is the first letter of the student's last name.</span></span>

<span data-ttu-id="4b058-125">Vložte následující metodu do `StudentClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="4b058-125">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="4b058-126">Změňte volání příkazu v `Main` metodu `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="4b058-126">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a><span data-ttu-id="4b058-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b058-127">Example</span></span>

<span data-ttu-id="4b058-128">Následující příklad ukazuje, jak seskupit zdroje prvky pomocí číselného rozsahu jako klíč skupiny.</span><span class="sxs-lookup"><span data-stu-id="4b058-128">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="4b058-129">Výsledky dotazu pak projekty do anonymního typu, který obsahuje pouze první a poslední název a percentil rozsahu, do které patří studenta.</span><span class="sxs-lookup"><span data-stu-id="4b058-129">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="4b058-130">Anonymní typ se používá, protože to není nutné použít úplnou `Student` zobrazíte výsledky.</span><span class="sxs-lookup"><span data-stu-id="4b058-130">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="4b058-131">`GetPercentile` pomocná funkce, který vypočítá percentil podle skóre průměrné známky studenta.</span><span class="sxs-lookup"><span data-stu-id="4b058-131">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="4b058-132">Metoda vrátí celé číslo mezi 0 a 10.</span><span class="sxs-lookup"><span data-stu-id="4b058-132">The method returns an integer between 0 and 10.</span></span>

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

<span data-ttu-id="4b058-133">Vložte následující metodu do `StudentClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="4b058-133">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="4b058-134">Změňte volání příkazu v `Main` metodu `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="4b058-134">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a><span data-ttu-id="4b058-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b058-135">Example</span></span>

<span data-ttu-id="4b058-136">Následující příklad ukazuje, jak pomocí výrazu porovnání logická seskupení zdrojové elementy.</span><span class="sxs-lookup"><span data-stu-id="4b058-136">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="4b058-137">V tomto příkladu logický výraz testuje, jestli student získal zkoušku průměrné skóre je větší než 75.</span><span class="sxs-lookup"><span data-stu-id="4b058-137">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="4b058-138">Stejně jako v předchozích příkladech výsledky se promítnou do anonymního typu vzhledem k tomu, že úplný zdrojový element není potřeba.</span><span class="sxs-lookup"><span data-stu-id="4b058-138">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="4b058-139">Všimněte si, že vlastnosti v anonymním typu stanou vlastnosti na `Key` člena a je přístupný podle názvu, při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="4b058-139">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>

<span data-ttu-id="4b058-140">Vložte následující metodu do `StudentClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="4b058-140">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="4b058-141">Změňte volání příkazu v `Main` metodu `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="4b058-141">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a><span data-ttu-id="4b058-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b058-142">Example</span></span>

<span data-ttu-id="4b058-143">Následující příklad ukazuje, jak použít anonymní typ k zapouzdření klíč, který obsahuje více hodnot.</span><span class="sxs-lookup"><span data-stu-id="4b058-143">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="4b058-144">V tomto příkladu první hodnota klíče je první písmeno student získal příjmení.</span><span class="sxs-lookup"><span data-stu-id="4b058-144">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="4b058-145">Druhá hodnota klíče je logická hodnota, která určuje, jestli student zohlednit více než 85 na první zkoušku.</span><span class="sxs-lookup"><span data-stu-id="4b058-145">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="4b058-146">Seřazení skupin podle libovolné vlastnosti v klíči.</span><span class="sxs-lookup"><span data-stu-id="4b058-146">You can order the groups by any property in the key.</span></span>

<span data-ttu-id="4b058-147">Vložte následující metodu do `StudentClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="4b058-147">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="4b058-148">Změňte volání příkazu v `Main` metodu `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="4b058-148">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a><span data-ttu-id="4b058-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b058-149">See also</span></span>

- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.IGrouping%602>
- [<span data-ttu-id="4b058-150">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="4b058-150">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="4b058-151">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="4b058-151">group clause</span></span>](../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="4b058-152">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="4b058-152">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="4b058-153">Provádění poddotazů na operace seskupení</span><span class="sxs-lookup"><span data-stu-id="4b058-153">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="4b058-154">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="4b058-154">Create a Nested Group</span></span>](create-a-nested-group.md)
- [<span data-ttu-id="4b058-155">Seskupování dat</span><span class="sxs-lookup"><span data-stu-id="4b058-155">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
