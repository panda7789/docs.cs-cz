---
title: '> (Je větší než) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: f2d3a0ed81cf75b7e567dbd07e119629ea47ac69
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833774"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="08238-102">> (Je větší než) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="08238-102">> (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="08238-103">Porovná dva výrazy a určí, zda má levý výraz hodnotu větší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="08238-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08238-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08238-104">Syntax</span></span>  
  
```sql  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="08238-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="08238-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="08238-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="08238-106">Any valid expression.</span></span> <span data-ttu-id="08238-107">Oba výrazy musí mít implicitně převoditelné datové typy.</span><span class="sxs-lookup"><span data-stu-id="08238-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="08238-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="08238-108">Result Types</span></span>  
 <span data-ttu-id="08238-109">`true`, pokud má levý výraz hodnotu větší než pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="08238-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08238-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="08238-110">Example</span></span>  
 <span data-ttu-id="08238-111">Následující Entity SQL dotaz pomocí operátoru porovnání > Porovná dva výrazy a určí, zda má levý výraz hodnotu větší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="08238-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="08238-112">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="08238-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="08238-113">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="08238-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="08238-114">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="08238-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="08238-115">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="08238-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="08238-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08238-116">See also</span></span>

- [<span data-ttu-id="08238-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="08238-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
