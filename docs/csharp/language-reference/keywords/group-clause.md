---
title: klauzule skupiny - odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 75a366ec24e4e48af7e87d3372950aad8d76435b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713473"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="70a75-102">group – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="70a75-102">group clause (C# Reference)</span></span>

<span data-ttu-id="70a75-103">Klauzule `group` vrátí posloupnost <xref:System.Linq.IGrouping%602> objektů, které obsahují nula nebo více položek, které odpovídají hodnotě klíče pro skupinu.</span><span class="sxs-lookup"><span data-stu-id="70a75-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="70a75-104">Můžete například seskupit posloupnost řetězců podle prvního písmene v každém řetězci.</span><span class="sxs-lookup"><span data-stu-id="70a75-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="70a75-105">V tomto případě první písmeno je klíč a má [znak](../builtin-types/char.md) `Key` typu a <xref:System.Linq.IGrouping%602> je uložen ve vlastnosti každého objektu.</span><span class="sxs-lookup"><span data-stu-id="70a75-105">In this case, the first letter is the key and has a type [char](../builtin-types/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="70a75-106">Kompilátor odvodí typ klíče.</span><span class="sxs-lookup"><span data-stu-id="70a75-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="70a75-107">Výraz dotazu můžete ukončit klauzulí, `group` jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="70a75-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="70a75-108">Pokud chcete provést další operace dotazu v každé skupině, můžete zadat dočasný identifikátor pomocí do [kontextové](into.md) klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="70a75-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="70a75-109">Při použití `into`je nutné pokračovat v dotazu a nakonec `select` jej ukončit příkazem nebo jinou `group` klauzulí, jak je znázorněno v následujícím výňatku:</span><span class="sxs-lookup"><span data-stu-id="70a75-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="70a75-110">Podrobnější příklady použití `group` s a `into` bez jsou uvedeny v příkladu části tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="70a75-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="70a75-111">Výčet výsledků skupinového dotazu</span><span class="sxs-lookup"><span data-stu-id="70a75-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="70a75-112">Vzhledem <xref:System.Linq.IGrouping%602> k tomu, že objekty vytvořené dotazem `group` jsou v podstatě seznam seznamy, je nutné použít vnořené [foreach](foreach-in.md) smyčky pro přístup k položkám v každé skupině.</span><span class="sxs-lookup"><span data-stu-id="70a75-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="70a75-113">Vnější smyčka iterát přes klíče skupiny a vnitřní smyčka iterates přes každou položku v samotné skupině.</span><span class="sxs-lookup"><span data-stu-id="70a75-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="70a75-114">Skupina může mít klíč, ale žádné prvky.</span><span class="sxs-lookup"><span data-stu-id="70a75-114">A group may have a key but no elements.</span></span> <span data-ttu-id="70a75-115">Následuje `foreach` smyčka, která spustí dotaz v předchozích příkladech kódu:</span><span class="sxs-lookup"><span data-stu-id="70a75-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="70a75-116">Typy klíčů</span><span class="sxs-lookup"><span data-stu-id="70a75-116">Key types</span></span>

<span data-ttu-id="70a75-117">Klíče skupiny mohou být libovolný typ, například řetězec, předdefinovaný číselný typ nebo uživatelem definovaný pojmenovaný typ nebo anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="70a75-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="70a75-118">Seskupení podle řetězce</span><span class="sxs-lookup"><span data-stu-id="70a75-118">Grouping by string</span></span>

<span data-ttu-id="70a75-119">Předchozí příklady kódu `char`používaly .</span><span class="sxs-lookup"><span data-stu-id="70a75-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="70a75-120">Místo toho mohl být snadno zadán řetězec, například úplný příjmení:</span><span class="sxs-lookup"><span data-stu-id="70a75-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="70a75-121">Seskupení podle bool</span><span class="sxs-lookup"><span data-stu-id="70a75-121">Grouping by bool</span></span>

<span data-ttu-id="70a75-122">Následující příklad ukazuje použití bool hodnotu klíče rozdělit výsledky do dvou skupin.</span><span class="sxs-lookup"><span data-stu-id="70a75-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="70a75-123">Všimněte si, že hodnota je vytvořena `group` podvýraz v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="70a75-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="70a75-124">Seskupení podle číselného rozsahu</span><span class="sxs-lookup"><span data-stu-id="70a75-124">Grouping by numeric range</span></span>

<span data-ttu-id="70a75-125">Další příklad používá výraz k vytvoření číselných skupinových klíčů, které představují rozsah percentilu.</span><span class="sxs-lookup"><span data-stu-id="70a75-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="70a75-126">Všimněte si použití [let](let-clause.md) jako vhodné umístění pro uložení výsledku volání metody, takže není `group` třeba volat metodu dvakrát v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="70a75-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="70a75-127">Další informace o bezpečném použití metod ve výrazech dotazu naleznete [v tématu Zpracování výjimek ve výrazech dotazu](../../linq/handle-exceptions-in-query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="70a75-127">For more information about how to safely use methods in query expressions, see [Handle exceptions in query expressions](../../linq/handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="70a75-128">Seskupení podle složených klíčů</span><span class="sxs-lookup"><span data-stu-id="70a75-128">Grouping by composite keys</span></span>

<span data-ttu-id="70a75-129">Složený klíč použijte, pokud chcete seskupit prvky podle více než jednoho klíče.</span><span class="sxs-lookup"><span data-stu-id="70a75-129">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="70a75-130">Složený klíč vytvoříte pomocí anonymního typu nebo pojmenovaného typu pro uložení klíčového prvku.</span><span class="sxs-lookup"><span data-stu-id="70a75-130">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="70a75-131">V následujícím příkladu předpokládejme, že třída `Person` `surname` byla `city`deklarována s členy s názvem a .</span><span class="sxs-lookup"><span data-stu-id="70a75-131">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="70a75-132">Klauzule `group` způsobí, že samostatná skupina má být vytvořena pro každou sadu osob se stejným příjmením a stejné město.</span><span class="sxs-lookup"><span data-stu-id="70a75-132">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="70a75-133">Pojmenovaný typ použijte, pokud je nutné předat proměnnou dotazu jiné metodě.</span><span class="sxs-lookup"><span data-stu-id="70a75-133">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="70a75-134">Vytvořte speciální třídu pomocí automaticky implementovaných vlastností <xref:System.Object.Equals%2A> pro <xref:System.Object.GetHashCode%2A> klíče a pak přepsat metody a.</span><span class="sxs-lookup"><span data-stu-id="70a75-134">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="70a75-135">Můžete také použít strukturu, v takovém případě není nutné přísně přepsat tyto metody.</span><span class="sxs-lookup"><span data-stu-id="70a75-135">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="70a75-136">Další informace naleznete [v tématu Jak implementovat zjednodušenou třídu s automaticky implementovanými vlastnostmi](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) a [Jak se dotazovat na duplicitní soubory ve stromu adresářů](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="70a75-136">For more information see [How to implement a lightweight class with auto-implemented properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to query for duplicate files in a directory tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="70a75-137">Druhý článek má příklad kódu, který ukazuje, jak používat složený klíč s pojmenovaným typem.</span><span class="sxs-lookup"><span data-stu-id="70a75-137">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="70a75-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="70a75-138">Example</span></span>

<span data-ttu-id="70a75-139">Následující příklad ukazuje standardní vzor pro řazení zdrojových dat do skupin, pokud není použita žádná další logika dotazu pro skupiny.</span><span class="sxs-lookup"><span data-stu-id="70a75-139">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="70a75-140">To se nazývá seskupení bez pokračování.</span><span class="sxs-lookup"><span data-stu-id="70a75-140">This is called a grouping without a continuation.</span></span> <span data-ttu-id="70a75-141">Prvky v poli řetězců jsou seskupeny podle jejich prvního písmene.</span><span class="sxs-lookup"><span data-stu-id="70a75-141">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="70a75-142">Výsledkem <xref:System.Linq.IGrouping%602> dotazu je typ, který `Key` obsahuje `char` veřejnou <xref:System.Collections.Generic.IEnumerable%601> vlastnost typu a kolekci, která obsahuje každou položku ve seskupení.</span><span class="sxs-lookup"><span data-stu-id="70a75-142">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="70a75-143">Výsledkem `group` klauzule je posloupnost sekvencí.</span><span class="sxs-lookup"><span data-stu-id="70a75-143">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="70a75-144">Proto pro přístup k jednotlivým prvkům v rámci `foreach` každé vrácené skupiny použijte vnořenou smyčku uvnitř smyčky, která itestraje klíče skupiny, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="70a75-144">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="70a75-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="70a75-145">Example</span></span>

<span data-ttu-id="70a75-146">Tento příklad ukazuje, jak provést další logiku ve skupinách *continuation* po `into`jejich vytvoření pomocí pokračování s .</span><span class="sxs-lookup"><span data-stu-id="70a75-146">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="70a75-147">Další informace naleznete [v tématu](into.md).</span><span class="sxs-lookup"><span data-stu-id="70a75-147">For more information, see [into](into.md).</span></span> <span data-ttu-id="70a75-148">Následující příklad dotazuje každou skupinu vybrat pouze ty, jejichž hodnota klíče je samohláská.</span><span class="sxs-lookup"><span data-stu-id="70a75-148">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="70a75-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70a75-149">Remarks</span></span>

<span data-ttu-id="70a75-150">V době `group` kompilace klauzule jsou přeloženy do volání <xref:System.Linq.Enumerable.GroupBy%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="70a75-150">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="70a75-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="70a75-151">See also</span></span>

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [<span data-ttu-id="70a75-152">Klíčová slova dotazu</span><span class="sxs-lookup"><span data-stu-id="70a75-152">Query Keywords</span></span>](query-keywords.md)
- [<span data-ttu-id="70a75-153">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="70a75-153">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="70a75-154">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="70a75-154">Create a nested group</span></span>](../../linq/create-a-nested-group.md)
- [<span data-ttu-id="70a75-155">Seskupení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="70a75-155">Group query results</span></span>](../../linq/group-query-results.md)
- [<span data-ttu-id="70a75-156">Provádění poddotazů na skupinách</span><span class="sxs-lookup"><span data-stu-id="70a75-156">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)
