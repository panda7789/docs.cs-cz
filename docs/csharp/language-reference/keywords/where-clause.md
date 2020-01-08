---
title: klauzule WHERE – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: f145811da2a90dd544b0590ad75af92b281884bc
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635883"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="07104-102">where – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="07104-102">where clause (C# Reference)</span></span>

<span data-ttu-id="07104-103">Klauzule `where` se používá ve výrazu dotazu k určení, které prvky ze zdroje dat budou vráceny ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="07104-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="07104-104">Aplikuje logickou podmínku (*predikát*) na každý zdrojový element (odkazovaný proměnnou rozsahu) a vrátí hodnoty, pro které je zadaná podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="07104-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="07104-105">Jeden výraz dotazu může obsahovat více klauzulí `where` a jedna klauzule může obsahovat více dílčích výrazů predikátu.</span><span class="sxs-lookup"><span data-stu-id="07104-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="07104-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="07104-106">Example</span></span>

<span data-ttu-id="07104-107">V následujícím příkladu vyfiltruje klauzule `where` všechny počty kromě těch, které jsou méně než pět.</span><span class="sxs-lookup"><span data-stu-id="07104-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="07104-108">Odeberete-li klauzuli `where`, bude vrácena veškerá čísla ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="07104-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="07104-109">Výraz `num < 5` je predikát, který je použit pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="07104-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="07104-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="07104-110">Example</span></span>

<span data-ttu-id="07104-111">V rámci jedné klauzule `where` můžete zadat libovolný počet predikátů podle potřeby pomocí operátorů [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) a [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="07104-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="07104-112">V následujícím příkladu dotaz určuje dva predikáty, aby bylo možné vybrat pouze sudá čísla, která jsou menší než pět.</span><span class="sxs-lookup"><span data-stu-id="07104-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="07104-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="07104-113">Example</span></span>

<span data-ttu-id="07104-114">Klauzule `where` může obsahovat jednu nebo více metod, které vracejí logické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="07104-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="07104-115">V následujícím příkladu klauzule `where` používá metodu k určení, zda je aktuální hodnota proměnné rozsahu sudá nebo lichá.</span><span class="sxs-lookup"><span data-stu-id="07104-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="07104-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07104-116">Remarks</span></span>

<span data-ttu-id="07104-117">Klauzule `where` je filtrovací mechanismus.</span><span class="sxs-lookup"><span data-stu-id="07104-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="07104-118">Může být umístěn skoro kdekoli ve výrazu dotazu, s výjimkou nemůže být první nebo poslední klauzule.</span><span class="sxs-lookup"><span data-stu-id="07104-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="07104-119">Klauzule `where` může být uvedena před nebo za klauzulí [Group](group-clause.md) v závislosti na tom, zda je nutné filtrovat zdrojové prvky před seskupením nebo po nich.</span><span class="sxs-lookup"><span data-stu-id="07104-119">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="07104-120">Pokud zadaný predikát není platný pro prvky ve zdroji dat, bude výsledkem chyba při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="07104-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="07104-121">Toto je jedna z výhod silné kontroly typu, kterou poskytuje LINQ.</span><span class="sxs-lookup"><span data-stu-id="07104-121">This is one benefit of the strong type-checking provided by LINQ.</span></span>

<span data-ttu-id="07104-122">V době kompilace je klíčové slovo `where` převedeno na volání metody operátoru dotazu <xref:System.Linq.Enumerable.Where%2A> Standard.</span><span class="sxs-lookup"><span data-stu-id="07104-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="07104-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07104-123">See also</span></span>

- [<span data-ttu-id="07104-124">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="07104-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="07104-125">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="07104-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="07104-126">select – klauzule</span><span class="sxs-lookup"><span data-stu-id="07104-126">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="07104-127">Filtrování dat</span><span class="sxs-lookup"><span data-stu-id="07104-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="07104-128">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="07104-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="07104-129">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="07104-129">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
