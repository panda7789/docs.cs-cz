---
title: where – klauzule (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0324346ee5e214bf467fcb522ef781c91fa1b76f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="3646e-102">where – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3646e-102">where clause (C# Reference)</span></span>
<span data-ttu-id="3646e-103">`where` Klauzule ve výrazu dotazu slouží k určení, které prvky ze zdroje dat bude vrácen ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="3646e-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="3646e-104">Platí Boolean podmínku (*predikát*) pro každý element source (odkazuje proměnná rozsahu) a vrátí ty, pro které je zadaná podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="3646e-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="3646e-105">Výraz jeden dotaz může obsahovat více `where` klauzule a jedna klauzule může obsahovat několik predikátů podvýrazy.</span><span class="sxs-lookup"><span data-stu-id="3646e-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3646e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3646e-106">Example</span></span>  
 <span data-ttu-id="3646e-107">V následujícím příkladu `where` klauzule filtruje všechna čísla kromě těch, které jsou menší než 5.</span><span class="sxs-lookup"><span data-stu-id="3646e-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="3646e-108">Pokud odeberete `where` klauzule, všechna čísla ze zdroje dat by vrátila.</span><span class="sxs-lookup"><span data-stu-id="3646e-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="3646e-109">Výraz `num < 5` je predikát, který se použije pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="3646e-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="3646e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="3646e-110">Example</span></span>  
 <span data-ttu-id="3646e-111">V rámci jednoho `where` klauzuli tolik predikáty podle potřeby můžete zadat pomocí [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) a [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="3646e-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operators.</span></span> <span data-ttu-id="3646e-112">V následujícím příkladu dotaz určuje dvě predikáty Chcete-li vybrat pouze sudá čísla, které jsou menší než 5.</span><span class="sxs-lookup"><span data-stu-id="3646e-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="3646e-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="3646e-113">Example</span></span>  
 <span data-ttu-id="3646e-114">A `where` klauzule může obsahovat jednu nebo více metod, které vracejí logické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3646e-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="3646e-115">V následujícím příkladu `where` klauzule používá k určení, zda je aktuální hodnota proměnné rozsahu popisných metody.</span><span class="sxs-lookup"><span data-stu-id="3646e-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="3646e-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3646e-116">Remarks</span></span>  
 <span data-ttu-id="3646e-117">`where` Mechanismus filtrování je klauzule.</span><span class="sxs-lookup"><span data-stu-id="3646e-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="3646e-118">Je možné umístit téměř odkudkoli ve výrazu dotazu s výjimkou nemůže být klauzuli první nebo poslední.</span><span class="sxs-lookup"><span data-stu-id="3646e-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="3646e-119">A `where` před nebo po, může se zobrazit klauzule [skupiny](../../../csharp/language-reference/keywords/group-clause.md) klauzule v závislosti na tom, jestli máte k filtrování zdrojové elementy před nebo po jsou seskupené.</span><span class="sxs-lookup"><span data-stu-id="3646e-119">A `where` clause may appear either before or after a [group](../../../csharp/language-reference/keywords/group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>  
  
 <span data-ttu-id="3646e-120">Pokud zadaným predikátem není platný pro elementy ve zdroji dat, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="3646e-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="3646e-121">Toto je jednou z výhod silné – kontrola typu poskytované [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3646e-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="3646e-122">Při kompilaci `where` – klíčové slovo je převeden na volání <xref:System.Linq.Enumerable.Where%2A> metoda standardní – operátor dotazu.</span><span class="sxs-lookup"><span data-stu-id="3646e-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3646e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="3646e-123">See Also</span></span>  
 [<span data-ttu-id="3646e-124">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="3646e-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="3646e-125">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="3646e-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="3646e-126">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="3646e-126">select clause</span></span>](../../../csharp/language-reference/keywords/select-clause.md)  
 [<span data-ttu-id="3646e-127">Filtrování dat</span><span class="sxs-lookup"><span data-stu-id="3646e-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)  
 [<span data-ttu-id="3646e-128">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="3646e-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="3646e-129">Začínáme s dotazy LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="3646e-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
