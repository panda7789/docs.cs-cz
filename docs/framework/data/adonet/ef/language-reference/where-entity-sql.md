---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 8dd0e34a6669b2147052befb17b8f4ff8395aabc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248483"
---
# <a name="where-entity-sql"></a><span data-ttu-id="363a7-102">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="363a7-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="363a7-103">Klauzule WHERE je použita přímo za klauzulí [from](from-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="363a7-103">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="363a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="363a7-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="363a7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="363a7-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="363a7-106">Typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="363a7-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="363a7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="363a7-107">Remarks</span></span>  
 <span data-ttu-id="363a7-108">Klauzule WHERE má stejnou sémantiku, jak je popsáno v jazyce Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="363a7-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="363a7-109">Omezuje objekty, které jsou vyprodukovány výrazem dotazu, omezením prvků zdrojových kolekcí na ty, které podmínku přecházejí.</span><span class="sxs-lookup"><span data-stu-id="363a7-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="363a7-110">Výraz `e` musí být typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="363a7-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="363a7-111">Klauzule WHERE se aplikuje přímo za klauzulí FROM a předtím, než se provede jakékoli seskupení, řazení nebo projekce.</span><span class="sxs-lookup"><span data-stu-id="363a7-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="363a7-112">Všechny názvy elementů definované v klauzuli FROM jsou viditelné pro výraz klauzule WHERE.</span><span class="sxs-lookup"><span data-stu-id="363a7-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="363a7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="363a7-113">See also</span></span>

- [<span data-ttu-id="363a7-114">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="363a7-114">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="363a7-115">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="363a7-115">Query Expressions</span></span>](query-expressions-entity-sql.md)
