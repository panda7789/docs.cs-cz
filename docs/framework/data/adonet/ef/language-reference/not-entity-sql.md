---
title: '! (NE) (Entita SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f2f8df14df3c4e330af20ff3691cbf266bb95da0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="-not-entity-sql"></a><span data-ttu-id="e5efd-103">!</span><span class="sxs-lookup"><span data-stu-id="e5efd-103">!</span></span> <span data-ttu-id="e5efd-104">(NE) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="e5efd-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="e5efd-105">Neguje `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="e5efd-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5efd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5efd-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e5efd-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="e5efd-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="e5efd-108">Jakýkoli platný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e5efd-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5efd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5efd-109">Remarks</span></span>  
 <span data-ttu-id="e5efd-110">Vykřičník (!) má stejné funkce jako operátor NOT.</span><span class="sxs-lookup"><span data-stu-id="e5efd-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5efd-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5efd-111">Example</span></span>  
 <span data-ttu-id="e5efd-112">Následující dotaz Entity SQL Neguje pomocí operátoru NOT `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="e5efd-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="e5efd-113">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e5efd-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e5efd-114">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="e5efd-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e5efd-115">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e5efd-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e5efd-116">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="e5efd-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="e5efd-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5efd-117">See Also</span></span>  
 [<span data-ttu-id="e5efd-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e5efd-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
