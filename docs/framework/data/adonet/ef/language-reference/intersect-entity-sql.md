---
title: INTERSECT (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 38814d3f4e8bca6a3a20d14c41d7674a205e30d2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="774eb-102">INTERSECT (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="774eb-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="774eb-103">Vrátí kolekci všech jedinečných hodnot, které jsou vráceny ve výrazech dotazů na levé straně a pravé straně operandu INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="774eb-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="774eb-104">Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="774eb-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="774eb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="774eb-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="774eb-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="774eb-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="774eb-107">Libovolný platný dotaz výraz, který vrátí kolekce k porovnání s kolekcí vrácená z jiného výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="774eb-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="774eb-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="774eb-108">Return Value</span></span>  
 <span data-ttu-id="774eb-109">Kolekce stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="774eb-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="774eb-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="774eb-110">Remarks</span></span>  
 <span data-ttu-id="774eb-111">INTERSECT je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="774eb-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="774eb-112">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="774eb-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="774eb-113">Priorita informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavení operátory najdete [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="774eb-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="774eb-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="774eb-114">Example</span></span>  
 <span data-ttu-id="774eb-115">Následující dotaz Entity SQL pomocí operátoru INTERSECT vrátí kolekci všech jedinečných hodnot, které jsou vráceny ve výrazech dotazů na levé straně a pravé straně operandu INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="774eb-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="774eb-116">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="774eb-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="774eb-117">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="774eb-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="774eb-118">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="774eb-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="774eb-119">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="774eb-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="774eb-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="774eb-120">See Also</span></span>  
 [<span data-ttu-id="774eb-121">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="774eb-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
