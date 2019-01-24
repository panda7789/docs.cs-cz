---
title: Proměnná rozsahu &lt;proměnnou&gt; skrývá proměnnou v nadřízeném bloku, dříve definovanou proměnnou rozsahu nebo implicitně deklarovanou proměnnou ve výrazu dotazu
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: aef52ea912a4180a6505949c8077296628592c72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54748113"
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="ca067-102">Proměnná rozsahu &lt;proměnnou&gt; skrývá proměnnou v nadřízeném bloku, dříve definovanou proměnnou rozsahu nebo implicitně deklarovanou proměnnou ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="ca067-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="ca067-103">Název proměnné rozsahu podle `Select`, `From`, `Aggregate`, nebo `Let` klauzule duplikuje název proměnné rozsahu již dříve zadaný v dotazu, nebo název proměnné, která je implicitně deklarován podle dotazu třeba na název pole nebo název agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="ca067-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="ca067-104">**ID chyby:** BC36633</span><span class="sxs-lookup"><span data-stu-id="ca067-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ca067-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ca067-105">To correct this error</span></span>  
  
-   <span data-ttu-id="ca067-106">Ujistěte se, že všechny proměnné rozsahu v oboru speciální dotaz mít jedinečné názvy.</span><span class="sxs-lookup"><span data-stu-id="ca067-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="ca067-107">Dotaz můžete uvést v závorkách k zajištění, že vnořené dotazy obsahovat jedinečný obor.</span><span class="sxs-lookup"><span data-stu-id="ca067-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca067-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca067-108">See also</span></span>
- [<span data-ttu-id="ca067-109">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca067-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ca067-110">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="ca067-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="ca067-111">Klauzule Let</span><span class="sxs-lookup"><span data-stu-id="ca067-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="ca067-112">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="ca067-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="ca067-113">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="ca067-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
