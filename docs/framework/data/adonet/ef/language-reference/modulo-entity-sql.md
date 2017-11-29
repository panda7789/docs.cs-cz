---
title: (Modulo) (Entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cff0e4eaadf601b7a90f3caa0ecd9cf2f48feab0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="72917-102">(Modulo) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="72917-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="72917-103">Vrátí zbytek rozdělené jiným jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="72917-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72917-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72917-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="72917-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="72917-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="72917-106">Číselný výraz k rozdělení.</span><span class="sxs-lookup"><span data-stu-id="72917-106">The numeric expression to divide.</span></span> <span data-ttu-id="72917-107">`dividend`je jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="72917-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="72917-108">Číselný výraz k rozdělení dělenec podle.</span><span class="sxs-lookup"><span data-stu-id="72917-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="72917-109">`divisor`je jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="72917-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="72917-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="72917-110">Result Types</span></span>  
 <span data-ttu-id="72917-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="72917-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="72917-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="72917-112">Example</span></span>  
 <span data-ttu-id="72917-113">Následující dotaz Entity SQL používá k vrácení zbytek jeden výraz rozdělené jiným aritmetického operátoru %.</span><span class="sxs-lookup"><span data-stu-id="72917-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="72917-114">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="72917-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="72917-115">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="72917-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="72917-116">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="72917-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="72917-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="72917-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="72917-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="72917-118">See Also</span></span>  
 [<span data-ttu-id="72917-119">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="72917-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
