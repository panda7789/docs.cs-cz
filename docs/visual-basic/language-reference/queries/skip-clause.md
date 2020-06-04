---
title: Skip – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 427d14453260a54bd3f2ab9a8ac75dedacd291f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359655"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="37154-102">Skip – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37154-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="37154-103">Obchází zadaný počet prvků v kolekci a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="37154-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37154-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37154-104">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="37154-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="37154-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="37154-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="37154-106">Required.</span></span> <span data-ttu-id="37154-107">Hodnota nebo výraz, který se vyhodnotí na počet prvků sekvence, která se má přeskočit.</span><span class="sxs-lookup"><span data-stu-id="37154-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37154-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37154-108">Remarks</span></span>  
 <span data-ttu-id="37154-109">`Skip`Klauzule způsobí, že dotaz obchází prvky na začátku seznamu výsledků a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="37154-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="37154-110">Počet elementů, které mají být přeskočeny, je identifikován `count` parametrem.</span><span class="sxs-lookup"><span data-stu-id="37154-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="37154-111">`Skip`Klauzuli s klauzulí můžete použít `Take` k vrácení rozsahu dat z libovolného segmentu dotazu.</span><span class="sxs-lookup"><span data-stu-id="37154-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="37154-112">Provedete to tak, že předáte index prvního prvku rozsahu k `Skip` klauzuli a velikost rozsahu na `Take` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="37154-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="37154-113">Při použití `Skip` klauzule v dotazu může být také nutné zajistit, aby výsledky byly vráceny v pořadí, které umožní `Skip` klauzuli pro obejít zamýšlené výsledky.</span><span class="sxs-lookup"><span data-stu-id="37154-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="37154-114">Další informace o řazení výsledků dotazu naleznete v tématu [ORDER by klauzule](order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="37154-114">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="37154-115">Pomocí `SkipWhile` klauzule můžete určit, že se v závislosti na zadané podmínce mají ignorovat jenom určité prvky.</span><span class="sxs-lookup"><span data-stu-id="37154-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37154-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="37154-116">Example</span></span>  
 <span data-ttu-id="37154-117">Následující příklad kódu používá `Skip` klauzuli spolu s `Take` klauzulí k vrácení dat z dotazu na stránkách.</span><span class="sxs-lookup"><span data-stu-id="37154-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="37154-118">`GetCustomers`Funkce používá `Skip` klauzuli pro obejít zákazníky v seznamu až do zadané hodnoty počátečního indexu a pomocí `Take` klauzule vrátí stránku zákazníků počínaje touto hodnotou indexu.</span><span class="sxs-lookup"><span data-stu-id="37154-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="37154-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="37154-119">See also</span></span>

- [<span data-ttu-id="37154-120">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="37154-120">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="37154-121">Dotazy</span><span class="sxs-lookup"><span data-stu-id="37154-121">Queries</span></span>](index.md)
- [<span data-ttu-id="37154-122">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="37154-122">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="37154-123">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="37154-123">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="37154-124">Order By – klauzule</span><span class="sxs-lookup"><span data-stu-id="37154-124">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="37154-125">Skip While – klauzule</span><span class="sxs-lookup"><span data-stu-id="37154-125">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="37154-126">Take – klauzule</span><span class="sxs-lookup"><span data-stu-id="37154-126">Take Clause</span></span>](take-clause.md)
