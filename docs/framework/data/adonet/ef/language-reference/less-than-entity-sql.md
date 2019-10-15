---
title: < (Méně než) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: fb3f4a1c6bc0df6af3c27836f7b53b2701776366
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319684"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="265b7-102">\< (méně než) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="265b7-102">\< (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="265b7-103">Porovná dva výrazy a určí, zda má levý výraz hodnotu menší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="265b7-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="265b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="265b7-104">Syntax</span></span>  
  
```sql  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="265b7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="265b7-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="265b7-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="265b7-106">Any valid expression.</span></span> <span data-ttu-id="265b7-107">Oba výrazy musí mít implicitně převoditelné datové typy.</span><span class="sxs-lookup"><span data-stu-id="265b7-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="265b7-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="265b7-108">Result Types</span></span>  
 <span data-ttu-id="265b7-109">`true`, pokud má levý výraz hodnotu menší než pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="265b7-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="265b7-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="265b7-110">Example</span></span>  
 <span data-ttu-id="265b7-111">Následující Entity SQL dotaz pomocí operátoru porovnání < Porovná dva výrazy a určí, zda má levý výraz hodnotu menší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="265b7-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="265b7-112">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="265b7-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="265b7-113">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="265b7-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="265b7-114">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="265b7-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="265b7-115">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="265b7-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="265b7-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="265b7-116">See also</span></span>

- [<span data-ttu-id="265b7-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="265b7-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
