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
ms.openlocfilehash: de649a7e1608e6a653f3280bfd5c4e52a3b661be
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078246"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="749df-102">orderby – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="749df-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="749df-103">Ve výrazu dotazu `orderby` klauzule způsobí, že vrácená sekvence nebo dílčí sekvenci (skupiny), který se má seřadit ve vzestupném nebo sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="749df-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="749df-104">Aby bylo možné provést jednu nebo více operací sekundární řazení lze zadat více klíčů.</span><span class="sxs-lookup"><span data-stu-id="749df-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="749df-105">Řazení se provádí pomocí výchozí porovnávací metody pro typ prvku.</span><span class="sxs-lookup"><span data-stu-id="749df-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="749df-106">Je výchozí pořadí řazení vzestupně.</span><span class="sxs-lookup"><span data-stu-id="749df-106">The default sort order is ascending.</span></span> <span data-ttu-id="749df-107">Můžete také určit vlastní porovnávací metody.</span><span class="sxs-lookup"><span data-stu-id="749df-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="749df-108">Je však pouze k dispozici pomocí syntaxe založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="749df-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="749df-109">Další informace najdete v tématu [řazení dat](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="749df-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="749df-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="749df-110">Example</span></span>

<span data-ttu-id="749df-111">V následujícím příkladu seřadí slova v abecedním pořadí A od prvního dotazu a druhý dotaz seřadí stejná slova v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="749df-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="749df-112">( `ascending` – Klíčové slovo je výchozí hodnota řazení a lze vynechat.)</span><span class="sxs-lookup"><span data-stu-id="749df-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="749df-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="749df-113">Example</span></span>

<span data-ttu-id="749df-114">Následující příklad provádí primární řazení podle příjmení studenty a sekundární řazení na jejich jména.</span><span class="sxs-lookup"><span data-stu-id="749df-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="749df-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="749df-115">Remarks</span></span>

<span data-ttu-id="749df-116">V době kompilace `orderby` přeložen na volání <xref:System.Linq.Enumerable.OrderBy%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="749df-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="749df-117">Více klíčů `orderby` klauzule přeložit do <xref:System.Linq.Enumerable.ThenBy%2A> volání metody.</span><span class="sxs-lookup"><span data-stu-id="749df-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="749df-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="749df-118">See also</span></span>

- [<span data-ttu-id="749df-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="749df-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="749df-120">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="749df-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="749df-121">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="749df-121">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="749df-122">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="749df-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="749df-123">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="749df-123">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)