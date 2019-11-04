---
title: vybrat klauzuli – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: f1bfbeccaf6c3916a591f6447760fa01c3f8a3b6
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422355"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="27784-102">select – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="27784-102">select clause (C# Reference)</span></span>

<span data-ttu-id="27784-103">Ve výrazu dotazu určuje klauzule `select` typ hodnot, které budou vytvořeny při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="27784-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="27784-104">Výsledek vychází z vyhodnocení všech předchozích klauzulí a na jakékoli výrazy v klauzuli `select` samotné.</span><span class="sxs-lookup"><span data-stu-id="27784-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="27784-105">Výraz dotazu musí být ukončen buď klauzulí `select`, nebo klauzulí [Group](group-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="27784-105">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="27784-106">Následující příklad ukazuje jednoduchou klauzuli `select` ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="27784-106">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="27784-107">Typ sekvence, která je vytvořena klauzulí `select`, určuje typ proměnné dotazu `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="27784-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="27784-108">V nejjednodušším případě klauzule `select` pouze určuje proměnnou rozsahu.</span><span class="sxs-lookup"><span data-stu-id="27784-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="27784-109">To způsobí, že vrácená sekvence bude obsahovat prvky stejného typu jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="27784-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="27784-110">Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="27784-110">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="27784-111">Klauzule `select` však také poskytuje výkonný mechanizmus pro transformaci (nebo *projekci*) zdrojových dat do nových typů.</span><span class="sxs-lookup"><span data-stu-id="27784-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="27784-112">Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="27784-112">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="27784-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="27784-113">Example</span></span>

<span data-ttu-id="27784-114">Následující příklad ukazuje všechny různé formuláře, které může klauzule `select` trvat.</span><span class="sxs-lookup"><span data-stu-id="27784-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="27784-115">V každém dotazu si poznamenejte vztah mezi klauzulí `select` a typem *proměnné dotazu* (`studentQuery1`, `studentQuery2`a tak dále).</span><span class="sxs-lookup"><span data-stu-id="27784-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="27784-116">Jak ukazuje `studentQuery8` v předchozím příkladu, někdy můžete chtít, aby prvky vrácené sekvence obsahovaly pouze podmnožinu vlastností zdrojových elementů.</span><span class="sxs-lookup"><span data-stu-id="27784-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="27784-117">Udržováním vrácené sekvence co nejmenší je možné snížit nároky na paměť a zvýšit rychlost provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="27784-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="27784-118">To lze provést tak, že vytvoříte anonymní typ v klauzuli `select` a pomocí inicializátoru objektu jej inicializujete s příslušnými vlastnostmi ze zdrojového elementu.</span><span class="sxs-lookup"><span data-stu-id="27784-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="27784-119">Příklad, jak to provést, naleznete v tématu [Inicializátory objektů a kolekcí](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="27784-119">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="27784-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27784-120">Remarks</span></span>

<span data-ttu-id="27784-121">V době kompilace je klauzule `select` přeložena do volání metody standardní operátor dotazu <xref:System.Linq.Enumerable.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="27784-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="27784-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27784-122">See also</span></span>

- [<span data-ttu-id="27784-123">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="27784-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="27784-124">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="27784-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="27784-125">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="27784-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="27784-126">Partial (metoda) (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="27784-126">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="27784-127">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="27784-127">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="27784-128">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="27784-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="27784-129">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="27784-129">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
