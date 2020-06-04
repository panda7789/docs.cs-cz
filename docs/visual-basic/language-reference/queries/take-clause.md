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
ms.openlocfilehash: 25dd06905525a96bc1504f033eb4f19af6d454a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359629"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="e6e86-102">Take – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6e86-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="e6e86-103">Vrátí zadaný počet souvislých prvků od začátku kolekce.</span><span class="sxs-lookup"><span data-stu-id="e6e86-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6e86-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="e6e86-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e6e86-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="e6e86-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="e6e86-106">Required.</span></span> <span data-ttu-id="e6e86-107">Hodnota nebo výraz, který se vyhodnotí na počet prvků sekvence, která se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="e6e86-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6e86-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6e86-108">Remarks</span></span>  
 <span data-ttu-id="e6e86-109">`Take`Klauzule způsobí, že dotaz zahrne zadaný počet souvislých prvků od začátku seznamu výsledků.</span><span class="sxs-lookup"><span data-stu-id="e6e86-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="e6e86-110">Počet prvků, které mají být zahrnuty, je určen `count` parametrem.</span><span class="sxs-lookup"><span data-stu-id="e6e86-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="e6e86-111">`Take`Klauzuli s klauzulí můžete použít `Skip` k vrácení rozsahu dat z libovolného segmentu dotazu.</span><span class="sxs-lookup"><span data-stu-id="e6e86-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="e6e86-112">Provedete to tak, že předáte index prvního prvku rozsahu k `Skip` klauzuli a velikost rozsahu na `Take` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e6e86-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="e6e86-113">V takovém případě `Take` musí být klauzule uvedena za `Skip` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="e6e86-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="e6e86-114">Použijete-li `Take` klauzuli v dotazu, může být také nutné zajistit, aby výsledky byly vráceny v pořadí, které umožní `Take` klauzuli zahrnout zamýšlené výsledky.</span><span class="sxs-lookup"><span data-stu-id="e6e86-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="e6e86-115">Další informace o řazení výsledků dotazu naleznete v tématu [ORDER by klauzule](order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e6e86-115">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="e6e86-116">Pomocí `TakeWhile` klauzule můžete určit, že se v závislosti na zadané podmínce mají vracet jenom určité prvky.</span><span class="sxs-lookup"><span data-stu-id="e6e86-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6e86-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6e86-117">Example</span></span>  
 <span data-ttu-id="e6e86-118">Následující příklad kódu používá `Take` klauzuli spolu s `Skip` klauzulí k vrácení dat z dotazu na stránkách.</span><span class="sxs-lookup"><span data-stu-id="e6e86-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="e6e86-119">Funkce GetCustomers používá `Skip` klauzuli pro obejít zákazníky v seznamu až do zadané hodnoty počátečního indexu a pomocí `Take` klauzule vrátí stránku zákazníků počínaje touto hodnotou indexu.</span><span class="sxs-lookup"><span data-stu-id="e6e86-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e6e86-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6e86-120">See also</span></span>

- [<span data-ttu-id="e6e86-121">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6e86-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="e6e86-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="e6e86-122">Queries</span></span>](index.md)
- [<span data-ttu-id="e6e86-123">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="e6e86-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="e6e86-124">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="e6e86-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="e6e86-125">Order By – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6e86-125">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="e6e86-126">Take While – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6e86-126">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="e6e86-127">Skip – klauzule</span><span class="sxs-lookup"><span data-stu-id="e6e86-127">Skip Clause</span></span>](skip-clause.md)
