---
title: Distinct – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 18d09d8018303aab6a69801c84c7ec9c6ea19ca9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788620"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="d6223-102">Distinct – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6223-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="d6223-103">Omezí hodnoty aktuální proměnnou rozsahu eliminovaly duplicitní hodnoty v klauzulích následné dotazování.</span><span class="sxs-lookup"><span data-stu-id="d6223-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6223-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6223-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="d6223-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6223-105">Remarks</span></span>  
 <span data-ttu-id="d6223-106">Můžete použít `Distinct` klauzule, která vrátí seznam jedinečných položek.</span><span class="sxs-lookup"><span data-stu-id="d6223-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="d6223-107">`Distinct` Klauzule způsobí, že dotaz ignorovat duplicitní dotaz výsledky.</span><span class="sxs-lookup"><span data-stu-id="d6223-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="d6223-108">`Distinct` Klauzule platí pro duplicitní hodnoty pro všechny vrátí pole určená `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d6223-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="d6223-109">Pokud ne `Select` není zadána klauzule `Distinct` klauzule platí pro proměnnou rozsahu uvedené v dotazu `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d6223-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="d6223-110">Pokud proměnná rozsahu není neumlčitelným typem, dotaz pouze ignorovat výsledku dotazu, pokud všechny členy typu odpovídají existující výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="d6223-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6223-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6223-111">Example</span></span>  
 <span data-ttu-id="d6223-112">Následující výraz dotaz spojí seznam zákazníků a seznam objednávek zákazníků.</span><span class="sxs-lookup"><span data-stu-id="d6223-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="d6223-113">`Distinct` Klauzule je součástí a vrátí seznam jedinečných zákaznických názvy a pořadí data.</span><span class="sxs-lookup"><span data-stu-id="d6223-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d6223-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6223-114">See Also</span></span>  
 [<span data-ttu-id="d6223-115">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6223-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="d6223-116">Dotazy</span><span class="sxs-lookup"><span data-stu-id="d6223-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="d6223-117">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="d6223-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="d6223-118">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="d6223-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="d6223-119">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="d6223-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
