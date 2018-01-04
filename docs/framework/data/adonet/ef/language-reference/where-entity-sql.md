---
title: KDE (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2ad170500770bc370eb67a04ab29d0c9f9dcaabd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="where-entity-sql"></a><span data-ttu-id="969fb-102">KDE (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="969fb-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="969fb-103">Přímo po použití klauzule WHERE [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) klauzule.</span><span class="sxs-lookup"><span data-stu-id="969fb-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="969fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="969fb-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="969fb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="969fb-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="969fb-106">Typem logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="969fb-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="969fb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="969fb-107">Remarks</span></span>  
 <span data-ttu-id="969fb-108">Klauzule WHERE obsahuje stejnou sémantiku, jak je popsáno pro [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="969fb-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="969fb-109">Omezuje objekty vyprodukované výrazu dotazu omezením elementy kolekcí zdroje na ty, které předat podmínku.</span><span class="sxs-lookup"><span data-stu-id="969fb-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="969fb-110">Výraz `e` musí být typu logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="969fb-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="969fb-111">Klauzule WHERE se použije přímo po klauzuli FROM a před jakoukoli seskupení, řazení nebo projekce probíhá.</span><span class="sxs-lookup"><span data-stu-id="969fb-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="969fb-112">Všechny názvy elementů, které jsou definované v klauzuli FROM jsou viditelné pro výraz klauzule WHERE.</span><span class="sxs-lookup"><span data-stu-id="969fb-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="969fb-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="969fb-113">See Also</span></span>  
 [<span data-ttu-id="969fb-114">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="969fb-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="969fb-115">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="969fb-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
