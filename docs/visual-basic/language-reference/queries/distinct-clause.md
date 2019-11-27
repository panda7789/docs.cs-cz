---
title: Distinct – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 94471898807ef4552564c3e01465f2b2f6211d0c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335376"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="313e5-102">Distinct – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="313e5-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="313e5-103">Omezuje hodnoty aktuální proměnné rozsahu tak, aby v následných klauzulích dotazu vyloučily duplicitní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="313e5-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="313e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="313e5-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="313e5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="313e5-105">Remarks</span></span>  
 <span data-ttu-id="313e5-106">Klauzuli `Distinct` můžete použít k vrácení seznamu jedinečných položek.</span><span class="sxs-lookup"><span data-stu-id="313e5-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="313e5-107">Klauzule `Distinct` způsobí, že dotaz ignoruje výsledky duplicitních dotazů.</span><span class="sxs-lookup"><span data-stu-id="313e5-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="313e5-108">Klauzule `Distinct` se vztahuje na duplicitní hodnoty všech vrácených polí určených klauzulí `Select`.</span><span class="sxs-lookup"><span data-stu-id="313e5-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="313e5-109">Není-li zadána žádná klauzule `Select`, je použita klauzule `Distinct` na proměnnou rozsahu pro dotaz identifikovaný v klauzuli `From`.</span><span class="sxs-lookup"><span data-stu-id="313e5-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="313e5-110">Pokud proměnná rozsahu není neměnný typ, dotaz bude ignorovat výsledek dotazu pouze v případě, že všichni členové typu odpovídají existujícímu výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="313e5-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="313e5-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="313e5-111">Example</span></span>  
 <span data-ttu-id="313e5-112">Následující výraz dotazu spojuje seznam zákazníků a seznam objednávek zákazníků.</span><span class="sxs-lookup"><span data-stu-id="313e5-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="313e5-113">K dispozici je klauzule `Distinct`, která vrátí seznam jedinečných názvů zákazníků a data objednávky.</span><span class="sxs-lookup"><span data-stu-id="313e5-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="313e5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="313e5-114">See also</span></span>

- [<span data-ttu-id="313e5-115">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="313e5-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="313e5-116">Dotazy</span><span class="sxs-lookup"><span data-stu-id="313e5-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="313e5-117">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="313e5-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="313e5-118">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="313e5-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="313e5-119">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="313e5-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
