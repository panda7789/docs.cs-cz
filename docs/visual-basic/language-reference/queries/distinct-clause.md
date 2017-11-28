---
title: "Distinct – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ed92d5d601c1ec329728346ac881c4fa2bad8aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="9ed9f-102">Distinct – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ed9f-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="9ed9f-103">Omezuje hodnoty aktuální proměnnou rozsahu eliminovat duplicitní hodnoty v klauzulích následné dotazu.</span><span class="sxs-lookup"><span data-stu-id="9ed9f-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ed9f-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="9ed9f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ed9f-105">Remarks</span></span>  
 <span data-ttu-id="9ed9f-106">Můžete použít `Distinct` klauzule, která vrátí seznam jedinečných položek.</span><span class="sxs-lookup"><span data-stu-id="9ed9f-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="9ed9f-107">`Distinct` Klauzule způsobí, že dotaz ignoroval výsledky duplicitní dotazu.</span><span class="sxs-lookup"><span data-stu-id="9ed9f-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="9ed9f-108">`Distinct` Klauzule platí pro duplicitní hodnoty pro všechny vrátí pole určeného `Select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="9ed9f-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="9ed9f-109">Pokud žádné `Select` je zadána klauzule, `Distinct` klauzule se použije pro proměnnou rozsahu pro dotaz v identifikovat `From` klauzule.</span><span class="sxs-lookup"><span data-stu-id="9ed9f-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="9ed9f-110">Pokud proměnná rozsahu není typ nedá změnit, dotaz pouze ignorovat výsledku dotazu, pokud všechny členy typu odpovídají stávající výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="9ed9f-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ed9f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ed9f-111">Example</span></span>  
 <span data-ttu-id="9ed9f-112">Následující výraz dotazu spojí seznamu zákazníků a seznamu objednávek zákazníků.</span><span class="sxs-lookup"><span data-stu-id="9ed9f-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="9ed9f-113">`Distinct` Klauzule je součástí vrátí seznam jedinečných zákaznických názvy a pořadí kalendářní data.</span><span class="sxs-lookup"><span data-stu-id="9ed9f-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9ed9f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ed9f-114">See Also</span></span>  
 [<span data-ttu-id="9ed9f-115">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ed9f-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="9ed9f-116">Dotazy</span><span class="sxs-lookup"><span data-stu-id="9ed9f-116">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="9ed9f-117">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="9ed9f-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="9ed9f-118">Select – klauzule</span><span class="sxs-lookup"><span data-stu-id="9ed9f-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="9ed9f-119">Kde – klauzule</span><span class="sxs-lookup"><span data-stu-id="9ed9f-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
