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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e204612904aa55b4a0ae9aa65f2bbfd644bbc396
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="ce343-102">(Modulo) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="ce343-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="ce343-103">Vrátí zbytek rozdělené jiným jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="ce343-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce343-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce343-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="ce343-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ce343-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="ce343-106">Číselný výraz k rozdělení.</span><span class="sxs-lookup"><span data-stu-id="ce343-106">The numeric expression to divide.</span></span> <span data-ttu-id="ce343-107">`dividend`je jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="ce343-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="ce343-108">Číselný výraz k rozdělení dělenec podle.</span><span class="sxs-lookup"><span data-stu-id="ce343-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="ce343-109">`divisor`je jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="ce343-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ce343-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="ce343-110">Result Types</span></span>  
 <span data-ttu-id="ce343-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="ce343-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce343-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce343-112">Example</span></span>  
 <span data-ttu-id="ce343-113">Následující dotaz Entity SQL používá k vrácení zbytek jeden výraz rozdělené jiným aritmetického operátoru %.</span><span class="sxs-lookup"><span data-stu-id="ce343-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="ce343-114">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ce343-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ce343-115">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="ce343-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ce343-116">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ce343-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ce343-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="ce343-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="ce343-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce343-118">See Also</span></span>  
 [<span data-ttu-id="ce343-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ce343-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
