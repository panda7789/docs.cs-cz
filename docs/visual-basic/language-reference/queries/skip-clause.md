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
ms.openlocfilehash: e52de186e1475bfabd02821a0cd2384d8350eed3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004764"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="c4796-102">Skip – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4796-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="c4796-103">Obchází zadaný počet prvků v kolekci a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="c4796-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4796-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4796-104">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="c4796-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c4796-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="c4796-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c4796-106">Required.</span></span> <span data-ttu-id="c4796-107">Hodnota nebo výraz, který se vyhodnotí na počet prvků sekvence, která se má přeskočit.</span><span class="sxs-lookup"><span data-stu-id="c4796-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4796-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4796-108">Remarks</span></span>  
 <span data-ttu-id="c4796-109">Klauzule `Skip` způsobí, že dotaz obchází prvky na začátku seznamu výsledků a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="c4796-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="c4796-110">Počet elementů, které mají být přeskočeny, je identifikován parametrem `count`.</span><span class="sxs-lookup"><span data-stu-id="c4796-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="c4796-111">Klauzuli `Skip` s klauzulí `Take` můžete použít k vrácení rozsahu dat z libovolného segmentu dotazu.</span><span class="sxs-lookup"><span data-stu-id="c4796-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="c4796-112">Provedete to tak, že předáte index prvního prvku rozsahu na klauzuli `Skip` a velikost rozsahu na klauzuli `Take`.</span><span class="sxs-lookup"><span data-stu-id="c4796-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="c4796-113">Použijete-li v dotazu klauzuli `Skip`, může být také nutné zajistit, aby výsledky byly vráceny v pořadí, které umožní, aby klauzule `Skip` využívala zamýšlené výsledky.</span><span class="sxs-lookup"><span data-stu-id="c4796-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="c4796-114">Další informace o řazení výsledků dotazu naleznete v tématu [ORDER by klauzule](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c4796-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="c4796-115">Pomocí klauzule `SkipWhile` můžete určit, že se v závislosti na zadané podmínce ignorují jenom určité prvky.</span><span class="sxs-lookup"><span data-stu-id="c4796-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4796-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4796-116">Example</span></span>  
 <span data-ttu-id="c4796-117">Následující příklad kódu používá klauzuli `Skip` spolu s klauzulí `Take` pro vrácení dat z dotazu na stránkách.</span><span class="sxs-lookup"><span data-stu-id="c4796-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="c4796-118">Funkce `GetCustomers` používá klauzuli `Skip` pro obejít zákazníky v seznamu do zadané hodnoty počátečního indexu a pomocí klauzule `Take` vrátí stránku zákazníků počínaje touto hodnotou indexu.</span><span class="sxs-lookup"><span data-stu-id="c4796-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c4796-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4796-119">See also</span></span>

- [<span data-ttu-id="c4796-120">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4796-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c4796-121">Dotazy</span><span class="sxs-lookup"><span data-stu-id="c4796-121">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="c4796-122">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="c4796-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="c4796-123">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="c4796-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="c4796-124">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="c4796-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="c4796-125">Klauzule Skip While</span><span class="sxs-lookup"><span data-stu-id="c4796-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="c4796-126">Klauzule Take</span><span class="sxs-lookup"><span data-stu-id="c4796-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
