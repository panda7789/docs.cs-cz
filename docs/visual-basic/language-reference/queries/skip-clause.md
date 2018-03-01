---
title: "Skip – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508f3c094df4c834305bcb4a78223c1cee82b1c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="bbeff-102">Skip – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbeff-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="bbeff-103">Obchází zadaný počet elementů v kolekci a pak vrátí zbývající elementy.</span><span class="sxs-lookup"><span data-stu-id="bbeff-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbeff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbeff-104">Syntax</span></span>  
  
```  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="bbeff-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="bbeff-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="bbeff-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bbeff-106">Required.</span></span> <span data-ttu-id="bbeff-107">Hodnota nebo výraz, který se vyhodnotí jako počet elementů pořadí tak, aby přeskočil.</span><span class="sxs-lookup"><span data-stu-id="bbeff-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbeff-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbeff-108">Remarks</span></span>  
 <span data-ttu-id="bbeff-109">`Skip` Klauzule způsobí, že dotaz vynechat elementy na začátku seznamu výsledků a vrátíte se zbývající elementy.</span><span class="sxs-lookup"><span data-stu-id="bbeff-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="bbeff-110">Počet elementů tak, aby přeskočil je identifikována `count` parametr.</span><span class="sxs-lookup"><span data-stu-id="bbeff-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="bbeff-111">Můžete použít `Skip` klauzuli with `Take` klauzule vrátit celou řadu dat ze žádného segmentu dotazu.</span><span class="sxs-lookup"><span data-stu-id="bbeff-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="bbeff-112">K tomuto účelu předat index první prvek rozsahu `Skip` klauzule a velikost rozsahu `Take` klauzule.</span><span class="sxs-lookup"><span data-stu-id="bbeff-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="bbeff-113">Při použití `Skip` klauzuli v dotazu, může také musíte zajistit, že jsou vráceny v pořadí, které vám umožní `Skip` klauzule obejít požadovaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="bbeff-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="bbeff-114">Další informace o řazení výsledků dotazu, najdete v části [klauzuli ORDER by](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="bbeff-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="bbeff-115">Můžete použít `SkipWhile` klauzule k určení, že pouze některé prvky jsou ignorovány, v závislosti na podmínce zadaný.</span><span class="sxs-lookup"><span data-stu-id="bbeff-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbeff-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="bbeff-116">Example</span></span>  
 <span data-ttu-id="bbeff-117">Následující příklad kódu používá `Skip` klauzule společně s `Take` klauzule vrátit data z dotazu na stránkách.</span><span class="sxs-lookup"><span data-stu-id="bbeff-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="bbeff-118">`GetCustomers` Využívá `Skip` klauzule obejít zákazníků v seznamu, dokud zadaný počáteční index hodnota a používá `Take` klauzule vrátit na stránce zákazníků od tuto hodnotu indexu.</span><span class="sxs-lookup"><span data-stu-id="bbeff-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bbeff-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbeff-119">See Also</span></span>  
 [<span data-ttu-id="bbeff-120">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bbeff-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="bbeff-121">Dotazy</span><span class="sxs-lookup"><span data-stu-id="bbeff-121">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="bbeff-122">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="bbeff-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="bbeff-123">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="bbeff-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="bbeff-124">Order By – klauzule</span><span class="sxs-lookup"><span data-stu-id="bbeff-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="bbeff-125">Skip While – klauzule</span><span class="sxs-lookup"><span data-stu-id="bbeff-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="bbeff-126">Take – klauzule</span><span class="sxs-lookup"><span data-stu-id="bbeff-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
