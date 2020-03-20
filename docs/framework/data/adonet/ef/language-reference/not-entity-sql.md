---
title: '! (NE) (Entita SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 0b69d4cb64adc1f9232631d50ec42af0d1ba47e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150126"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="06e05-103">!</span><span class="sxs-lookup"><span data-stu-id="06e05-103">!</span></span> <span data-ttu-id="06e05-104">(NE) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="06e05-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="06e05-105">Neguje `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="06e05-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06e05-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06e05-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a><span data-ttu-id="06e05-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="06e05-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="06e05-108">Libovolný platný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="06e05-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06e05-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06e05-109">Remarks</span></span>  
 <span data-ttu-id="06e05-110">Vykřičník (!) má stejné funkce jako operátor NOT.</span><span class="sxs-lookup"><span data-stu-id="06e05-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06e05-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="06e05-111">Example</span></span>  
 <span data-ttu-id="06e05-112">Následující dotaz ENTITY SQL používá operátor NOT `Boolean` k negování výrazu.</span><span class="sxs-lookup"><span data-stu-id="06e05-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="06e05-113">Dotaz je založen na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="06e05-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="06e05-114">Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="06e05-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="06e05-115">Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="06e05-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="06e05-116">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="06e05-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="06e05-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="06e05-117">See also</span></span>

- [<span data-ttu-id="06e05-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="06e05-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
