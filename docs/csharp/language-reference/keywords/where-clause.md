---
description: Where – klauzule – reference jazyka C#
title: Where – klauzule – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 58a8dc226bb2720b6a8251f028712a80f74e893c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141683"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="4b72f-103">where – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4b72f-103">where clause (C# Reference)</span></span>

<span data-ttu-id="4b72f-104">`where`Klauzule je použita ve výrazu dotazu k určení, které prvky ze zdroje dat budou vráceny ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="4b72f-104">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="4b72f-105">Aplikuje logickou podmínku (*predikát*) na každý zdrojový element (odkazovaný proměnnou rozsahu) a vrátí hodnoty, pro které je zadaná podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="4b72f-105">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="4b72f-106">Jeden výraz dotazu může obsahovat více `where` klauzulí a jedna klauzule může obsahovat více dílčích výrazů predikátu.</span><span class="sxs-lookup"><span data-stu-id="4b72f-106">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="4b72f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b72f-107">Example</span></span>

<span data-ttu-id="4b72f-108">V následujícím příkladu `where` klauzule filtruje všechna čísla kromě těch, které jsou méně než pět.</span><span class="sxs-lookup"><span data-stu-id="4b72f-108">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="4b72f-109">Při odebrání klauzule se `where` vrátí všechna čísla ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="4b72f-109">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="4b72f-110">Výraz `num < 5` je predikát, který je použit pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="4b72f-110">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="4b72f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b72f-111">Example</span></span>

<span data-ttu-id="4b72f-112">V rámci jedné `where` klauzule můžete zadat libovolný počet predikátů podle potřeby pomocí [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) operátorů a [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="4b72f-112">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="4b72f-113">V následujícím příkladu dotaz určuje dva predikáty, aby bylo možné vybrat pouze sudá čísla, která jsou menší než pět.</span><span class="sxs-lookup"><span data-stu-id="4b72f-113">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="4b72f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b72f-114">Example</span></span>

<span data-ttu-id="4b72f-115">`where`Klauzule může obsahovat jednu nebo více metod, které vracejí logické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4b72f-115">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="4b72f-116">V následujícím příkladu `where` klauzule používá metodu k určení, zda je aktuální hodnota proměnné rozsahu sudá nebo lichá.</span><span class="sxs-lookup"><span data-stu-id="4b72f-116">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="4b72f-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b72f-117">Remarks</span></span>

<span data-ttu-id="4b72f-118">`where`Klauzule je filtrovací mechanismus.</span><span class="sxs-lookup"><span data-stu-id="4b72f-118">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="4b72f-119">Může být umístěn skoro kdekoli ve výrazu dotazu, s výjimkou nemůže být první nebo poslední klauzule.</span><span class="sxs-lookup"><span data-stu-id="4b72f-119">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="4b72f-120">`where`Klauzule může být uvedena před nebo po klauzuli [skupiny](group-clause.md) v závislosti na tom, zda je nutné filtrovat zdrojové prvky před nebo po seskupení.</span><span class="sxs-lookup"><span data-stu-id="4b72f-120">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="4b72f-121">Pokud zadaný predikát není platný pro prvky ve zdroji dat, bude výsledkem chyba při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="4b72f-121">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="4b72f-122">Toto je jedna z výhod silné kontroly typu, kterou poskytuje LINQ.</span><span class="sxs-lookup"><span data-stu-id="4b72f-122">This is one benefit of the strong type-checking provided by LINQ.</span></span>

<span data-ttu-id="4b72f-123">V době kompilace se `where` klíčové slovo převede na volání <xref:System.Linq.Enumerable.Where%2A> standardní metody operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="4b72f-123">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b72f-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b72f-124">See also</span></span>

- [<span data-ttu-id="4b72f-125">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="4b72f-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="4b72f-126">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="4b72f-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="4b72f-127">select – klauzule (C#)</span><span class="sxs-lookup"><span data-stu-id="4b72f-127">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="4b72f-128">Filtrování dat</span><span class="sxs-lookup"><span data-stu-id="4b72f-128">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="4b72f-129">LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="4b72f-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="4b72f-130">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="4b72f-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
