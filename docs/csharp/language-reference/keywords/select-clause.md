---
description: Select – klauzule – reference jazyka C#
title: Select – klauzule – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: d67c99cc841c08a63cc83843a07a46e80199b9d1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136899"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="b514a-103">select – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b514a-103">select clause (C# Reference)</span></span>

<span data-ttu-id="b514a-104">Ve výrazu dotazu `select` klauzule určuje typ hodnot, které budou vytvořeny při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="b514a-104">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="b514a-105">Výsledek vychází z vyhodnocení všech předchozích klauzulí a na jakékoli výrazy v `select` klauzuli samotné.</span><span class="sxs-lookup"><span data-stu-id="b514a-105">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="b514a-106">Výraz dotazu musí být ukončen `select` klauzulí klauzule nebo [Group](group-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="b514a-106">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="b514a-107">Následující příklad ukazuje jednoduchou `select` klauzuli ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="b514a-107">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="b514a-108">Typ sekvence vytvářené `select` klauzulí určuje typ proměnné dotazu `queryHighScores` .</span><span class="sxs-lookup"><span data-stu-id="b514a-108">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="b514a-109">V nejjednodušším případě `select` klauzule pouze určuje proměnnou rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b514a-109">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="b514a-110">To způsobí, že vrácená sekvence bude obsahovat prvky stejného typu jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="b514a-110">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="b514a-111">Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b514a-111">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="b514a-112">Nicméně `select` klauzule také poskytuje výkonný mechanizmus pro transformaci (nebo *projekci*) zdrojových dat do nových typů.</span><span class="sxs-lookup"><span data-stu-id="b514a-112">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="b514a-113">Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="b514a-113">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="b514a-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="b514a-114">Example</span></span>

<span data-ttu-id="b514a-115">Následující příklad ukazuje všechny různé formuláře, které `select` klauzule může provést.</span><span class="sxs-lookup"><span data-stu-id="b514a-115">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="b514a-116">V každém dotazu si poznamenejte vztah mezi `select` klauzulí a typem *proměnné dotazu* ( `studentQuery1` , `studentQuery2` a tak dále).</span><span class="sxs-lookup"><span data-stu-id="b514a-116">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="b514a-117">Jak je znázorněno v `studentQuery8` předchozím příkladu, někdy může být vhodné, aby prvky vrácené sekvence obsahovaly pouze podmnožinu vlastností zdrojových elementů.</span><span class="sxs-lookup"><span data-stu-id="b514a-117">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="b514a-118">Udržováním vrácené sekvence co nejmenší je možné snížit nároky na paměť a zvýšit rychlost provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="b514a-118">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="b514a-119">To lze provést tak, že vytvoříte anonymní typ v `select` klauzuli a pomocí inicializátoru objektu jej inicializujete s příslušnými vlastnostmi ze zdrojového elementu.</span><span class="sxs-lookup"><span data-stu-id="b514a-119">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="b514a-120">Příklad, jak to provést, naleznete v tématu [Inicializátory objektů a kolekcí](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="b514a-120">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="b514a-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b514a-121">Remarks</span></span>

<span data-ttu-id="b514a-122">V době kompilace `select` je klauzule přeložena na volání metody <xref:System.Linq.Enumerable.Select%2A> standardního operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="b514a-122">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="b514a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b514a-123">See also</span></span>

- [<span data-ttu-id="b514a-124">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b514a-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b514a-125">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b514a-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="b514a-126">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="b514a-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="b514a-127">Partial (metoda) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b514a-127">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="b514a-128">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="b514a-128">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="b514a-129">LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="b514a-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="b514a-130">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="b514a-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
