---
title: "Skip While – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f447a6d9b2eb58fa546ced6c96b987caf68fb3e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="d653d-102">Skip While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d653d-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="d653d-103">Obchází elementů v kolekci, pokud je zadaná podmínka `true` a vrátí zbývající elementy.</span><span class="sxs-lookup"><span data-stu-id="d653d-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d653d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d653d-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d653d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d653d-105">Parts</span></span>  
  
|<span data-ttu-id="d653d-106">Termín</span><span class="sxs-lookup"><span data-stu-id="d653d-106">Term</span></span>|<span data-ttu-id="d653d-107">Definice</span><span class="sxs-lookup"><span data-stu-id="d653d-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="d653d-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d653d-108">Required.</span></span> <span data-ttu-id="d653d-109">Výraz, který představuje podmínku, kterou chcete testovat prvky pro.</span><span class="sxs-lookup"><span data-stu-id="d653d-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="d653d-110">Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, například `Integer` má být vyhodnocen jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d653d-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d653d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d653d-111">Remarks</span></span>  
 <span data-ttu-id="d653d-112">`Skip While` Klauzule obchází elementy od začátku až do zadaných výsledků dotazu `expression` vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="d653d-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="d653d-113">Po `expression` vrátí `false`, dotaz vrátí všechny zbývající elementy.</span><span class="sxs-lookup"><span data-stu-id="d653d-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="d653d-114">`expression` Pro zbývající výsledky se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="d653d-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="d653d-115">`Skip While` Klauzule se liší od `Where` klauzule v tom, že `Where` klauzuli lze použít k vyloučení všechny elementy z dotazu, které nesplňují určité podmínky.</span><span class="sxs-lookup"><span data-stu-id="d653d-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="d653d-116">`Skip While` Klauzule vyloučí elementy pouze dokud poprvé, která není splněna podmínka.</span><span class="sxs-lookup"><span data-stu-id="d653d-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="d653d-117">`Skip While` Klauzule je nejvhodnější pro práci se výsledek seřazené dotazu.</span><span class="sxs-lookup"><span data-stu-id="d653d-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="d653d-118">Můžete obejít konkrétní počet výsledků od začátku výsledků dotazu pomocí `Skip` klauzule.</span><span class="sxs-lookup"><span data-stu-id="d653d-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d653d-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="d653d-119">Example</span></span>  
 <span data-ttu-id="d653d-120">Následující příklad kódu používá `Skip While` klauzule obejít výsledky, dokud nebude nalezen první zákazník z USA.</span><span class="sxs-lookup"><span data-stu-id="d653d-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d653d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d653d-121">See Also</span></span>  
 [<span data-ttu-id="d653d-122">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d653d-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="d653d-123">Dotazy</span><span class="sxs-lookup"><span data-stu-id="d653d-123">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="d653d-124">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="d653d-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="d653d-125">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="d653d-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="d653d-126">Skip – klauzule</span><span class="sxs-lookup"><span data-stu-id="d653d-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="d653d-127">Take While – klauzule</span><span class="sxs-lookup"><span data-stu-id="d653d-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="d653d-128">Kde – klauzule</span><span class="sxs-lookup"><span data-stu-id="d653d-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
