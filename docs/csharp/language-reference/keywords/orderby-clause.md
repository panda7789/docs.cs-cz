---
description: orderby – klauzule – reference jazyka C#
title: orderby – klauzule – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 2f64b45ff252c7cc02e56c465da21ccc5e861aec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142346"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="48e8d-103">orderby – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="48e8d-103">orderby clause (C# Reference)</span></span>

<span data-ttu-id="48e8d-104">Ve výrazu dotazu `orderby` klauzule způsobí, že vrácená sekvence nebo dílčí sekvence (skupina) bude seřazena ve vzestupném nebo sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="48e8d-104">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="48e8d-105">K provedení jedné nebo více sekundárních operací řazení lze zadat více klíčů.</span><span class="sxs-lookup"><span data-stu-id="48e8d-105">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="48e8d-106">Řazení je provedeno pomocí výchozí porovnávací metody pro typ elementu.</span><span class="sxs-lookup"><span data-stu-id="48e8d-106">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="48e8d-107">Výchozí pořadí řazení je vzestupné.</span><span class="sxs-lookup"><span data-stu-id="48e8d-107">The default sort order is ascending.</span></span> <span data-ttu-id="48e8d-108">Můžete také zadat vlastní porovnávací metodu.</span><span class="sxs-lookup"><span data-stu-id="48e8d-108">You can also specify a custom comparer.</span></span> <span data-ttu-id="48e8d-109">Je však k dispozici pouze pomocí syntaxe založené na metodě.</span><span class="sxs-lookup"><span data-stu-id="48e8d-109">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="48e8d-110">Další informace najdete v tématu [řazení dat](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="48e8d-110">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="48e8d-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="48e8d-111">Example</span></span>

<span data-ttu-id="48e8d-112">V následujícím příkladu první dotaz seřadí slova v abecedním pořadí začínajícím na a druhý dotaz seřadí stejná slova v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="48e8d-112">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="48e8d-113">( `ascending` Klíčové slovo je výchozí hodnota řazení a může být vynecháno.)</span><span class="sxs-lookup"><span data-stu-id="48e8d-113">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="48e8d-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="48e8d-114">Example</span></span>

<span data-ttu-id="48e8d-115">Následující příklad provádí primární řazení pro příjmení studentů a pak sekundární řazení podle jejich křestních jmen.</span><span class="sxs-lookup"><span data-stu-id="48e8d-115">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="48e8d-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48e8d-116">Remarks</span></span>

<span data-ttu-id="48e8d-117">V době kompilace `orderby` je klauzule přeložena na volání <xref:System.Linq.Enumerable.OrderBy%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="48e8d-117">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="48e8d-118">Více klíčů v `orderby` klauzuli je přeloženo na <xref:System.Linq.Enumerable.ThenBy%2A> volání metody.</span><span class="sxs-lookup"><span data-stu-id="48e8d-118">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="48e8d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="48e8d-119">See also</span></span>

- [<span data-ttu-id="48e8d-120">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="48e8d-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="48e8d-121">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="48e8d-121">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="48e8d-122">LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="48e8d-122">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="48e8d-123">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="48e8d-123">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="48e8d-124">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="48e8d-124">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
