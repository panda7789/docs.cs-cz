---
title: klauzule Group – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 806bc3de138ebae682d2e248593230c753eb7ba2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422762"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="b0a3f-102">group – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b0a3f-102">group clause (C# Reference)</span></span>

<span data-ttu-id="b0a3f-103">Klauzule `group` vrací sekvenci <xref:System.Linq.IGrouping%602> objektů, které obsahují nula nebo více položek, které se shodují s hodnotou klíče pro skupinu.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="b0a3f-104">Například můžete seskupit sekvenci řetězců podle prvního písmene v každém řetězci.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="b0a3f-105">V tomto případě je prvním písmenem klíč a má typ [char](char.md)a je uložen ve vlastnosti `Key` každého objektu <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-105">In this case, the first letter is the key and has a type [char](char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="b0a3f-106">Kompilátor odvodí typ klíče.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="b0a3f-107">Můžete ukončit výraz dotazu s klauzulí `group`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b0a3f-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="b0a3f-108">Pokud chcete pro každou skupinu provést další operace dotazování, můžete zadat dočasný identifikátor pomocí klíčového slova [into](into.md) .</span><span class="sxs-lookup"><span data-stu-id="b0a3f-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="b0a3f-109">Při použití `into`musíte pokračovat v dotazu a nakonec ho ukončit buď pomocí příkazu `select` nebo jiné klauzule `group`, jak je znázorněno v následujícím výpisu:</span><span class="sxs-lookup"><span data-stu-id="b0a3f-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="b0a3f-110">Úplnější příklady použití `group` s a bez `into` jsou uvedené v příkladu v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="b0a3f-111">Vyčíslení výsledků dotazu skupiny</span><span class="sxs-lookup"><span data-stu-id="b0a3f-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="b0a3f-112">Vzhledem k tomu, že <xref:System.Linq.IGrouping%602> objekty vytvořené pomocí dotazu `group` jsou v podstatě seznam seznamů, je nutné použít vnořenou smyčku [foreach](foreach-in.md) pro přístup k položkám v každé skupině.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="b0a3f-113">Vnější smyčka projde klíče skupiny a vnitřní smyčka projde každou položku v samotné skupině.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="b0a3f-114">Skupina může mít klíč, ale neobsahuje žádné prvky.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-114">A group may have a key but no elements.</span></span> <span data-ttu-id="b0a3f-115">Následuje `foreach` smyčka, která spouští dotaz v předchozích příkladech kódu:</span><span class="sxs-lookup"><span data-stu-id="b0a3f-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="b0a3f-116">Typy klíčů</span><span class="sxs-lookup"><span data-stu-id="b0a3f-116">Key types</span></span>

<span data-ttu-id="b0a3f-117">Klíče skupiny mohou být libovolného typu, jako je například řetězec, vestavěný číselný typ nebo uživatelsky definovaný pojmenovaný typ nebo anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="b0a3f-118">Seskupení podle řetězce</span><span class="sxs-lookup"><span data-stu-id="b0a3f-118">Grouping by string</span></span>

<span data-ttu-id="b0a3f-119">Předchozí příklady kódu používaly `char`.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="b0a3f-120">Místo toho je možné zadat klíč řetězce, například poslední příjmení:</span><span class="sxs-lookup"><span data-stu-id="b0a3f-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="b0a3f-121">Seskupení podle bool</span><span class="sxs-lookup"><span data-stu-id="b0a3f-121">Grouping by bool</span></span>

<span data-ttu-id="b0a3f-122">Následující příklad ukazuje použití bool hodnoty pro klíč k rozdělení výsledků do dvou skupin.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="b0a3f-123">Všimněte si, že hodnota je vytvořena dílčím výrazem v klauzuli `group`.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="b0a3f-124">Seskupení podle číselného rozsahu</span><span class="sxs-lookup"><span data-stu-id="b0a3f-124">Grouping by numeric range</span></span>

<span data-ttu-id="b0a3f-125">Následující příklad používá výraz pro vytvoření číselné skupiny klíčů, které reprezentují rozsah percentilu.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="b0a3f-126">Všimněte si, že použití [let](let-clause.md) jako vhodného umístění pro uložení výsledku volání metody, takže nemusíte volat metodu dvakrát v klauzuli `group`.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="b0a3f-127">Další informace o bezpečném použití metod ve výrazech dotazů naleznete v tématu [How to: Handle Exceptions in Query Expressions](../../linq/handle-exceptions-in-query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b0a3f-127">For more information about how to safely use methods in query expressions, see [How to: Handle Exceptions in Query Expressions](../../linq/handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="b0a3f-128">Seskupení podle složených klíčů</span><span class="sxs-lookup"><span data-stu-id="b0a3f-128">Grouping by composite keys</span></span>

<span data-ttu-id="b0a3f-129">Pokud chcete seskupit prvky podle více než jednoho klíče, použijte složený klíč.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-129">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="b0a3f-130">Složený klíč vytvoříte pomocí anonymního typu nebo pojmenovaného typu pro uložení klíčového elementu.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-130">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="b0a3f-131">V následujícím příkladu Předpokládejme, že třída `Person` byla deklarována s členy s názvem `surname` a `city`.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-131">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="b0a3f-132">Klauzule `group` způsobí, že se vytvoří samostatná skupina pro každou sadu osob se stejným názvem a stejným městem.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-132">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="b0a3f-133">Pojmenovaný typ použijte v případě, že je nutné předat proměnnou dotazu jiné metodě.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-133">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="b0a3f-134">Vytvořte speciální třídu s použitím automaticky implementovaných vlastností klíčů a potom přepište metody <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-134">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="b0a3f-135">Můžete také použít strukturu. v takovém případě není nutné tyto metody přepsat bezpodmínečně.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-135">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="b0a3f-136">Další informace naleznete v tématu [How to: Implementing Lightweight Class s automaticky implementovanými vlastnostmi](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) a [Postupy: dotaz na duplicitní soubory ve stromové struktuře adresáře](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="b0a3f-136">For more information see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to: Query for Duplicate Files in a Directory Tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="b0a3f-137">Druhý článek obsahuje příklad kódu, který ukazuje, jak použít složený klíč s pojmenovaným typem.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-137">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="b0a3f-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0a3f-138">Example</span></span>

<span data-ttu-id="b0a3f-139">Následující příklad ukazuje standardní vzor pro řazení zdrojových dat do skupin, pokud se pro skupiny nepoužívá žádná další logika dotazu.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-139">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="b0a3f-140">Označuje se jako seskupení bez pokračování.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-140">This is called a grouping without a continuation.</span></span> <span data-ttu-id="b0a3f-141">Prvky v poli řetězců jsou seskupeny podle jejich prvního písmene.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-141">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="b0a3f-142">Výsledkem dotazu je typ <xref:System.Linq.IGrouping%602>, který obsahuje vlastnost Public `Key` typu `char` a kolekci <xref:System.Collections.Generic.IEnumerable%601> obsahující každou položku v seskupení.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-142">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="b0a3f-143">Výsledkem klauzule `group` je sekvence sekvencí.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-143">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="b0a3f-144">Proto pro přístup k jednotlivým prvkům v rámci jednotlivých vrácených skupin použijte vnořený `foreach` smyčka uvnitř smyčky, která opakuje klíče skupiny, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-144">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="b0a3f-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0a3f-145">Example</span></span>

<span data-ttu-id="b0a3f-146">Tento příklad ukazuje, jak provést další logiku pro skupiny po jejich vytvoření pomocí *pokračování* s `into`.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-146">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="b0a3f-147">Další informace najdete [v tématu.](into.md)</span><span class="sxs-lookup"><span data-stu-id="b0a3f-147">For more information, see [into](into.md).</span></span> <span data-ttu-id="b0a3f-148">Následující příklad dotazuje každou skupinu na výběr pouze těch, jejichž klíčová hodnota je samohláska.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-148">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="b0a3f-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0a3f-149">Remarks</span></span>

<span data-ttu-id="b0a3f-150">V době kompilace jsou klauzule `group` přeloženy do volání metody <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0a3f-150">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0a3f-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0a3f-151">See also</span></span>

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [<span data-ttu-id="b0a3f-152">Klíčová slova dotazu</span><span class="sxs-lookup"><span data-stu-id="b0a3f-152">Query Keywords</span></span>](query-keywords.md)
- [<span data-ttu-id="b0a3f-153">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="b0a3f-153">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="b0a3f-154">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="b0a3f-154">Create a nested group</span></span>](../../linq/create-a-nested-group.md)
- [<span data-ttu-id="b0a3f-155">Seskupení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="b0a3f-155">Group query results</span></span>](../../linq/group-query-results.md)
- [<span data-ttu-id="b0a3f-156">Provádění poddotazů na skupinách</span><span class="sxs-lookup"><span data-stu-id="b0a3f-156">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)
