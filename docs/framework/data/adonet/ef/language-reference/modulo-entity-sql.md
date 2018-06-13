---
title: (Modulo) (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: ad7b76c1479906e9dcd875407e75475b55d5ae16
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764538"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="faef5-102">(Modulo) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="faef5-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="faef5-103">Vrátí zbytek rozdělené jiným jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="faef5-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faef5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faef5-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="faef5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="faef5-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="faef5-106">Číselný výraz k rozdělení.</span><span class="sxs-lookup"><span data-stu-id="faef5-106">The numeric expression to divide.</span></span> <span data-ttu-id="faef5-107">`dividend` je jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="faef5-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="faef5-108">Číselný výraz k rozdělení dělenec podle.</span><span class="sxs-lookup"><span data-stu-id="faef5-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="faef5-109">`divisor` je jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="faef5-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="faef5-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="faef5-110">Result Types</span></span>  
 <span data-ttu-id="faef5-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="faef5-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="faef5-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="faef5-112">Example</span></span>  
 <span data-ttu-id="faef5-113">Následující dotaz Entity SQL používá k vrácení zbytek jeden výraz rozdělené jiným aritmetického operátoru %.</span><span class="sxs-lookup"><span data-stu-id="faef5-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="faef5-114">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="faef5-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="faef5-115">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="faef5-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="faef5-116">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="faef5-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="faef5-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="faef5-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="faef5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="faef5-118">See Also</span></span>  
 [<span data-ttu-id="faef5-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="faef5-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
