---
title: = (Rovná) (entita SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: bda314208a25426be321ba307be96067b1df2ac8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="f4874-102">= (Rovná) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="f4874-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="f4874-103">Porovnání rovnosti dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="f4874-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4874-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4874-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f4874-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f4874-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f4874-106">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="f4874-106">Any valid expression.</span></span> <span data-ttu-id="f4874-107">Oba výrazy musí mít implicitně převést datové typy.</span><span class="sxs-lookup"><span data-stu-id="f4874-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f4874-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="f4874-108">Result Types</span></span>  
 <span data-ttu-id="f4874-109">`true` Pokud levý výraz rovná pravý výraz; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="f4874-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4874-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4874-110">Remarks</span></span>  
 <span data-ttu-id="f4874-111">== Operátor je ekvivalentní =.</span><span class="sxs-lookup"><span data-stu-id="f4874-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4874-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4874-112">Example</span></span>  
 <span data-ttu-id="f4874-113">Následující dotaz Entity SQL používá = – operátor porovnání k porovnání rovnosti dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="f4874-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="f4874-114">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f4874-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f4874-115">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="f4874-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f4874-116">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f4874-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="f4874-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="f4874-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="f4874-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4874-118">See Also</span></span>  
 [<span data-ttu-id="f4874-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f4874-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
