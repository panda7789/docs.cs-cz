---
title: "Take – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ee289a24c15226126a526af116ed53b4a9055b35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="9abd5-102">Take – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9abd5-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="9abd5-103">Vrátí zadaný počet souvislý elementů od začátku kolekce.</span><span class="sxs-lookup"><span data-stu-id="9abd5-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9abd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9abd5-104">Syntax</span></span>  
  
```  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="9abd5-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9abd5-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="9abd5-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9abd5-106">Required.</span></span> <span data-ttu-id="9abd5-107">Hodnota nebo výraz, který se vyhodnotí jako počet elementů pořadí vrátit.</span><span class="sxs-lookup"><span data-stu-id="9abd5-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9abd5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9abd5-108">Remarks</span></span>  
 <span data-ttu-id="9abd5-109">`Take` Klauzule způsobí, že dotaz, který patří zadaný počet elementů souvislý od začátku seznamu výsledků.</span><span class="sxs-lookup"><span data-stu-id="9abd5-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="9abd5-110">Počet elementů zahrnout je zadána `count` parametr.</span><span class="sxs-lookup"><span data-stu-id="9abd5-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="9abd5-111">Můžete použít `Take` klauzuli with `Skip` klauzule vrátit celou řadu dat ze žádného segmentu dotazu.</span><span class="sxs-lookup"><span data-stu-id="9abd5-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="9abd5-112">K tomuto účelu předat index první prvek rozsahu `Skip` klauzule a velikost rozsahu `Take` klauzule.</span><span class="sxs-lookup"><span data-stu-id="9abd5-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="9abd5-113">V takovém případě `Take` klauzule musí být zadán za `Skip` klauzule.</span><span class="sxs-lookup"><span data-stu-id="9abd5-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="9abd5-114">Při použití `Take` klauzuli v dotazu, může také musíte zajistit, že jsou vráceny v pořadí, které vám umožní `Take` klauzule zahrnout požadovaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="9abd5-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="9abd5-115">Další informace o řazení výsledků dotazu, najdete v části [klauzuli ORDER by](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9abd5-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="9abd5-116">Můžete použít `TakeWhile` klauzule k určení, že se vrátí jenom některé prvky, v závislosti na podmínce zadaný.</span><span class="sxs-lookup"><span data-stu-id="9abd5-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9abd5-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="9abd5-117">Example</span></span>  
 <span data-ttu-id="9abd5-118">Následující příklad kódu používá `Take` klauzule společně s `Skip` klauzule vrátit data z dotazu na stránkách.</span><span class="sxs-lookup"><span data-stu-id="9abd5-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="9abd5-119">GetCustomers funkce používá `Skip` klauzule obejít zákazníků v seznamu, dokud zadaný počáteční index hodnota a používá `Take` klauzule vrátit na stránce zákazníků od tuto hodnotu indexu.</span><span class="sxs-lookup"><span data-stu-id="9abd5-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9abd5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9abd5-120">See Also</span></span>  
 [<span data-ttu-id="9abd5-121">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9abd5-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="9abd5-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="9abd5-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="9abd5-123">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="9abd5-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="9abd5-124">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="9abd5-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="9abd5-125">Order By – klauzule</span><span class="sxs-lookup"><span data-stu-id="9abd5-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="9abd5-126">Take While – klauzule</span><span class="sxs-lookup"><span data-stu-id="9abd5-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="9abd5-127">Skip – klauzule</span><span class="sxs-lookup"><span data-stu-id="9abd5-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
