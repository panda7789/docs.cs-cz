---
title: "Proměnná rozsahu &lt;proměnná&gt; skrývá proměnnou z vnějšího bloku, dříve definovaném rozsahu proměnná nebo proměnná implicitně deklarované ve výrazu dotazu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords: BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccbac48694a13daa09f2511cf39d5dbd51cdaaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="ff773-102">Proměnná rozsahu &lt;proměnná&gt; skrývá proměnnou z vnějšího bloku, dříve definovaném rozsahu proměnná nebo proměnná implicitně deklarované ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="ff773-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="ff773-103">Název proměnné rozsahu zadaný v `Select`, `From`, `Aggregate`, nebo `Let` klauzule duplikuje název proměnné rozsahu již dříve zadaný v dotazu nebo název proměnné, která je implicitně deklarován v dotazu jako název pole nebo název agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="ff773-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="ff773-104">**ID chyby:** BC36633</span><span class="sxs-lookup"><span data-stu-id="ff773-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ff773-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ff773-105">To correct this error</span></span>  
  
-   <span data-ttu-id="ff773-106">Zajistěte, aby všechny proměnné rozsahu v oboru konkrétní dotazu jedinečné názvy.</span><span class="sxs-lookup"><span data-stu-id="ff773-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="ff773-107">Dotaz můžete uveďte v závorkách, vnořené dotazy získali jedinečný obor.</span><span class="sxs-lookup"><span data-stu-id="ff773-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff773-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff773-108">See Also</span></span>  
 [<span data-ttu-id="ff773-109">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff773-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="ff773-110">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="ff773-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="ff773-111">Let – klauzule</span><span class="sxs-lookup"><span data-stu-id="ff773-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="ff773-112">AGGREGATE – klauzule</span><span class="sxs-lookup"><span data-stu-id="ff773-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="ff773-113">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="ff773-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
