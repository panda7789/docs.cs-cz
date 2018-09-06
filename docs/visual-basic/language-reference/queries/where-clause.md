---
title: Where – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: de7b4bf3e7dc1145b7e95197c7bd05c66acdabd6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43859433"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="e0339-102">Where – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0339-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="e0339-103">Určuje podmínku filtrování dotazu.</span><span class="sxs-lookup"><span data-stu-id="e0339-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0339-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0339-104">Syntax</span></span>  
  
```  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="e0339-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e0339-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="e0339-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e0339-106">Required.</span></span> <span data-ttu-id="e0339-107">Výraz, který určuje, zda hodnoty pro aktuální položku v kolekci jsou zahrnuty v kolekci výstup.</span><span class="sxs-lookup"><span data-stu-id="e0339-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="e0339-108">Výraz se musí vyhodnotit na `Boolean` hodnotu nebo ekvivalent `Boolean` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e0339-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="e0339-109">Pokud je podmínka vyhodnocena jako `True`elementu je zahrnut ve výsledku dotazu; jinak vrátí hodnotu, elementu je vyloučen z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="e0339-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0339-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0339-110">Remarks</span></span>  
 <span data-ttu-id="e0339-111">`Where` Klauzule umožňuje filtrovat dotaz na data tak, že vyberete pouze prvky, které splňují určitá kritéria.</span><span class="sxs-lookup"><span data-stu-id="e0339-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="e0339-112">Elementy způsobovat jehož hodnoty `Where` klauzule vyhodnotilo `True` jsou zahrnuty ve výsledku dotazu; další prvky jsou vyloučeny.</span><span class="sxs-lookup"><span data-stu-id="e0339-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="e0339-113">Výraz, který se používá v `Where` klauzule se musí vyhodnotit na `Boolean` nebo ekvivalent `Boolean`, například celé číslo, které se vyhodnotí jako `False` když jeho hodnota je nula.</span><span class="sxs-lookup"><span data-stu-id="e0339-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="e0339-114">Můžete zkombinovat více výrazů v `Where` klauzule pomocí logických operátorů `And`, `Or`, `AndAlso`, `OrElse`, `Is`, a `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="e0339-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="e0339-115">Ve výchozím nastavení, se nevyhodnocují – výrazy dotazů, dokud jsou přístupné – například když jsou vázané na data nebo v iterovaném prostřednictvím `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="e0339-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="e0339-116">V důsledku toho `Where` klauzule není vyhodnocen, dokud dotaz přistupuje.</span><span class="sxs-lookup"><span data-stu-id="e0339-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="e0339-117">Pokud máte hodnoty pro dotaz, který se používají v externí `Where` klauzule, zajistit, aby používal odpovídající hodnotu v `Where` klauzule v době spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="e0339-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="e0339-118">Další informace o provádění dotazů, najdete v části [zápis svůj první dotaz LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="e0339-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="e0339-119">Bude možné volat funkce v rámci `Where` k provedení výpočtu nebo operace na základě hodnot z aktuální prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e0339-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="e0339-120">Volání funkce `Where` klauzule může způsobit provedení okamžitě, když je definována místo při přístupu k dotazu.</span><span class="sxs-lookup"><span data-stu-id="e0339-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="e0339-121">Další informace o provádění dotazů, najdete v části [zápis svůj první dotaz LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="e0339-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0339-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0339-122">Example</span></span>  
 <span data-ttu-id="e0339-123">Následující dotaz používá výraz `From` klauzule k deklaraci proměnné rozsahu `cust` pro každou `Customer` objekt `customers` kolekce.</span><span class="sxs-lookup"><span data-stu-id="e0339-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="e0339-124">`Where` Klauzule používá proměnnou rozsahu omezení výstup pro zákazníky ze zadané oblasti.</span><span class="sxs-lookup"><span data-stu-id="e0339-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="e0339-125">`For Each` Smyčky zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="e0339-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="e0339-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0339-126">Example</span></span>  
 <span data-ttu-id="e0339-127">Následující příklad používá `And` a `Or` logické operátory při `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e0339-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e0339-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0339-128">See Also</span></span>  
 [<span data-ttu-id="e0339-129">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e0339-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="e0339-130">Dotazy</span><span class="sxs-lookup"><span data-stu-id="e0339-130">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="e0339-131">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="e0339-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="e0339-132">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="e0339-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="e0339-133">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="e0339-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
