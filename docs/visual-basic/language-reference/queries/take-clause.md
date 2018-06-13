---
title: Take – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 0dddb411af1b4ee269e091c07553a94589d90b2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604026"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="4b933-102">Take – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b933-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="4b933-103">Vrátí zadaný počet souvislý elementů od začátku kolekce.</span><span class="sxs-lookup"><span data-stu-id="4b933-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b933-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b933-104">Syntax</span></span>  
  
```  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="4b933-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4b933-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="4b933-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4b933-106">Required.</span></span> <span data-ttu-id="4b933-107">Hodnota nebo výraz, který se vyhodnotí jako počet elementů pořadí vrátit.</span><span class="sxs-lookup"><span data-stu-id="4b933-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b933-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b933-108">Remarks</span></span>  
 <span data-ttu-id="4b933-109">`Take` Klauzule způsobí, že dotaz, který patří zadaný počet elementů souvislý od začátku seznamu výsledků.</span><span class="sxs-lookup"><span data-stu-id="4b933-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="4b933-110">Počet elementů zahrnout je zadána `count` parametr.</span><span class="sxs-lookup"><span data-stu-id="4b933-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="4b933-111">Můžete použít `Take` klauzuli with `Skip` klauzule vrátit celou řadu dat ze žádného segmentu dotazu.</span><span class="sxs-lookup"><span data-stu-id="4b933-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="4b933-112">K tomuto účelu předat index první prvek rozsahu `Skip` klauzule a velikost rozsahu `Take` klauzule.</span><span class="sxs-lookup"><span data-stu-id="4b933-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="4b933-113">V takovém případě `Take` klauzule musí být zadán za `Skip` klauzule.</span><span class="sxs-lookup"><span data-stu-id="4b933-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="4b933-114">Při použití `Take` klauzuli v dotazu, může také musíte zajistit, že jsou vráceny v pořadí, které vám umožní `Take` klauzule zahrnout požadovaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="4b933-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="4b933-115">Další informace o řazení výsledků dotazu, najdete v části [klauzuli ORDER by](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4b933-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="4b933-116">Můžete použít `TakeWhile` klauzule k určení, že se vrátí jenom některé prvky, v závislosti na podmínce zadaný.</span><span class="sxs-lookup"><span data-stu-id="4b933-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b933-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b933-117">Example</span></span>  
 <span data-ttu-id="4b933-118">Následující příklad kódu používá `Take` klauzule společně s `Skip` klauzule vrátit data z dotazu na stránkách.</span><span class="sxs-lookup"><span data-stu-id="4b933-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="4b933-119">GetCustomers funkce používá `Skip` klauzule obejít zákazníků v seznamu, dokud zadaný počáteční index hodnota a používá `Take` klauzule vrátit na stránce zákazníků od tuto hodnotu indexu.</span><span class="sxs-lookup"><span data-stu-id="4b933-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4b933-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b933-120">See Also</span></span>  
 [<span data-ttu-id="4b933-121">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b933-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="4b933-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="4b933-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="4b933-123">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="4b933-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="4b933-124">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="4b933-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="4b933-125">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="4b933-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="4b933-126">Klauzule Take While</span><span class="sxs-lookup"><span data-stu-id="4b933-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="4b933-127">Klauzule Skip</span><span class="sxs-lookup"><span data-stu-id="4b933-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
