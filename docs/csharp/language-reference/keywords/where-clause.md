---
title: kde klauzule - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 4b9a5169baa07f2b0363778afbea64ba34eee1d8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238663"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="3a6b5-102">where – klauzule (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3a6b5-102">where clause (C# Reference)</span></span>
<span data-ttu-id="3a6b5-103">`where` Klauzule se používá ve výrazu dotazu k určení, které elementy ze zdroje dat se vrátí ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="3a6b5-104">Použije se logická podmínka (*predikátu*) pro každý prvek zdroje (odkazuje proměnnou rozsahu) a vrátí těch, u kterých je zadaná podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="3a6b5-105">Výraz jeden dotaz může obsahovat více `where` klauzule a jedna klauzule může obsahovat několik dílčích výrazů predikátu.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a6b5-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a6b5-106">Example</span></span>  
 <span data-ttu-id="3a6b5-107">V následujícím příkladu `where` klauzule odfiltruje všechna čísla s výjimkou těch, které jsou méně než pět.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="3a6b5-108">Pokud odeberete `where` klauzule všechna čísla ve zdroji dat by vrátila.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="3a6b5-109">Výraz `num < 5` je predikát, který se použije na každý prvek.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="3a6b5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a6b5-110">Example</span></span>  
 <span data-ttu-id="3a6b5-111">V jednom `where` klauzule, podle potřeby můžete zadat libovolný počet predikátů s použitím [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) a [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operators.</span></span> <span data-ttu-id="3a6b5-112">V následujícím příkladu dotaz určuje dva predikáty abyste mohli vybrat pouze sudá čísla, které jsou méně než pět.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="3a6b5-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a6b5-113">Example</span></span>  
 <span data-ttu-id="3a6b5-114">A `where` klauzule může obsahovat jednu nebo více metod, které vracejí logické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="3a6b5-115">V následujícím příkladu `where` klauzule používá metodu k určení, zda je aktuální hodnota proměnné rozsahu sudý, nebo lichý.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="3a6b5-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a6b5-116">Remarks</span></span>  
 <span data-ttu-id="3a6b5-117">`where` Klauzule virtuálních sítí je mechanismus filtrování.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="3a6b5-118">To může být umístěné skoro kdekoli ve výrazu dotazu, s výjimkou nemůže být prvním nebo posledním klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="3a6b5-119">A `where` klauzule může být buď před, nebo po [skupiny](../../../csharp/language-reference/keywords/group-clause.md) klauzule v závislosti na tom, zda je třeba k filtrování zdrojové prvky před nebo po jsou seskupené.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-119">A `where` clause may appear either before or after a [group](../../../csharp/language-reference/keywords/group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>  
  
 <span data-ttu-id="3a6b5-120">Pokud zadaný predikát není platná pro elementy ve zdroji dat, způsobí chybu kompilace.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="3a6b5-121">Toto je jednou z výhod silné kontroly typů poskytované [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a6b5-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="3a6b5-122">V době kompilace `where` – klíčové slovo se převede na volání <xref:System.Linq.Enumerable.Where%2A> metody standardního operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="3a6b5-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a6b5-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a6b5-123">See Also</span></span>

- [<span data-ttu-id="3a6b5-124">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="3a6b5-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
- [<span data-ttu-id="3a6b5-125">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="3a6b5-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
- [<span data-ttu-id="3a6b5-126">select – klauzule</span><span class="sxs-lookup"><span data-stu-id="3a6b5-126">select clause</span></span>](../../../csharp/language-reference/keywords/select-clause.md)  
- [<span data-ttu-id="3a6b5-127">Filtrování dat</span><span class="sxs-lookup"><span data-stu-id="3a6b5-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)  
- [<span data-ttu-id="3a6b5-128">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="3a6b5-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="3a6b5-129">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3a6b5-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
