---
title: "orderby – klauzule (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc688e7ba164dcca71d13b2d79d30f1373c4778e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="d9f88-102">orderby – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d9f88-102">orderby clause (C# Reference)</span></span>
<span data-ttu-id="d9f88-103">Ve výrazu dotazu `orderby` klauzule způsobí, že vrácený pořadí nebo dalším (skupiny), který se má seřadit ve vzestupném nebo sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d9f88-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="d9f88-104">Aby bylo možné provést jednu nebo více operací sekundární řazení lze zadat více klíčů.</span><span class="sxs-lookup"><span data-stu-id="d9f88-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="d9f88-105">Toto řazení je prováděno pomocí porovnávače výchozí pro typ elementu.</span><span class="sxs-lookup"><span data-stu-id="d9f88-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="d9f88-106">Výchozí pořadí řazení je vzestupně.</span><span class="sxs-lookup"><span data-stu-id="d9f88-106">The default sort order is ascending.</span></span> <span data-ttu-id="d9f88-107">Můžete také zadat vlastní porovnávací funkci.</span><span class="sxs-lookup"><span data-stu-id="d9f88-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="d9f88-108">Je však pouze k dispozici pomocí syntaxe na základě metod.</span><span class="sxs-lookup"><span data-stu-id="d9f88-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="d9f88-109">Další informace najdete v tématu [řazení dat](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="d9f88-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9f88-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9f88-110">Example</span></span>  
 <span data-ttu-id="d9f88-111">V následujícím příkladu první dotaz seřadí slova v abecedním pořadí spouštění z A a druhý dotaz seřadí stejná slova v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d9f88-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="d9f88-112">( `ascending` – Klíčové slovo je výchozí hodnota řazení a lze vynechat.)</span><span class="sxs-lookup"><span data-stu-id="d9f88-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="d9f88-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9f88-113">Example</span></span>  
 <span data-ttu-id="d9f88-114">Následující příklad primární řazení na na studentů příjmení a sekundární řazení provádí jejich názvy první.</span><span class="sxs-lookup"><span data-stu-id="d9f88-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="d9f88-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9f88-115">Remarks</span></span>  
 <span data-ttu-id="d9f88-116">Při kompilaci `orderby` přeložen volání <xref:System.Linq.Enumerable.OrderBy%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d9f88-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="d9f88-117">Více klíčů v `orderby` klauzule nepřeloží na <xref:System.Linq.Enumerable.ThenBy%2A> volání metody.</span><span class="sxs-lookup"><span data-stu-id="d9f88-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f88-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9f88-118">See Also</span></span>  
 [<span data-ttu-id="d9f88-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d9f88-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d9f88-120">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d9f88-120">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="d9f88-121">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="d9f88-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="d9f88-122">Group – klauzule</span><span class="sxs-lookup"><span data-stu-id="d9f88-122">group clause</span></span>](../../../csharp/language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="d9f88-123">Začínáme s dotazy LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="d9f88-123">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
