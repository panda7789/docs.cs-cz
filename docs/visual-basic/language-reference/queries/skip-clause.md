---
title: Skip – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 1810bf4a6573c6fa36f1d8149bf341d45cfd6f52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602824"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="31cb9-102">Skip – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31cb9-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="31cb9-103">Obchází zadaný počet elementů v kolekci a pak vrátí zbývající elementy.</span><span class="sxs-lookup"><span data-stu-id="31cb9-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31cb9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31cb9-104">Syntax</span></span>  
  
```  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="31cb9-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="31cb9-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="31cb9-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="31cb9-106">Required.</span></span> <span data-ttu-id="31cb9-107">Hodnota nebo výraz, který se vyhodnotí jako počet elementů pořadí tak, aby přeskočil.</span><span class="sxs-lookup"><span data-stu-id="31cb9-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31cb9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31cb9-108">Remarks</span></span>  
 <span data-ttu-id="31cb9-109">`Skip` Klauzule způsobí, že dotaz vynechat elementy na začátku seznamu výsledků a vrátíte se zbývající elementy.</span><span class="sxs-lookup"><span data-stu-id="31cb9-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="31cb9-110">Počet elementů tak, aby přeskočil je identifikována `count` parametr.</span><span class="sxs-lookup"><span data-stu-id="31cb9-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="31cb9-111">Můžete použít `Skip` klauzuli with `Take` klauzule vrátit celou řadu dat ze žádného segmentu dotazu.</span><span class="sxs-lookup"><span data-stu-id="31cb9-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="31cb9-112">K tomuto účelu předat index první prvek rozsahu `Skip` klauzule a velikost rozsahu `Take` klauzule.</span><span class="sxs-lookup"><span data-stu-id="31cb9-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="31cb9-113">Při použití `Skip` klauzuli v dotazu, může také musíte zajistit, že jsou vráceny v pořadí, které vám umožní `Skip` klauzule obejít požadovaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="31cb9-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="31cb9-114">Další informace o řazení výsledků dotazu, najdete v části [klauzuli ORDER by](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="31cb9-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="31cb9-115">Můžete použít `SkipWhile` klauzule k určení, že pouze některé prvky jsou ignorovány, v závislosti na podmínce zadaný.</span><span class="sxs-lookup"><span data-stu-id="31cb9-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31cb9-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="31cb9-116">Example</span></span>  
 <span data-ttu-id="31cb9-117">Následující příklad kódu používá `Skip` klauzule společně s `Take` klauzule vrátit data z dotazu na stránkách.</span><span class="sxs-lookup"><span data-stu-id="31cb9-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="31cb9-118">`GetCustomers` Využívá `Skip` klauzule obejít zákazníků v seznamu, dokud zadaný počáteční index hodnota a používá `Take` klauzule vrátit na stránce zákazníků od tuto hodnotu indexu.</span><span class="sxs-lookup"><span data-stu-id="31cb9-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="31cb9-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="31cb9-119">See Also</span></span>  
 [<span data-ttu-id="31cb9-120">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31cb9-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="31cb9-121">Dotazy</span><span class="sxs-lookup"><span data-stu-id="31cb9-121">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="31cb9-122">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="31cb9-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="31cb9-123">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="31cb9-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="31cb9-124">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="31cb9-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="31cb9-125">Klauzule Skip While</span><span class="sxs-lookup"><span data-stu-id="31cb9-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="31cb9-126">Klauzule Take</span><span class="sxs-lookup"><span data-stu-id="31cb9-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
