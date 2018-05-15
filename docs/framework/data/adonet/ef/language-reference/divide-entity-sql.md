---
title: '- (Dělení) (Entita SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 506553de78ce9fbdf5f3710805906ee8cd5b8757
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="8a8dc-102">/ (Dělení) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="8a8dc-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="8a8dc-103">Vydělí jedno číslo jiným.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a8dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a8dc-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="8a8dc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8a8dc-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="8a8dc-106">Číselný výraz k rozdělení.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-106">The numeric expression to divide.</span></span> <span data-ttu-id="8a8dc-107">`dividend` je jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="8a8dc-108">Číselný výraz k rozdělení dělenec podle.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="8a8dc-109">`divisor` je jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8a8dc-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="8a8dc-110">Result Types</span></span>  
 <span data-ttu-id="8a8dc-111">Datový typ, který je výsledkem implicitní typ povýšením dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="8a8dc-112">Další informace o povýšení implicitní typ najdete v tématu [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8a8dc-112">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a8dc-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a8dc-113">Example</span></span>  
 <span data-ttu-id="8a8dc-114">Následující dotaz Entity SQL používá / aritmetické operátor rozdělit jeden kontrolních jiným.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-114">The following Entity SQL query uses the / arithmetic operator to divide one numer by another.</span></span> <span data-ttu-id="8a8dc-115">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8a8dc-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8a8dc-116">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="8a8dc-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8a8dc-117">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8a8dc-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="8a8dc-118">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="8a8dc-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="8a8dc-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a8dc-119">See Also</span></span>  
 [<span data-ttu-id="8a8dc-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8a8dc-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
