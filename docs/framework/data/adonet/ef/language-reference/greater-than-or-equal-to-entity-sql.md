---
title: '>= (Je větší než nebo rovno) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 9e1d7e92097713ebdaf15523a5f99f98ed8be0b3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833748"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="5a5bf-102">> = (je větší než nebo rovno) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5a5bf-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="5a5bf-103">Porovná dva výrazy a určí, zda má levý výraz hodnotu větší nebo rovnu pravému výrazu.</span><span class="sxs-lookup"><span data-stu-id="5a5bf-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a5bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a5bf-104">Syntax</span></span>  
  
```sql  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5a5bf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5a5bf-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5a5bf-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="5a5bf-106">Any valid expression.</span></span> <span data-ttu-id="5a5bf-107">Oba výrazy musí mít implicitně převoditelné datové typy.</span><span class="sxs-lookup"><span data-stu-id="5a5bf-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5a5bf-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="5a5bf-108">Result Types</span></span>  
 <span data-ttu-id="5a5bf-109">`true`, pokud má levý výraz hodnotu větší nebo rovnou pravému výrazu; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="5a5bf-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5bf-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a5bf-110">Example</span></span>  
 <span data-ttu-id="5a5bf-111">Následující Entity SQL dotaz pomocí operátoru > = Compare Porovná dva výrazy a určí, zda má levý výraz hodnotu větší nebo rovnu pravému výrazu.</span><span class="sxs-lookup"><span data-stu-id="5a5bf-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="5a5bf-112">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5a5bf-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5a5bf-113">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="5a5bf-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5a5bf-114">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5a5bf-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5a5bf-115">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="5a5bf-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="5a5bf-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a5bf-116">See also</span></span>

- [<span data-ttu-id="5a5bf-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5a5bf-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
