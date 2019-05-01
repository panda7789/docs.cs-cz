---
title: Proměnná rozsahu <variable> skrývá proměnnou v nadřazeném bloku, dříve definovanou proměnnou rozsahu nebo implicitně deklarovanou proměnnou ve výrazu dotazu.
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: e31f728de228bea743f6c7b5cbfef3cd73367262
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971625"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="0c10e-102">Proměnná rozsahu \<proměnná > skrývá proměnnou v nadřízeném bloku, dříve definovanou proměnnou rozsahu nebo implicitně deklarovanou proměnnou ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="0c10e-102">Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="0c10e-103">Název proměnné rozsahu podle `Select`, `From`, `Aggregate`, nebo `Let` klauzule duplikuje název proměnné rozsahu již dříve zadaný v dotazu, nebo název proměnné, která je implicitně deklarován podle dotazu třeba na název pole nebo název agregační funkci.</span><span class="sxs-lookup"><span data-stu-id="0c10e-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="0c10e-104">**ID chyby:** BC36633</span><span class="sxs-lookup"><span data-stu-id="0c10e-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0c10e-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0c10e-105">To correct this error</span></span>  
  
- <span data-ttu-id="0c10e-106">Ujistěte se, že všechny proměnné rozsahu v oboru speciální dotaz mít jedinečné názvy.</span><span class="sxs-lookup"><span data-stu-id="0c10e-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="0c10e-107">Dotaz můžete uvést v závorkách k zajištění, že vnořené dotazy obsahovat jedinečný obor.</span><span class="sxs-lookup"><span data-stu-id="0c10e-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c10e-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c10e-108">See also</span></span>

- [<span data-ttu-id="0c10e-109">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0c10e-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="0c10e-110">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="0c10e-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="0c10e-111">Klauzule Let</span><span class="sxs-lookup"><span data-stu-id="0c10e-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="0c10e-112">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="0c10e-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="0c10e-113">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="0c10e-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
