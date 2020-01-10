---
title: Klauzule OrderBy – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: d88b2b40f63f0616cfd54e8abb62f1bc2183f776
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713301"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="5db58-102">orderby – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5db58-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="5db58-103">Ve výrazu dotazu klauzule `orderby` způsobí, že vrácená sekvence nebo dílčí sekvence (skupina) bude seřazena ve vzestupném nebo sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5db58-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="5db58-104">K provedení jedné nebo více sekundárních operací řazení lze zadat více klíčů.</span><span class="sxs-lookup"><span data-stu-id="5db58-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="5db58-105">Řazení je provedeno pomocí výchozí porovnávací metody pro typ elementu.</span><span class="sxs-lookup"><span data-stu-id="5db58-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="5db58-106">Výchozí pořadí řazení je vzestupné.</span><span class="sxs-lookup"><span data-stu-id="5db58-106">The default sort order is ascending.</span></span> <span data-ttu-id="5db58-107">Můžete také zadat vlastní porovnávací metodu.</span><span class="sxs-lookup"><span data-stu-id="5db58-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="5db58-108">Je však k dispozici pouze pomocí syntaxe založené na metodě.</span><span class="sxs-lookup"><span data-stu-id="5db58-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="5db58-109">Další informace najdete v tématu [řazení dat](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="5db58-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="5db58-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5db58-110">Example</span></span>

<span data-ttu-id="5db58-111">V následujícím příkladu první dotaz seřadí slova v abecedním pořadí začínajícím na a druhý dotaz seřadí stejná slova v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5db58-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="5db58-112">(Klíčové slovo `ascending` je výchozí hodnota řazení a může být vynechána.)</span><span class="sxs-lookup"><span data-stu-id="5db58-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="5db58-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="5db58-113">Example</span></span>

<span data-ttu-id="5db58-114">Následující příklad provádí primární řazení pro příjmení studentů a pak sekundární řazení podle jejich křestních jmen.</span><span class="sxs-lookup"><span data-stu-id="5db58-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="5db58-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5db58-115">Remarks</span></span>

<span data-ttu-id="5db58-116">V době kompilace je klauzule `orderby` přeložena na volání metody <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="5db58-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="5db58-117">Více klíčů v klauzuli `orderby` se přeloží na <xref:System.Linq.Enumerable.ThenBy%2A> volání metod.</span><span class="sxs-lookup"><span data-stu-id="5db58-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="5db58-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5db58-118">See also</span></span>

- [<span data-ttu-id="5db58-119">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="5db58-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5db58-120">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="5db58-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="5db58-121"> (LINQ)</span><span class="sxs-lookup"><span data-stu-id="5db58-121">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="5db58-122">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="5db58-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="5db58-123">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5db58-123">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
