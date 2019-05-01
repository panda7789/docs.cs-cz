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
ms.openlocfilehash: cb109eaf43fee19b77ac690492b85919c9d78301
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054390"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="0eba3-102">Take – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0eba3-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="0eba3-103">Vrátí zadaný počet souvislých prvků od začátku kolekce.</span><span class="sxs-lookup"><span data-stu-id="0eba3-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eba3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0eba3-104">Syntax</span></span>  
  
```  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="0eba3-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0eba3-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="0eba3-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0eba3-106">Required.</span></span> <span data-ttu-id="0eba3-107">Hodnota nebo výraz, který se vyhodnotí jako počet elementů k vrácení sekvence.</span><span class="sxs-lookup"><span data-stu-id="0eba3-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0eba3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0eba3-108">Remarks</span></span>  
 <span data-ttu-id="0eba3-109">`Take` Klauzule způsobí, že dotaz pro přidání zadaný počet souvislých prvků od začátku seznamu výsledků.</span><span class="sxs-lookup"><span data-stu-id="0eba3-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="0eba3-110">Je určený počet prvků, které chcete zahrnout `count` parametru.</span><span class="sxs-lookup"><span data-stu-id="0eba3-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="0eba3-111">Můžete použít `Take` klauzule `Skip` klauzule, která vrátí celou řadu dat z libovolnou část dotazu.</span><span class="sxs-lookup"><span data-stu-id="0eba3-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="0eba3-112">K tomuto účelu předat index prvního prvku rozsahu, který chcete `Skip` klauzule a velikost rozsahu `Take` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0eba3-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="0eba3-113">V takovém případě `Take` klauzule musí být zadán za `Skip` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0eba3-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="0eba3-114">Při použití `Take` klauzule v dotazu, budete také muset zajistit, že výsledky jsou vráceny v pořadí, které vám umožní `Take` klauzule, která zahrnují požadovaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="0eba3-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="0eba3-115">Další informace o řazení výsledků dotazu, naleznete v tématu [klauzuli ORDER by](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0eba3-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="0eba3-116">Můžete použít `TakeWhile` klauzule k určení, že se vrátí jenom některé prvky, v závislosti na zadaných podmínek.</span><span class="sxs-lookup"><span data-stu-id="0eba3-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eba3-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="0eba3-117">Example</span></span>  
 <span data-ttu-id="0eba3-118">Následující příklad kódu používá `Take` klauzule spolu s `Skip` klauzule vrátit data z dotazu na stránkách.</span><span class="sxs-lookup"><span data-stu-id="0eba3-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="0eba3-119">GetCustomers funkce používá `Skip` klauzule obejít zákazníky v seznamu, dokud se zadaný počáteční index, hodnotu a použití `Take` klauzuli pro vrácení stránky s zákazníků od hodnotě indexu.</span><span class="sxs-lookup"><span data-stu-id="0eba3-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0eba3-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0eba3-120">See also</span></span>

- [<span data-ttu-id="0eba3-121">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0eba3-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="0eba3-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="0eba3-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="0eba3-123">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="0eba3-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="0eba3-124">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="0eba3-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="0eba3-125">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="0eba3-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="0eba3-126">Klauzule Take While</span><span class="sxs-lookup"><span data-stu-id="0eba3-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="0eba3-127">Klauzule Skip</span><span class="sxs-lookup"><span data-stu-id="0eba3-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
