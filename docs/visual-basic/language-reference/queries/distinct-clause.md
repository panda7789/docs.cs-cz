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
ms.openlocfilehash: fbca9fa8aa227d8d5b6488bef179f4bda08bb38c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830055"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="13abe-102">Distinct – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13abe-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="13abe-103">Omezí hodnoty aktuální proměnnou rozsahu eliminovaly duplicitní hodnoty v klauzulích následné dotazování.</span><span class="sxs-lookup"><span data-stu-id="13abe-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13abe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13abe-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="13abe-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13abe-105">Remarks</span></span>  
 <span data-ttu-id="13abe-106">Můžete použít `Distinct` klauzule, která vrátí seznam jedinečných položek.</span><span class="sxs-lookup"><span data-stu-id="13abe-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="13abe-107">`Distinct` Klauzule způsobí, že dotaz ignorovat duplicitní dotaz výsledky.</span><span class="sxs-lookup"><span data-stu-id="13abe-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="13abe-108">`Distinct` Klauzule platí pro duplicitní hodnoty pro všechny vrátí pole určená `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="13abe-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="13abe-109">Pokud ne `Select` není zadána klauzule `Distinct` klauzule platí pro proměnnou rozsahu uvedené v dotazu `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="13abe-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="13abe-110">Pokud proměnná rozsahu není neumlčitelným typem, dotaz pouze ignorovat výsledku dotazu, pokud všechny členy typu odpovídají existující výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="13abe-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13abe-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="13abe-111">Example</span></span>  
 <span data-ttu-id="13abe-112">Následující výraz dotaz spojí seznam zákazníků a seznam objednávek zákazníků.</span><span class="sxs-lookup"><span data-stu-id="13abe-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="13abe-113">`Distinct` Klauzule je součástí a vrátí seznam jedinečných zákaznických názvy a pořadí data.</span><span class="sxs-lookup"><span data-stu-id="13abe-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="13abe-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13abe-114">See also</span></span>

- [<span data-ttu-id="13abe-115">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13abe-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="13abe-116">Dotazy</span><span class="sxs-lookup"><span data-stu-id="13abe-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="13abe-117">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="13abe-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="13abe-118">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="13abe-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="13abe-119">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="13abe-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
