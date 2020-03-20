---
title: = (Rovná se) (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 101dccd40e9197c7cf0795ccb80ded367676842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150309"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="e2184-102">= (Rovná se) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="e2184-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="e2184-103">Porovná rovnost dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="e2184-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2184-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2184-104">Syntax</span></span>  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e2184-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e2184-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e2184-106">Libovolný platný výraz</span><span class="sxs-lookup"><span data-stu-id="e2184-106">Any valid expression.</span></span> <span data-ttu-id="e2184-107">Oba výrazy musí mít implicitně konvertibilní datové typy.</span><span class="sxs-lookup"><span data-stu-id="e2184-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e2184-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="e2184-108">Result Types</span></span>  
 <span data-ttu-id="e2184-109">`true`pokud je levý výraz roven pravému výrazu; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="e2184-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2184-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2184-110">Remarks</span></span>  
 <span data-ttu-id="e2184-111">Operátor == je ekvivalentní =.</span><span class="sxs-lookup"><span data-stu-id="e2184-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2184-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2184-112">Example</span></span>  
 <span data-ttu-id="e2184-113">Následující entita SQL dotaz používá = operátor porovnání porovnat rovnost dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="e2184-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="e2184-114">Dotaz je založen na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="e2184-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e2184-115">Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="e2184-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e2184-116">Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e2184-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e2184-117">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="e2184-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="e2184-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2184-118">See also</span></span>

- [<span data-ttu-id="e2184-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e2184-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
