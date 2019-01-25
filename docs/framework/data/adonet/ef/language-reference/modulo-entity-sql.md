---
title: (Modulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 543c35c56955fb0a9909fced23357444bc78197a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732593"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="d58e7-102">(Modulo) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d58e7-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="d58e7-103">Vrátí zbytek jeden výraz hodnotou druhého.</span><span class="sxs-lookup"><span data-stu-id="d58e7-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d58e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d58e7-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="d58e7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d58e7-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="d58e7-106">Číselný výraz, který se má dělit.</span><span class="sxs-lookup"><span data-stu-id="d58e7-106">The numeric expression to divide.</span></span> <span data-ttu-id="d58e7-107">`dividend` je libovolný platný výraz některou z číselných datových typů.</span><span class="sxs-lookup"><span data-stu-id="d58e7-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="d58e7-108">Číselný výraz, který se má dělit dělenec.</span><span class="sxs-lookup"><span data-stu-id="d58e7-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="d58e7-109">`divisor` je libovolný platný výraz některou z číselných datových typů.</span><span class="sxs-lookup"><span data-stu-id="d58e7-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d58e7-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="d58e7-110">Result Types</span></span>  
 <span data-ttu-id="d58e7-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="d58e7-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="d58e7-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d58e7-112">Example</span></span>  
 <span data-ttu-id="d58e7-113">Následující dotaz Entity SQL používá aritmetického operátoru % vrátit zbývající jeden výraz hodnotou druhého.</span><span class="sxs-lookup"><span data-stu-id="d58e7-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="d58e7-114">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d58e7-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d58e7-115">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="d58e7-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d58e7-116">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d58e7-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d58e7-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="d58e7-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="d58e7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d58e7-118">See also</span></span>
- [<span data-ttu-id="d58e7-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d58e7-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
