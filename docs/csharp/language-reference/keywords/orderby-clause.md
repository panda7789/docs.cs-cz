---
title: klauzule orderby - C# Reference
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: cd76b2c33fe1a1a986bc05e3c3ed5f22809686ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173572"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="dd5e5-102">orderby – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dd5e5-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="dd5e5-103">Ve výrazu dotazu `orderby` klauzule způsobí, že vrácená sekvence nebo dílčí sekvence (skupina) mají být seřazeny vzestupně nebo sestupně.</span><span class="sxs-lookup"><span data-stu-id="dd5e5-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="dd5e5-104">Pro provedení jedné nebo více sekundárních operací řazení lze zadat více klíčů.</span><span class="sxs-lookup"><span data-stu-id="dd5e5-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="dd5e5-105">Řazení se provádí výchozí porovnávání pro typ prvku.</span><span class="sxs-lookup"><span data-stu-id="dd5e5-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="dd5e5-106">Výchozí pořadí řazení je vzestupně.</span><span class="sxs-lookup"><span data-stu-id="dd5e5-106">The default sort order is ascending.</span></span> <span data-ttu-id="dd5e5-107">Můžete také zadat vlastní porovnávání.</span><span class="sxs-lookup"><span data-stu-id="dd5e5-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="dd5e5-108">Je však k dispozici pouze pomocí syntaxe založené na metodě.</span><span class="sxs-lookup"><span data-stu-id="dd5e5-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="dd5e5-109">Další informace naleznete v [tématu Řazení dat](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="dd5e5-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="dd5e5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd5e5-110">Example</span></span>

<span data-ttu-id="dd5e5-111">V následujícím příkladu první dotaz seřadí slova v abecedním pořadí od A a druhý dotaz seřadí stejná slova v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="dd5e5-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="dd5e5-112">(Klíčové `ascending` slovo je výchozí hodnotou řazení a lze jej vynechat.)</span><span class="sxs-lookup"><span data-stu-id="dd5e5-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="dd5e5-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd5e5-113">Example</span></span>

<span data-ttu-id="dd5e5-114">Následující příklad provádí primární řazení na příjmení studentů a potom sekundární řazení na jejich křestní jména.</span><span class="sxs-lookup"><span data-stu-id="dd5e5-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="dd5e5-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd5e5-115">Remarks</span></span>

<span data-ttu-id="dd5e5-116">V době kompilace klauzule `orderby` je přeložen <xref:System.Linq.Enumerable.OrderBy%2A> a volání metody.</span><span class="sxs-lookup"><span data-stu-id="dd5e5-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="dd5e5-117">Více klíčů `orderby` v klauzuli přeložit volání <xref:System.Linq.Enumerable.ThenBy%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dd5e5-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd5e5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd5e5-118">See also</span></span>

- [<span data-ttu-id="dd5e5-119">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dd5e5-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dd5e5-120">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="dd5e5-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="dd5e5-121">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dd5e5-121">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="dd5e5-122">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="dd5e5-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="dd5e5-123">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="dd5e5-123">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
