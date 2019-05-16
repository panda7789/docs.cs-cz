---
title: Select – klauzule - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 3ba52fccc0521df1a0bb5b6177575dc5d2152248
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633810"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="d4e83-102">select – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d4e83-102">select clause (C# Reference)</span></span>

<span data-ttu-id="d4e83-103">Ve výrazu dotazu `select` klauzule určuje typ hodnoty, které se budou vytvářet při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="d4e83-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="d4e83-104">Výsledkem je založeno na vyhodnocení všechny předchozí klauzule a na všechny výrazy v `select` klauzule samotný.</span><span class="sxs-lookup"><span data-stu-id="d4e83-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="d4e83-105">Buď musí končit výrazu dotazu `select` klauzule nebo [skupiny](group-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d4e83-105">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="d4e83-106">Následující příklad ukazuje jednoduchý `select` klauzule ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="d4e83-106">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="d4e83-107">Typ pořadí vytvářených `select` klauzule určuje typ proměnné dotazu `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="d4e83-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="d4e83-108">V nejjednodušším případě `select` klauzule právě Určuje proměnnou rozsahu.</span><span class="sxs-lookup"><span data-stu-id="d4e83-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="d4e83-109">To způsobí, že vrácená sekvence má obsahovat prvky stejného typu jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="d4e83-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="d4e83-110">Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d4e83-110">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="d4e83-111">Ale `select` klauzule také poskytuje výkonný mechanismus pro transformaci (nebo *projekci*) zdroje dat do nové typy.</span><span class="sxs-lookup"><span data-stu-id="d4e83-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="d4e83-112">Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="d4e83-112">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="d4e83-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4e83-113">Example</span></span>

<span data-ttu-id="d4e83-114">Následující příklad ukazuje různé formuláře, který `select` klauzule může trvat.</span><span class="sxs-lookup"><span data-stu-id="d4e83-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="d4e83-115">V obou dotazech, mějte na paměti o vztah mezi `select` klauzule a typ *proměnné dotazu* (`studentQuery1`, `studentQuery2`, a tak dále).</span><span class="sxs-lookup"><span data-stu-id="d4e83-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="d4e83-116">Jak je znázorněno v `studentQuery8` v předchozím příkladu, můžete někdy chtít prvky vrácená sekvence má obsahovat pouze podmnožinu vlastností zdrojové elementy.</span><span class="sxs-lookup"><span data-stu-id="d4e83-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="d4e83-117">Udržováním vrácené posloupnosti co nejmenší může snížit požadavky na paměť a zvýšit rychlost provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="d4e83-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="d4e83-118">Můžete to udělat tak, že vytvoříte anonymního typu v `select` klauzule a pomocí inicializátoru objektu inicializovat s odpovídající vlastností ze zdrojového elementu.</span><span class="sxs-lookup"><span data-stu-id="d4e83-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="d4e83-119">Příklad toho, jak to provést, najdete v části [inicializátory objektu a kolekce](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="d4e83-119">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="d4e83-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4e83-120">Remarks</span></span>

<span data-ttu-id="d4e83-121">V době kompilace `select` přeložen na volání metody <xref:System.Linq.Enumerable.Select%2A> standardní operátor dotazu.</span><span class="sxs-lookup"><span data-stu-id="d4e83-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4e83-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4e83-122">See also</span></span>

- [<span data-ttu-id="d4e83-123">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d4e83-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d4e83-124">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d4e83-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="d4e83-125">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="d4e83-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="d4e83-126">partial (metoda) (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d4e83-126">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="d4e83-127">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="d4e83-127">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="d4e83-128">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="d4e83-128">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="d4e83-129">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d4e83-129">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)
