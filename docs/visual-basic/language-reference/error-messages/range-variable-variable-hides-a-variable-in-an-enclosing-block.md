---
title: Proměnná rozsahu <variable> skrývá proměnnou v nadřazeném bloku, dříve definovanou proměnnou rozsahu nebo implicitně deklarovanou proměnnou ve výrazu dotazu.
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 290ca81dea500558ed73956c91bdf7bfec312014
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400393"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="805ea-102">Proměnná rozsahu \<variable> skrývá proměnnou v nadřazeném bloku, dříve definovanou proměnnou rozsahu nebo implicitně deklarovanou proměnnou ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="805ea-102">Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="805ea-103">Název proměnné rozsahu zadaný v `Select` `From` klauzuli,, `Aggregate` nebo `Let` je duplicitní s názvem proměnné rozsahu, která je již v dotazu zadána dříve, nebo názvem proměnné, která je implicitně deklarována dotazem, jako je název pole nebo název agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="805ea-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="805ea-104">**ID chyby:** BC36633</span><span class="sxs-lookup"><span data-stu-id="805ea-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="805ea-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="805ea-105">To correct this error</span></span>  
  
- <span data-ttu-id="805ea-106">Ujistěte se, že všechny proměnné rozsahu v konkrétním oboru dotazu mají jedinečné názvy.</span><span class="sxs-lookup"><span data-stu-id="805ea-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="805ea-107">Dotaz můžete uzavřít do závorek, abyste zajistili, že vnořené dotazy mají jedinečný obor.</span><span class="sxs-lookup"><span data-stu-id="805ea-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="805ea-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="805ea-108">See also</span></span>

- [<span data-ttu-id="805ea-109">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="805ea-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="805ea-110">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="805ea-110">From Clause</span></span>](../queries/from-clause.md)
- [<span data-ttu-id="805ea-111">Let – klauzule</span><span class="sxs-lookup"><span data-stu-id="805ea-111">Let Clause</span></span>](../queries/let-clause.md)
- [<span data-ttu-id="805ea-112">Aggregate – klauzule</span><span class="sxs-lookup"><span data-stu-id="805ea-112">Aggregate Clause</span></span>](../queries/aggregate-clause.md)
- [<span data-ttu-id="805ea-113">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="805ea-113">Select Clause</span></span>](../queries/select-clause.md)
