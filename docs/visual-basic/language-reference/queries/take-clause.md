---
title: Take – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 3082954ef84560ccb70f7a47cd3532f622829392
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349636"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="55e99-102">Take – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55e99-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="55e99-103">Vrátí zadaný počet souvislých prvků od začátku kolekce.</span><span class="sxs-lookup"><span data-stu-id="55e99-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55e99-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="55e99-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="55e99-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="55e99-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="55e99-106">Required.</span></span> <span data-ttu-id="55e99-107">Hodnota nebo výraz, který se vyhodnotí na počet prvků sekvence, která se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="55e99-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55e99-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55e99-108">Remarks</span></span>  
 <span data-ttu-id="55e99-109">Klauzule `Take` způsobí, že dotaz zahrne zadaný počet souvislých prvků od začátku seznamu výsledků.</span><span class="sxs-lookup"><span data-stu-id="55e99-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="55e99-110">Počet prvků, které mají být zahrnuty, je určen parametrem `count`.</span><span class="sxs-lookup"><span data-stu-id="55e99-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="55e99-111">Klauzuli `Take` s klauzulí `Skip` můžete použít k vrácení rozsahu dat z libovolného segmentu dotazu.</span><span class="sxs-lookup"><span data-stu-id="55e99-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="55e99-112">Provedete to tak, že předáte index prvního prvku rozsahu na klauzuli `Skip` a velikost rozsahu na klauzuli `Take`.</span><span class="sxs-lookup"><span data-stu-id="55e99-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="55e99-113">V tomto případě je nutné zadat klauzuli `Take` za klauzulí `Skip`.</span><span class="sxs-lookup"><span data-stu-id="55e99-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="55e99-114">Použijete-li v dotazu klauzuli `Take`, může být také nutné zajistit, aby výsledky byly vráceny v pořadí, ve kterém bude povolena klauzule `Take`, aby zahrnovala zamýšlené výsledky.</span><span class="sxs-lookup"><span data-stu-id="55e99-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="55e99-115">Další informace o řazení výsledků dotazu naleznete v tématu [ORDER by klauzule](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="55e99-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="55e99-116">Pomocí klauzule `TakeWhile` můžete určit, že se v závislosti na zadané podmínce mají vracet jenom určité prvky.</span><span class="sxs-lookup"><span data-stu-id="55e99-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55e99-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="55e99-117">Example</span></span>  
 <span data-ttu-id="55e99-118">Následující příklad kódu používá klauzuli `Take` spolu s klauzulí `Skip`, která vrací data z dotazu na stránkách.</span><span class="sxs-lookup"><span data-stu-id="55e99-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="55e99-119">Funkce GetCustomers používá klauzuli `Skip` pro obejít zákazníky v seznamu až do zadané hodnoty počátečního indexu a pomocí klauzule `Take` vracet stránku zákazníků počínaje touto hodnotou indexu.</span><span class="sxs-lookup"><span data-stu-id="55e99-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="55e99-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55e99-120">See also</span></span>

- [<span data-ttu-id="55e99-121">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55e99-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="55e99-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="55e99-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="55e99-123">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="55e99-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="55e99-124">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="55e99-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="55e99-125">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="55e99-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="55e99-126">Klauzule Take While</span><span class="sxs-lookup"><span data-stu-id="55e99-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="55e99-127">Klauzule Skip</span><span class="sxs-lookup"><span data-stu-id="55e99-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
