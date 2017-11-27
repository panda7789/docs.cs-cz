---
title: "Výsledky dotazu skupiny"
description: "Jak výsledky skupiny."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: ca68cf96a2c27bbd1999d5445c14fc93e8e2566c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="group-query-results"></a><span data-ttu-id="d69fc-104">Výsledky dotazu skupiny</span><span class="sxs-lookup"><span data-stu-id="d69fc-104">Group query results</span></span>

<span data-ttu-id="d69fc-105">Seskupení je jedním z nejúčinnějších možnosti LINQ.</span><span class="sxs-lookup"><span data-stu-id="d69fc-105">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="d69fc-106">Následující příklady ukazují, jak k seskupení dat různými způsoby:</span><span class="sxs-lookup"><span data-stu-id="d69fc-106">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="d69fc-107">Pomocí vlastnosti jediné.</span><span class="sxs-lookup"><span data-stu-id="d69fc-107">By a single property.</span></span>  
  
-   <span data-ttu-id="d69fc-108">První písmeno ve vlastnosti string.</span><span class="sxs-lookup"><span data-stu-id="d69fc-108">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="d69fc-109">Podle počítaný číselný rozsah.</span><span class="sxs-lookup"><span data-stu-id="d69fc-109">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="d69fc-110">Logická hodnota predikátu nebo jiných výraz.</span><span class="sxs-lookup"><span data-stu-id="d69fc-110">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="d69fc-111">Pomocí složeného klíče.</span><span class="sxs-lookup"><span data-stu-id="d69fc-111">By a compound key.</span></span>  
  
 <span data-ttu-id="d69fc-112">Kromě toho poslední dva dotazy projektu jejich výsledky do nové anonymní typ, který obsahuje pouze student je první a poslední název.</span><span class="sxs-lookup"><span data-stu-id="d69fc-112">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="d69fc-113">Další informace najdete v tématu [group – klauzule](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d69fc-113">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d69fc-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d69fc-114">Example</span></span>  
 <span data-ttu-id="d69fc-115">V příkladech v tomto tématu použijte následující pomocné rutiny třídy a datové zdroje.</span><span class="sxs-lookup"><span data-stu-id="d69fc-115">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="d69fc-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="d69fc-116">Example</span></span>  
 <span data-ttu-id="d69fc-117">Následující příklad ukazuje, jak chcete seskupit zdrojové elementy pomocí vlastnosti jediné elementu jako klíč skupiny.</span><span class="sxs-lookup"><span data-stu-id="d69fc-117">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="d69fc-118">V takovém případě je klíč `string`, Studentova příjmení.</span><span class="sxs-lookup"><span data-stu-id="d69fc-118">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="d69fc-119">Je také možné použít dílčí řetězec pro klíč.</span><span class="sxs-lookup"><span data-stu-id="d69fc-119">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="d69fc-120">Operace seskupení se pro typ používá výchozí procedury rovnosti.</span><span class="sxs-lookup"><span data-stu-id="d69fc-120">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="d69fc-121">Vložte následující metodu do `StudentClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="d69fc-121">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="d69fc-122">Změňte volání příkaz v `Main` metodu `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="d69fc-122">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="d69fc-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="d69fc-123">Example</span></span>  
 <span data-ttu-id="d69fc-124">Následující příklad ukazuje, jak chcete seskupit zdrojové elementy něco jiného než vlastnost objektu pomocí pro klíč skupiny.</span><span class="sxs-lookup"><span data-stu-id="d69fc-124">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="d69fc-125">V tomto příkladu je klíč první písmeno Studentova příjmení.</span><span class="sxs-lookup"><span data-stu-id="d69fc-125">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="d69fc-126">Vložte následující metodu do `StudentClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="d69fc-126">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="d69fc-127">Změňte volání příkaz v `Main` metodu `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="d69fc-127">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="d69fc-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="d69fc-128">Example</span></span>  
 <span data-ttu-id="d69fc-129">Následující příklad ukazuje, jak chcete seskupit zdrojové elementy pomocí číselný rozsah jako klíč skupiny.</span><span class="sxs-lookup"><span data-stu-id="d69fc-129">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="d69fc-130">Výsledky dotazu pak projekty do anonymní typ, který obsahuje pouze první a poslední název a percentilu rozsahu, ke kterému patří student.</span><span class="sxs-lookup"><span data-stu-id="d69fc-130">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="d69fc-131">Anonymní typ se používá, protože není nutné k použití kompletní `Student` objekt, který chcete zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="d69fc-131">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="d69fc-132">`GetPercentile`pomocné funkce pro výpočet percentilu podle Studentova průměrné skóre.</span><span class="sxs-lookup"><span data-stu-id="d69fc-132">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="d69fc-133">Metoda vrátí celé číslo mezi 0 a 10.</span><span class="sxs-lookup"><span data-stu-id="d69fc-133">The method returns an integer between 0 and 10.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 <span data-ttu-id="d69fc-134">Vložte následující metodu do `StudentClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="d69fc-134">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="d69fc-135">Změňte volání příkaz v `Main` metodu `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="d69fc-135">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="d69fc-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="d69fc-136">Example</span></span>  
 <span data-ttu-id="d69fc-137">Následující příklad ukazuje, jak chcete seskupit pomocí výrazu Boolean porovnání zdrojové elementy.</span><span class="sxs-lookup"><span data-stu-id="d69fc-137">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="d69fc-138">V tomto příkladu logický výraz ověřuje, zda je větší než 75 Studentova průměrná zkoušku skóre.</span><span class="sxs-lookup"><span data-stu-id="d69fc-138">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="d69fc-139">Jako v předchozích příkladech jsou výsledky promítnout do anonymního typu, protože není potřeba kompletní zdrojový element.</span><span class="sxs-lookup"><span data-stu-id="d69fc-139">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="d69fc-140">Všimněte si, že vlastnosti v anonymního typu stát vlastnosti `Key` člen a je přístupný pomocí názvu, když je proveden dotaz.</span><span class="sxs-lookup"><span data-stu-id="d69fc-140">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="d69fc-141">Vložte následující metodu do `StudentClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="d69fc-141">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="d69fc-142">Změňte volání příkaz v `Main` metodu `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="d69fc-142">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="d69fc-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="d69fc-143">Example</span></span>  
 <span data-ttu-id="d69fc-144">Následující příklad ukazuje, jak použít anonymní typ k zapouzdření klíč, který obsahuje více hodnot.</span><span class="sxs-lookup"><span data-stu-id="d69fc-144">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="d69fc-145">V tomto příkladu je první hodnota klíče první písmeno Studentova příjmení.</span><span class="sxs-lookup"><span data-stu-id="d69fc-145">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="d69fc-146">Druhá hodnota klíče je logická hodnota, která určuje, zda student skóre pro magnitudu více než 85 na první zkoušku.</span><span class="sxs-lookup"><span data-stu-id="d69fc-146">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="d69fc-147">Skupiny můžete uspořádat podle libovolných vlastností v klíči.</span><span class="sxs-lookup"><span data-stu-id="d69fc-147">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="d69fc-148">Vložte následující metodu do `StudentClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="d69fc-148">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="d69fc-149">Změňte volání příkaz v `Main` metodu `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="d69fc-149">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d69fc-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="d69fc-150">See also</span></span>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [<span data-ttu-id="d69fc-151">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="d69fc-151">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="d69fc-152">Group – klauzule</span><span class="sxs-lookup"><span data-stu-id="d69fc-152">group clause</span></span>](../language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="d69fc-153">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="d69fc-153">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="d69fc-154">Provádění poddotazů na skupinách</span><span class="sxs-lookup"><span data-stu-id="d69fc-154">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)  
 [<span data-ttu-id="d69fc-155">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="d69fc-155">Create a Nested Group</span></span>](create-a-nested-group.md)  
 [<span data-ttu-id="d69fc-156">Seskupování dat</span><span class="sxs-lookup"><span data-stu-id="d69fc-156">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
