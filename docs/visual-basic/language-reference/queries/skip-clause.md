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
ms.openlocfilehash: 53fc47c7dd26142d2ead49178afefe2775a96580
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543143"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="57057-102">Skip – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57057-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="57057-103">Vynechá zadaný počet prvků v kolekci a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="57057-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57057-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57057-104">Syntax</span></span>  
  
```  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="57057-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="57057-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="57057-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="57057-106">Required.</span></span> <span data-ttu-id="57057-107">Hodnota nebo výraz, který se vyhodnotí jako počet elementů pořadí přeskočit.</span><span class="sxs-lookup"><span data-stu-id="57057-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57057-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57057-108">Remarks</span></span>  
 <span data-ttu-id="57057-109">`Skip` Klauzule způsobí, že dotaz obejít prvky na začátek seznamu výsledků a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="57057-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="57057-110">Počet prvků, které mají přeskočit je identifikován `count` parametru.</span><span class="sxs-lookup"><span data-stu-id="57057-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="57057-111">Můžete použít `Skip` klauzule `Take` klauzule, která vrátí celou řadu dat z libovolnou část dotazu.</span><span class="sxs-lookup"><span data-stu-id="57057-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="57057-112">K tomuto účelu předat index prvního prvku rozsahu, který chcete `Skip` klauzule a velikost rozsahu `Take` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="57057-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="57057-113">Při použití `Skip` klauzule v dotazu, budete také muset zajistit, že výsledky jsou vráceny v pořadí, které vám umožní `Skip` klauzule obejít požadovaných výsledků.</span><span class="sxs-lookup"><span data-stu-id="57057-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="57057-114">Další informace o řazení výsledků dotazu, naleznete v tématu [klauzuli ORDER by](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="57057-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="57057-115">Můžete použít `SkipWhile` klauzule k určení, že pouze některé prvky jsou ignorovány, v závislosti na zadaných podmínek.</span><span class="sxs-lookup"><span data-stu-id="57057-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57057-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="57057-116">Example</span></span>  
 <span data-ttu-id="57057-117">Následující příklad kódu používá `Skip` klauzule spolu s `Take` klauzule vrátit data z dotazu na stránkách.</span><span class="sxs-lookup"><span data-stu-id="57057-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="57057-118">`GetCustomers` Funkce používá `Skip` klauzule obejít zákazníky v seznamu, dokud se zadaný počáteční index, hodnotu a použití `Take` klauzuli pro vrácení stránky s zákazníků od hodnotě indexu.</span><span class="sxs-lookup"><span data-stu-id="57057-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="57057-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57057-119">See also</span></span>
- [<span data-ttu-id="57057-120">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57057-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="57057-121">Dotazy</span><span class="sxs-lookup"><span data-stu-id="57057-121">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="57057-122">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="57057-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="57057-123">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="57057-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="57057-124">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="57057-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="57057-125">Klauzule Skip While</span><span class="sxs-lookup"><span data-stu-id="57057-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="57057-126">Klauzule Take</span><span class="sxs-lookup"><span data-stu-id="57057-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
