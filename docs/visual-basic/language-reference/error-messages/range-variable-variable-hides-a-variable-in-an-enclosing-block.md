---
title: Proměnná rozsahu &lt;proměnná&gt; skrývá proměnnou z vnějšího bloku, dříve definovaném rozsahu proměnná nebo proměnná implicitně deklarované ve výrazu dotazu
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: f02533cf7cb79c34e5bb5a6d445aaef7ab0e86da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593123"
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="9b95b-102">Proměnná rozsahu &lt;proměnná&gt; skrývá proměnnou z vnějšího bloku, dříve definovaném rozsahu proměnná nebo proměnná implicitně deklarované ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="9b95b-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="9b95b-103">Název proměnné rozsahu zadaný v `Select`, `From`, `Aggregate`, nebo `Let` klauzule duplikuje název proměnné rozsahu již dříve zadaný v dotazu nebo název proměnné, která je implicitně deklarován v dotazu jako název pole nebo název agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="9b95b-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="9b95b-104">**ID chyby:** BC36633</span><span class="sxs-lookup"><span data-stu-id="9b95b-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9b95b-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9b95b-105">To correct this error</span></span>  
  
-   <span data-ttu-id="9b95b-106">Zajistěte, aby všechny proměnné rozsahu v oboru konkrétní dotazu jedinečné názvy.</span><span class="sxs-lookup"><span data-stu-id="9b95b-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="9b95b-107">Dotaz můžete uveďte v závorkách, vnořené dotazy získali jedinečný obor.</span><span class="sxs-lookup"><span data-stu-id="9b95b-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b95b-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b95b-108">See Also</span></span>  
 [<span data-ttu-id="9b95b-109">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b95b-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="9b95b-110">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="9b95b-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="9b95b-111">Klauzule Let</span><span class="sxs-lookup"><span data-stu-id="9b95b-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="9b95b-112">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="9b95b-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="9b95b-113">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="9b95b-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
