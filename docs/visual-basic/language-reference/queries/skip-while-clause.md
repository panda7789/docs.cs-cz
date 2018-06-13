---
title: Skip While – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 9d95dc4a9f61a9ec3a50f9d594b31d673c2d3764
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602016"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="43c64-102">Skip While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43c64-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="43c64-103">Obchází elementů v kolekci, pokud je zadaná podmínka `true` a vrátí zbývající elementy.</span><span class="sxs-lookup"><span data-stu-id="43c64-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43c64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43c64-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="43c64-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="43c64-105">Parts</span></span>  
  
|<span data-ttu-id="43c64-106">Termín</span><span class="sxs-lookup"><span data-stu-id="43c64-106">Term</span></span>|<span data-ttu-id="43c64-107">Definice</span><span class="sxs-lookup"><span data-stu-id="43c64-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="43c64-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="43c64-108">Required.</span></span> <span data-ttu-id="43c64-109">Výraz, který představuje podmínku, kterou chcete testovat prvky pro.</span><span class="sxs-lookup"><span data-stu-id="43c64-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="43c64-110">Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, například `Integer` má být vyhodnocen jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="43c64-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43c64-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43c64-111">Remarks</span></span>  
 <span data-ttu-id="43c64-112">`Skip While` Klauzule obchází elementy od začátku až do zadaných výsledků dotazu `expression` vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="43c64-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="43c64-113">Po `expression` vrátí `false`, dotaz vrátí všechny zbývající elementy.</span><span class="sxs-lookup"><span data-stu-id="43c64-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="43c64-114">`expression` Pro zbývající výsledky se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="43c64-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="43c64-115">`Skip While` Klauzule se liší od `Where` klauzule v tom, že `Where` klauzuli lze použít k vyloučení všechny elementy z dotazu, které nesplňují určité podmínky.</span><span class="sxs-lookup"><span data-stu-id="43c64-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="43c64-116">`Skip While` Klauzule vyloučí elementy pouze dokud poprvé, která není splněna podmínka.</span><span class="sxs-lookup"><span data-stu-id="43c64-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="43c64-117">`Skip While` Klauzule je nejvhodnější pro práci se výsledek seřazené dotazu.</span><span class="sxs-lookup"><span data-stu-id="43c64-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="43c64-118">Můžete obejít konkrétní počet výsledků od začátku výsledků dotazu pomocí `Skip` klauzule.</span><span class="sxs-lookup"><span data-stu-id="43c64-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43c64-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="43c64-119">Example</span></span>  
 <span data-ttu-id="43c64-120">Následující příklad kódu používá `Skip While` klauzule obejít výsledky, dokud nebude nalezen první zákazník z USA.</span><span class="sxs-lookup"><span data-stu-id="43c64-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="43c64-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="43c64-121">See Also</span></span>  
 [<span data-ttu-id="43c64-122">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43c64-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="43c64-123">Dotazy</span><span class="sxs-lookup"><span data-stu-id="43c64-123">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="43c64-124">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="43c64-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="43c64-125">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="43c64-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="43c64-126">Klauzule Skip</span><span class="sxs-lookup"><span data-stu-id="43c64-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="43c64-127">Klauzule Take While</span><span class="sxs-lookup"><span data-stu-id="43c64-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="43c64-128">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="43c64-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
