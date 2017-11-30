---
title: "Where – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8c2572f513d00bc72e869cf28d382be799f7a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="1473f-102">Where – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1473f-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="1473f-103">Určuje podmínku filtrování pro dotaz.</span><span class="sxs-lookup"><span data-stu-id="1473f-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1473f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1473f-104">Syntax</span></span>  
  
```  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="1473f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1473f-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="1473f-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1473f-106">Required.</span></span> <span data-ttu-id="1473f-107">Výraz, který určuje, zda hodnoty pro aktuální položku v kolekci jsou zahrnuty v kolekci výstup.</span><span class="sxs-lookup"><span data-stu-id="1473f-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="1473f-108">Výraz se musí vyhodnotit `Boolean` hodnotu nebo ekvivalent `Boolean` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1473f-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="1473f-109">Pokud je podmínka vyhodnocena jako `True`elementu je zahrnutý ve výsledku dotazu jinak, element je vyloučen z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="1473f-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1473f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1473f-110">Remarks</span></span>  
 <span data-ttu-id="1473f-111">`Where` Klauzule vám umožní filtrovat dotaz na data tak, že vyberete pouze elementy, které splňují určitá kritéria.</span><span class="sxs-lookup"><span data-stu-id="1473f-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="1473f-112">Elementy, jejichž hodnoty způsobit `Where` klauzule vyhodnocení `True` jsou zahrnuty do výsledku dotazu; další elementy jsou vyloučeny.</span><span class="sxs-lookup"><span data-stu-id="1473f-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="1473f-113">Výraz, který se používá v `Where` klauzule se musí vyhodnotit `Boolean` nebo ekvivalent `Boolean`, například celé číslo, jehož výsledkem `False` při jeho hodnota může být nula.</span><span class="sxs-lookup"><span data-stu-id="1473f-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="1473f-114">Můžete kombinovat více výrazů v `Where` klauzule pomocí logických operátorů, například `And`, `Or`, `AndAlso`, `OrElse`, `Is`, a `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="1473f-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="1473f-115">Ve výchozím nastavení, nejsou vyhodnotí výrazy dotazu, dokud jsou přístupná – například když jsou vázané na data nebo vstupní prostřednictvím `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="1473f-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="1473f-116">V důsledku toho `Where` klauzule není vyhodnocen, dokud dotaz přistupuje.</span><span class="sxs-lookup"><span data-stu-id="1473f-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="1473f-117">Pokud máte hodnoty externí do dotazu, které se používají v `Where` klauzule, ujistěte se, že příslušná hodnota se používá `Where` klauzule v době spustit dotaz.</span><span class="sxs-lookup"><span data-stu-id="1473f-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="1473f-118">Další informace o provádění dotazů najdete v tématu [zápis vaše první dotaz LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="1473f-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="1473f-119">Můžete volat funkce v rámci `Where` klauzule k provedení výpočtu nebo operaci na hodnotu z aktuálního elementu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="1473f-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="1473f-120">Volání funkce v `Where` klauzule může způsobit dotaz spustit okamžitě, když je definována místo při přístupu.</span><span class="sxs-lookup"><span data-stu-id="1473f-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="1473f-121">Další informace o provádění dotazů najdete v tématu [zápis vaše první dotaz LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="1473f-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1473f-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="1473f-122">Example</span></span>  
 <span data-ttu-id="1473f-123">Následující dotaz výraz používá `From` klauzule deklarovat proměnnou rozsahu `cust` pro každou `Customer` objekt v `customers` kolekce.</span><span class="sxs-lookup"><span data-stu-id="1473f-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="1473f-124">`Where` Klauzule používá proměnnou rozsahu omezit výstupu na zákazníky ze zadané oblasti.</span><span class="sxs-lookup"><span data-stu-id="1473f-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="1473f-125">`For Each` Smyčky zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="1473f-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="1473f-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="1473f-126">Example</span></span>  
 <span data-ttu-id="1473f-127">Následující příklad používá `And` a `Or` logické operátory při `Where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="1473f-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1473f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="1473f-128">See Also</span></span>  
 [<span data-ttu-id="1473f-129">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1473f-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="1473f-130">Dotazy</span><span class="sxs-lookup"><span data-stu-id="1473f-130">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="1473f-131">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="1473f-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="1473f-132">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="1473f-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="1473f-133">Pro každou... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="1473f-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
