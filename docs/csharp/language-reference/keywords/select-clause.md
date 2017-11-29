---
title: "select – klauzule (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f40bc26d1812e76ac618c5a0ddf23c4cef2700d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="e2350-102">select – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e2350-102">select clause (C# Reference)</span></span>
<span data-ttu-id="e2350-103">Ve výrazu dotazu `select` klauzuli Určuje typ hodnoty, které budou vytvořeny, když je proveden dotaz.</span><span class="sxs-lookup"><span data-stu-id="e2350-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="e2350-104">Výsledkem je založena na vyhodnocení všechny předchozí klauzule a na všechny výrazy v `select` klauzule sám sebe.</span><span class="sxs-lookup"><span data-stu-id="e2350-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="e2350-105">Výraz dotazu musí ukončit některým `select` klauzule nebo [skupiny](../../../csharp/language-reference/keywords/group-clause.md) klauzule.</span><span class="sxs-lookup"><span data-stu-id="e2350-105">A query expression must terminate with either a `select` clause or a [group](../../../csharp/language-reference/keywords/group-clause.md) clause.</span></span>  
  
 <span data-ttu-id="e2350-106">Následující příklad ukazuje jednoduchý `select` klauzule ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="e2350-106">The following example shows a simple `select` clause in a query expression.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 <span data-ttu-id="e2350-107">Typ pořadí vyprodukované `select` klauzuli Určuje typ proměnné dotazu `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="e2350-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="e2350-108">V nejjednodušším případě `select` klauzule právě Určuje proměnnou rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e2350-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="e2350-109">To způsobí, že vrácený pořadí tak, aby obsahovala elementy stejného typu jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="e2350-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="e2350-110">Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e2350-110">For more information, see [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="e2350-111">Ale `select` klauzule také poskytuje výkonný mechanismus pro transformaci (nebo *plánování*) zdroj dat do nové typy.</span><span class="sxs-lookup"><span data-stu-id="e2350-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="e2350-112">Další informace najdete v tématu [transformace dat pomocí LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="e2350-112">For more information, see [Data Transformations with LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2350-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2350-113">Example</span></span>  
 <span data-ttu-id="e2350-114">Následující příklad ukazuje na různé způsoby, které `select` klauzule může trvat.</span><span class="sxs-lookup"><span data-stu-id="e2350-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="e2350-115">V každém dotazu Poznámka: vztah mezi `select` klauzule a typ *proměnné dotazu* (`studentQuery1`, `studentQuery2`a tak dále).</span><span class="sxs-lookup"><span data-stu-id="e2350-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 <span data-ttu-id="e2350-116">Jak je znázorněno v `studentQuery8` v předchozím příkladu, v některých případech můžete elementy vrácený pořadí tak, aby obsahovala pouze podmnožinu vlastností zdrojové elementy.</span><span class="sxs-lookup"><span data-stu-id="e2350-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="e2350-117">Udržováním vrácený pořadí co nejmenší může snížit požadavky na paměť a zvýšit rychlost zpracování dotazu.</span><span class="sxs-lookup"><span data-stu-id="e2350-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="e2350-118">To můžete udělat tak, že vytvoříte instanci anonymního typu v `select` klauzule a pomocí inicializátoru objektu k chybě při inicializaci s příslušné vlastnosti ze zdroje elementu.</span><span class="sxs-lookup"><span data-stu-id="e2350-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="e2350-119">Příklad toho, jak to provést, naleznete v části [inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="e2350-119">For an example of how to do this, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2350-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2350-120">Remarks</span></span>  
 <span data-ttu-id="e2350-121">Při kompilaci `select` přeložen volání metody <xref:System.Linq.Enumerable.Select%2A> operátor standardní dotazu.</span><span class="sxs-lookup"><span data-stu-id="e2350-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2350-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2350-122">See Also</span></span>  
 [<span data-ttu-id="e2350-123">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e2350-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e2350-124">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="e2350-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="e2350-125">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="e2350-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="e2350-126">partial (metoda) (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e2350-126">partial (Method) (C# Reference)</span></span>](../../../csharp/language-reference/keywords/partial-method.md)  
 [<span data-ttu-id="e2350-127">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="e2350-127">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="e2350-128">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="e2350-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="e2350-129">Začínáme s dotazy LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="e2350-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
