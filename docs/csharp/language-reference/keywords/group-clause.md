---
title: group clause - C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: dd14a4baf9967f41690e7978b8b6cf57c9275e36
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428505"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="6fa5f-102">group – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6fa5f-102">group clause (C# Reference)</span></span>

<span data-ttu-id="6fa5f-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="6fa5f-104">For example, you can group a sequence of strings according to the first letter in each string.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="6fa5f-105">In this case, the first letter is the key and has a type [char](../builtin-types/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-105">In this case, the first letter is the key and has a type [char](../builtin-types/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="6fa5f-106">The compiler infers the type of the key.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="6fa5f-107">You can end a query expression with a `group` clause, as shown in the following example:</span><span class="sxs-lookup"><span data-stu-id="6fa5f-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="6fa5f-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="6fa5f-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span><span class="sxs-lookup"><span data-stu-id="6fa5f-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="6fa5f-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="6fa5f-111">Enumerating the results of a group query</span><span class="sxs-lookup"><span data-stu-id="6fa5f-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="6fa5f-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="6fa5f-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="6fa5f-114">A group may have a key but no elements.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-114">A group may have a key but no elements.</span></span> <span data-ttu-id="6fa5f-115">The following is the `foreach` loop that executes the query in the previous code examples:</span><span class="sxs-lookup"><span data-stu-id="6fa5f-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="6fa5f-116">Key types</span><span class="sxs-lookup"><span data-stu-id="6fa5f-116">Key types</span></span>

<span data-ttu-id="6fa5f-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="6fa5f-118">Grouping by string</span><span class="sxs-lookup"><span data-stu-id="6fa5f-118">Grouping by string</span></span>

<span data-ttu-id="6fa5f-119">The previous code examples used a `char`.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="6fa5f-120">A string key could easily have been specified instead, for example the complete last name:</span><span class="sxs-lookup"><span data-stu-id="6fa5f-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="6fa5f-121">Grouping by bool</span><span class="sxs-lookup"><span data-stu-id="6fa5f-121">Grouping by bool</span></span>

<span data-ttu-id="6fa5f-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="6fa5f-123">Note that the value is produced by a sub-expression in the `group` clause.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="6fa5f-124">Grouping by numeric range</span><span class="sxs-lookup"><span data-stu-id="6fa5f-124">Grouping by numeric range</span></span>

<span data-ttu-id="6fa5f-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="6fa5f-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="6fa5f-127">For more information about how to safely use methods in query expressions, see [How to: Handle Exceptions in Query Expressions](../../linq/handle-exceptions-in-query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6fa5f-127">For more information about how to safely use methods in query expressions, see [How to: Handle Exceptions in Query Expressions](../../linq/handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="6fa5f-128">Grouping by composite keys</span><span class="sxs-lookup"><span data-stu-id="6fa5f-128">Grouping by composite keys</span></span>

<span data-ttu-id="6fa5f-129">Use a composite key when you want to group elements according to more than one key.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-129">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="6fa5f-130">You create a composite key by using an anonymous type or a named type to hold the key element.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-130">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="6fa5f-131">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-131">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="6fa5f-132">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-132">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="6fa5f-133">Use a named type if you must pass the query variable to another method.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-133">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="6fa5f-134">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-134">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="6fa5f-135">You can also use a struct, in which case you do not strictly have to override those methods.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-135">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="6fa5f-136">For more information see [How to implement a lightweight class with auto-implemented properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to: Query for Duplicate Files in a Directory Tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="6fa5f-136">For more information see [How to implement a lightweight class with auto-implemented properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to: Query for Duplicate Files in a Directory Tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="6fa5f-137">The latter article has a code example that demonstrates how to use a composite key with a named type.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-137">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="6fa5f-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="6fa5f-138">Example</span></span>

<span data-ttu-id="6fa5f-139">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-139">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="6fa5f-140">This is called a grouping without a continuation.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-140">This is called a grouping without a continuation.</span></span> <span data-ttu-id="6fa5f-141">The elements in an array of strings are grouped according to their first letter.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-141">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="6fa5f-142">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-142">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="6fa5f-143">The result of a `group` clause is a sequence of sequences.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-143">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="6fa5f-144">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-144">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="6fa5f-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="6fa5f-145">Example</span></span>

<span data-ttu-id="6fa5f-146">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-146">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="6fa5f-147">For more information, see [into](into.md).</span><span class="sxs-lookup"><span data-stu-id="6fa5f-147">For more information, see [into](into.md).</span></span> <span data-ttu-id="6fa5f-148">The following example queries each group to select only those whose key value is a vowel.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-148">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="6fa5f-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fa5f-149">Remarks</span></span>

<span data-ttu-id="6fa5f-150">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span><span class="sxs-lookup"><span data-stu-id="6fa5f-150">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fa5f-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fa5f-151">See also</span></span>

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [<span data-ttu-id="6fa5f-152">Klíčová slova dotazu</span><span class="sxs-lookup"><span data-stu-id="6fa5f-152">Query Keywords</span></span>](query-keywords.md)
- [<span data-ttu-id="6fa5f-153">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="6fa5f-153">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="6fa5f-154">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="6fa5f-154">Create a nested group</span></span>](../../linq/create-a-nested-group.md)
- [<span data-ttu-id="6fa5f-155">Seskupení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="6fa5f-155">Group query results</span></span>](../../linq/group-query-results.md)
- [<span data-ttu-id="6fa5f-156">Provádění poddotazů na skupinách</span><span class="sxs-lookup"><span data-stu-id="6fa5f-156">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)
