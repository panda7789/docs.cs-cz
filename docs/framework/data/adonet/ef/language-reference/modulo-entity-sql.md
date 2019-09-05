---
title: (Modulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: a30306539d45c3718d2e948e9717997bbe2104fa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250087"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="e5dd6-102">(Modulo) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e5dd6-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="e5dd6-103">Vrátí zbytek jednoho výrazu děleného jiným.</span><span class="sxs-lookup"><span data-stu-id="e5dd6-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5dd6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5dd6-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="e5dd6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e5dd6-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="e5dd6-106">Číselný výraz, který se má rozdělit</span><span class="sxs-lookup"><span data-stu-id="e5dd6-106">The numeric expression to divide.</span></span> <span data-ttu-id="e5dd6-107">`dividend`je libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="e5dd6-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="e5dd6-108">Číselný výraz, podle kterého se má dělenec rozdělit.</span><span class="sxs-lookup"><span data-stu-id="e5dd6-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="e5dd6-109">`divisor`je libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="e5dd6-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e5dd6-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="e5dd6-110">Result Types</span></span>  
 <span data-ttu-id="e5dd6-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="e5dd6-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5dd6-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5dd6-112">Example</span></span>  
 <span data-ttu-id="e5dd6-113">Následující Entity SQL dotaz pomocí aritmetického operátoru% vrátí zbytek jednoho výrazu děleného jiným.</span><span class="sxs-lookup"><span data-stu-id="e5dd6-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="e5dd6-114">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e5dd6-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e5dd6-115">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="e5dd6-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e5dd6-116">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="e5dd6-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e5dd6-117">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="e5dd6-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="e5dd6-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5dd6-118">See also</span></span>

- [<span data-ttu-id="e5dd6-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e5dd6-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
