---
title: "Take While – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c8add6c55bb9353bac3489e68f497cb32785aad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="d497f-102">Take While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d497f-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="d497f-103">Obsahuje prvky v kolekci, pokud je zadaná podmínka `true` a obchází zbývající elementy.</span><span class="sxs-lookup"><span data-stu-id="d497f-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d497f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d497f-104">Syntax</span></span>  
  
```  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d497f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d497f-105">Parts</span></span>  
  
|<span data-ttu-id="d497f-106">Termín</span><span class="sxs-lookup"><span data-stu-id="d497f-106">Term</span></span>|<span data-ttu-id="d497f-107">Definice</span><span class="sxs-lookup"><span data-stu-id="d497f-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="d497f-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d497f-108">Required.</span></span> <span data-ttu-id="d497f-109">Výraz, který představuje podmínku, kterou chcete testovat prvky pro.</span><span class="sxs-lookup"><span data-stu-id="d497f-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="d497f-110">Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, například `Integer` má být vyhodnocen jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d497f-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d497f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d497f-111">Remarks</span></span>  
 <span data-ttu-id="d497f-112">`Take While` Klauzule obsahuje prvky od začátku výsledku dotazu až do zadaných `expression` vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="d497f-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="d497f-113">Po `expression` vrátí `false`, dotaz se nepoužívat všechny zbývající elementy.</span><span class="sxs-lookup"><span data-stu-id="d497f-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="d497f-114">`expression` Pro zbývající výsledky se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="d497f-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="d497f-115">`Take While` Klauzule se liší od `Where` klauzule v tom, že `Where` klauzule lze zahrnout všechny elementy z dotazu, které splňují určitá podmínka.</span><span class="sxs-lookup"><span data-stu-id="d497f-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="d497f-116">`Take While` Klauzule obsahuje prvky pouze dokud poprvé, která není splněna podmínka.</span><span class="sxs-lookup"><span data-stu-id="d497f-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="d497f-117">`Take While` Klauzule je nejvhodnější pro práci se výsledek seřazené dotazu.</span><span class="sxs-lookup"><span data-stu-id="d497f-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d497f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d497f-118">Example</span></span>  
 <span data-ttu-id="d497f-119">Následující příklad kódu používá `Take While` klauzule a načtěte výsledky, dokud nebude nalezen první zákazníků bez jakékoli objednávky.</span><span class="sxs-lookup"><span data-stu-id="d497f-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d497f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d497f-120">See Also</span></span>  
 [<span data-ttu-id="d497f-121">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d497f-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="d497f-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="d497f-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="d497f-123">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="d497f-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="d497f-124">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="d497f-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="d497f-125">Take – klauzule</span><span class="sxs-lookup"><span data-stu-id="d497f-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="d497f-126">Skip While – klauzule</span><span class="sxs-lookup"><span data-stu-id="d497f-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="d497f-127">Kde – klauzule</span><span class="sxs-lookup"><span data-stu-id="d497f-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
