---
title: group – klauzule (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 157bd07f3332883f010ef26ba920dae88276051b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43744858"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="86070-102">group – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="86070-102">group clause (C# Reference)</span></span>

<span data-ttu-id="86070-103">`group` Klauzule vrátí sekvenci <xref:System.Linq.IGrouping%602> objektů, které obsahují nula nebo více položek, které odpovídají hodnotě klíče pro skupinu.</span><span class="sxs-lookup"><span data-stu-id="86070-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="86070-104">Můžete například seskupit posloupnost řetězce jsou první písmena jednotlivých řetězců.</span><span class="sxs-lookup"><span data-stu-id="86070-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="86070-105">V tomto případě první písmeno jednotky je klíč a má typ [char](char.md)a je uložen v `Key` vlastnosti každého <xref:System.Linq.IGrouping%602> objektu.</span><span class="sxs-lookup"><span data-stu-id="86070-105">In this case, the first letter is the key and has a type [char](char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="86070-106">Kompilátor odvodí typ klíče.</span><span class="sxs-lookup"><span data-stu-id="86070-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="86070-107">Můžete ukončit pomocí výrazu dotazu `group` klauzule, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="86070-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="86070-108">Pokud chcete provádět operace dalšího dotazu pro každou skupinu, můžete určit identifikátor dočasné pomocí [do](into.md) kontextové klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="86070-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="86070-109">Při použití `into`, musíte pokračovat s dotazem a nakonec ukončit některým `select` příkazu nebo jiného `group` klauzule, jak je znázorněno v následujícím výtažku:</span><span class="sxs-lookup"><span data-stu-id="86070-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="86070-110">Více kompletní příklady použití `group` a nemusíte `into` jsou k dispozici v oddíle Příklad tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="86070-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="86070-111">Vytváření výčtu výsledků dotazu skupiny</span><span class="sxs-lookup"><span data-stu-id="86070-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="86070-112">Protože <xref:System.Linq.IGrouping%602> objekty vytvářené `group` dotaz jsou v podstatě seznam seznamů, je nutné použít vnořený [foreach](foreach-in.md) smyčky pro přístup k položkám v každé skupině.</span><span class="sxs-lookup"><span data-stu-id="86070-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="86070-113">Vnější smyčka Iteruje přes skupiny klíče a vnitřní smyčku iteruje každou položku v samotnou skupinu.</span><span class="sxs-lookup"><span data-stu-id="86070-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="86070-114">Skupina může mít klíč, ale žádné elementy.</span><span class="sxs-lookup"><span data-stu-id="86070-114">A group may have a key but no elements.</span></span> <span data-ttu-id="86070-115">Tady je `foreach` smyčku, která spustí dotaz v předchozích příkladech kódu:</span><span class="sxs-lookup"><span data-stu-id="86070-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="86070-116">Typy klíčů</span><span class="sxs-lookup"><span data-stu-id="86070-116">Key types</span></span>

<span data-ttu-id="86070-117">Skupiny klíče může být libovolný typ, například řetězce, vestavěným číselným typem nebo uživatelem definované s názvem typu nebo anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="86070-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="86070-118">Seskupení podle řetězce</span><span class="sxs-lookup"><span data-stu-id="86070-118">Grouping by string</span></span>

<span data-ttu-id="86070-119">V předchozích příkladech kódu použít `char`.</span><span class="sxs-lookup"><span data-stu-id="86070-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="86070-120">Řetězec klíče může snadno nebyli určeni místo, například dokončení příjmení:</span><span class="sxs-lookup"><span data-stu-id="86070-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="86070-121">Seskupení podle bool</span><span class="sxs-lookup"><span data-stu-id="86070-121">Grouping by bool</span></span>

<span data-ttu-id="86070-122">Následující příklad ukazuje použití bool hodnotu pro klíč k rozdělení výsledky do dvou skupin.</span><span class="sxs-lookup"><span data-stu-id="86070-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="86070-123">Všimněte si, že hodnota je produkovaný dílčí výraz v `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="86070-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="86070-124">Seskupení podle číselného rozsahu</span><span class="sxs-lookup"><span data-stu-id="86070-124">Grouping by numeric range</span></span>

<span data-ttu-id="86070-125">Následující příklad používá výraz k vytvoření klíče číselné skupiny, které představují širokou percentil.</span><span class="sxs-lookup"><span data-stu-id="86070-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="86070-126">Všimněte si použití [nechat](let-clause.md) jako vhodné umístění pro uložení metodu výsledek volání, takže není nutné volat metodu dvěma časy `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="86070-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="86070-127">Všimněte si také v `group` klauzule, že aby se zabránilo výjimka "dělení nulou" kód zkontroluje, ujistěte se, že student nemá průměrem nula.</span><span class="sxs-lookup"><span data-stu-id="86070-127">Note also in the `group` clause that to avoid a "divide by zero" exception the code checks to make sure that the student doesn't have an average of zero.</span></span> <span data-ttu-id="86070-128">Další informace o tom, jak bezpečně použít metody ve výrazech dotazů najdete v tématu [postupy: zpracování výjimek ve výrazech dotazů](../../programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="86070-128">For more information about how to safely use methods in query expressions, see [How to: Handle Exceptions in Query Expressions](../../programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="86070-129">Seskupování pomocí složených klíčů</span><span class="sxs-lookup"><span data-stu-id="86070-129">Grouping by composite keys</span></span>

<span data-ttu-id="86070-130">Složený klíč používejte, pokud chcete seskupit elementy podle více než jeden klíč.</span><span class="sxs-lookup"><span data-stu-id="86070-130">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="86070-131">Vytvoříte složený klíč pomocí anonymního typu nebo typu s názvem pro uložení klíčovým prvkem.</span><span class="sxs-lookup"><span data-stu-id="86070-131">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="86070-132">V následujícím příkladu se předpokládá, že třída `Person` byla deklarována s členy s názvem `surname` a `city`.</span><span class="sxs-lookup"><span data-stu-id="86070-132">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="86070-133">`group` Klauzule způsobí, že mají být vytvořeny pro každou sadu osoby se stejným názvem poslední a stejném městě samostatnou skupinu.</span><span class="sxs-lookup"><span data-stu-id="86070-133">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="86070-134">Použijte pojmenovaného typu, pokud je proměnná dotazu musí předávat na jinou metodu.</span><span class="sxs-lookup"><span data-stu-id="86070-134">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="86070-135">Vytváření speciální třídy pomocí automaticky implementovaných vlastností pro klíče a potom přepsat <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="86070-135">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="86070-136">Můžete také použít – struktura, v takovém případě není nutné výhradně přepsat tyto metody.</span><span class="sxs-lookup"><span data-stu-id="86070-136">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="86070-137">Další informace najdete v části [postupy: implementace lehké třídy s implemented Properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) a [jak: dotazu na duplicitní soubory v adresářovém stromu](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="86070-137">For more information see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to: Query for Duplicate Files in a Directory Tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="86070-138">Ten článek obsahuje příklad kódu, který ukazuje, jak použít složený klíč s názvem typu.</span><span class="sxs-lookup"><span data-stu-id="86070-138">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="86070-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="86070-139">Example</span></span>

<span data-ttu-id="86070-140">Následující příklad ukazuje standardní vzor k řazení zdroje dat do skupin, při použití logiky bez dalšího dotazu do skupin.</span><span class="sxs-lookup"><span data-stu-id="86070-140">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="86070-141">Tomu se říká seskupení bez pokračování.</span><span class="sxs-lookup"><span data-stu-id="86070-141">This is called a grouping without a continuation.</span></span> <span data-ttu-id="86070-142">Prvky v poli řetězců jsou seskupeny podle jejich první písmeno.</span><span class="sxs-lookup"><span data-stu-id="86070-142">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="86070-143">Výsledek dotazu je <xref:System.Linq.IGrouping%602> typ, který obsahuje veřejnou `Key` vlastnost typu `char` a <xref:System.Collections.Generic.IEnumerable%601> kolekce, která obsahuje každou položku v seskupení.</span><span class="sxs-lookup"><span data-stu-id="86070-143">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="86070-144">Výsledek `group` sekvence sekvencí je klauzule.</span><span class="sxs-lookup"><span data-stu-id="86070-144">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="86070-145">Proto se pro přístup k jednotlivým prvkům v rámci jednotlivých skupin vrácené, použití vnořeného `foreach` smyčky uvnitř smyčky, která iteruje skupiny klíče, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="86070-145">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="86070-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="86070-146">Example</span></span>

<span data-ttu-id="86070-147">Tento příklad ukazuje, jak provádět další logiku na skupiny po jejich vytvoření s použitím *pokračování* s `into`.</span><span class="sxs-lookup"><span data-stu-id="86070-147">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="86070-148">Další informace najdete v tématu [do](into.md).</span><span class="sxs-lookup"><span data-stu-id="86070-148">For more information, see [into](into.md).</span></span> <span data-ttu-id="86070-149">V následujícím příkladu se dotazuje každou skupinu a vybrat jenom na ty, jejichž hodnota klíče je samohláskou.</span><span class="sxs-lookup"><span data-stu-id="86070-149">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="86070-150">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86070-150">Remarks</span></span>

<span data-ttu-id="86070-151">V době kompilace `group` klauzule jsou přeloženy do volání <xref:System.Linq.Enumerable.GroupBy%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="86070-151">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="86070-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86070-152">See also</span></span>

- <xref:System.Linq.IGrouping%602>  
- <xref:System.Linq.Enumerable.GroupBy%2A>  
- <xref:System.Linq.Enumerable.ThenBy%2A>  
- <xref:System.Linq.Enumerable.ThenByDescending%2A>  
- [<span data-ttu-id="86070-153">Klíčová slova dotazu</span><span class="sxs-lookup"><span data-stu-id="86070-153">Query Keywords</span></span>](query-keywords.md)  
- [<span data-ttu-id="86070-154">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="86070-154">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)  
- [<span data-ttu-id="86070-155">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="86070-155">Create a nested group</span></span>](../../linq/create-a-nested-group.md)  
- [<span data-ttu-id="86070-156">Seskupení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="86070-156">Group query results</span></span>](../../linq/group-query-results.md)  
- [<span data-ttu-id="86070-157">Provádění poddotazů na skupinách</span><span class="sxs-lookup"><span data-stu-id="86070-157">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)