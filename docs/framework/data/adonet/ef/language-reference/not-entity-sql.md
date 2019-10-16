---
title: '! MĚNÍ (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 7755219c5238f78e59332c508643fe2ae1f5096f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319522"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="b7069-103">!</span><span class="sxs-lookup"><span data-stu-id="b7069-103">!</span></span> <span data-ttu-id="b7069-104">MĚNÍ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b7069-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="b7069-105">Negace výrazu `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b7069-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7069-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7069-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
``` 
  
## <a name="arguments"></a><span data-ttu-id="b7069-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="b7069-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="b7069-108">Libovolný platný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b7069-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7069-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7069-109">Remarks</span></span>  
 <span data-ttu-id="b7069-110">Vykřičník (!) má stejnou funkci jako operátor NOT.</span><span class="sxs-lookup"><span data-stu-id="b7069-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7069-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7069-111">Example</span></span>  
 <span data-ttu-id="b7069-112">Následující Entity SQL dotaz používá operátor NOT pro negaci výrazu `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b7069-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="b7069-113">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b7069-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b7069-114">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="b7069-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b7069-115">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b7069-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b7069-116">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="b7069-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="b7069-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7069-117">See also</span></span>

- [<span data-ttu-id="b7069-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b7069-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
