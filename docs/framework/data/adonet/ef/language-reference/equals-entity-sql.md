---
title: = (Je rovno) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 5cdfd35450514a9699a39cf78f64c0fa6b7d5f39
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833842"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="156e0-102">= (Je rovno) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="156e0-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="156e0-103">Porovná rovnost dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="156e0-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="156e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="156e0-104">Syntax</span></span>  
  
```sql  
expression = expression  
-- or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="156e0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="156e0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="156e0-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="156e0-106">Any valid expression.</span></span> <span data-ttu-id="156e0-107">Oba výrazy musí mít implicitně převoditelné datové typy.</span><span class="sxs-lookup"><span data-stu-id="156e0-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="156e0-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="156e0-108">Result Types</span></span>  
 <span data-ttu-id="156e0-109">`true`, pokud je levý výraz roven pravému výrazu; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="156e0-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="156e0-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="156e0-110">Remarks</span></span>  
 <span data-ttu-id="156e0-111">Operátor = = je ekvivalentem =.</span><span class="sxs-lookup"><span data-stu-id="156e0-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="156e0-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="156e0-112">Example</span></span>  
 <span data-ttu-id="156e0-113">Následující Entity SQL dotaz používá operátor porovnání k porovnání rovnosti dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="156e0-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="156e0-114">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="156e0-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="156e0-115">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="156e0-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="156e0-116">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="156e0-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="156e0-117">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="156e0-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="156e0-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="156e0-118">See also</span></span>

- [<span data-ttu-id="156e0-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="156e0-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
