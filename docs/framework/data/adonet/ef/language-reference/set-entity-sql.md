---
title: Sada (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1378295cfa8e2563e56843c2e1dec89846bbf494
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="set-entity-sql"></a><span data-ttu-id="66db1-102">Sada (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="66db1-102">SET (Entity SQL)</span></span>
<span data-ttu-id="66db1-103">Výraz sady se používá k získávání novou kolekci s všechny elementy s duplicitním odebrat převést na kolekci objektů do sady.</span><span class="sxs-lookup"><span data-stu-id="66db1-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66db1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66db1-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="66db1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="66db1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="66db1-106">Jakýkoli platný dotaz výraz, která vrátí kolekci.</span><span class="sxs-lookup"><span data-stu-id="66db1-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66db1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66db1-107">Remarks</span></span>  
 <span data-ttu-id="66db1-108">Výraz sady `SET(c)` logicky odpovídá následující příkaz select:</span><span class="sxs-lookup"><span data-stu-id="66db1-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="66db1-109">`SET`patří mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="66db1-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="66db1-110">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="66db1-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="66db1-111">V tématu [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) přednost informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="66db1-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66db1-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="66db1-112">Example</span></span>  
 <span data-ttu-id="66db1-113">Následující dotaz Entity SQL používá pro převod na kolekci objektů do sady výraz sady.</span><span class="sxs-lookup"><span data-stu-id="66db1-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="66db1-114">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="66db1-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="66db1-115">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="66db1-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="66db1-116">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="66db1-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="66db1-117">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="66db1-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="66db1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="66db1-118">See Also</span></span>  
 [<span data-ttu-id="66db1-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="66db1-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
