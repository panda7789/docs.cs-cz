---
title: orderby – klauzule (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 1fd0036e8bd3c838fe92ca27635cd7638d59ef1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268048"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="5111d-102">orderby – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5111d-102">orderby clause (C# Reference)</span></span>
<span data-ttu-id="5111d-103">Ve výrazu dotazu `orderby` klauzule způsobí, že vrácený pořadí nebo dalším (skupiny), který se má seřadit ve vzestupném nebo sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5111d-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="5111d-104">Aby bylo možné provést jednu nebo více operací sekundární řazení lze zadat více klíčů.</span><span class="sxs-lookup"><span data-stu-id="5111d-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="5111d-105">Toto řazení je prováděno pomocí porovnávače výchozí pro typ elementu.</span><span class="sxs-lookup"><span data-stu-id="5111d-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="5111d-106">Výchozí pořadí řazení je vzestupně.</span><span class="sxs-lookup"><span data-stu-id="5111d-106">The default sort order is ascending.</span></span> <span data-ttu-id="5111d-107">Můžete také zadat vlastní porovnávací funkci.</span><span class="sxs-lookup"><span data-stu-id="5111d-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="5111d-108">Je však pouze k dispozici pomocí syntaxe na základě metod.</span><span class="sxs-lookup"><span data-stu-id="5111d-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="5111d-109">Další informace najdete v tématu [řazení dat](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="5111d-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5111d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5111d-110">Example</span></span>  
 <span data-ttu-id="5111d-111">V následujícím příkladu první dotaz seřadí slova v abecedním pořadí spouštění z A a druhý dotaz seřadí stejná slova v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5111d-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="5111d-112">( `ascending` – Klíčové slovo je výchozí hodnota řazení a lze vynechat.)</span><span class="sxs-lookup"><span data-stu-id="5111d-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="5111d-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="5111d-113">Example</span></span>  
 <span data-ttu-id="5111d-114">Následující příklad primární řazení na na studentů příjmení a sekundární řazení provádí jejich názvy první.</span><span class="sxs-lookup"><span data-stu-id="5111d-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="5111d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5111d-115">Remarks</span></span>  
 <span data-ttu-id="5111d-116">Při kompilaci `orderby` přeložen volání <xref:System.Linq.Enumerable.OrderBy%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5111d-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="5111d-117">Více klíčů v `orderby` klauzule nepřeloží na <xref:System.Linq.Enumerable.ThenBy%2A> volání metody.</span><span class="sxs-lookup"><span data-stu-id="5111d-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5111d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5111d-118">See Also</span></span>  
 [<span data-ttu-id="5111d-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5111d-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5111d-120">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="5111d-120">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="5111d-121">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="5111d-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="5111d-122">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="5111d-122">group clause</span></span>](../../../csharp/language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="5111d-123">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5111d-123">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
