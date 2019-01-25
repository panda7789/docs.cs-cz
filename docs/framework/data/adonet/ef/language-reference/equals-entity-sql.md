---
title: = (Rovná se) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 2791bc0940bad92208c5bdce3659534f237bd6e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551875"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="0fc25-102">= (Rovná se) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0fc25-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="0fc25-103">Porovná rovnost dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="0fc25-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fc25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fc25-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0fc25-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0fc25-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0fc25-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="0fc25-106">Any valid expression.</span></span> <span data-ttu-id="0fc25-107">Implicitně převést datové typy musí mít oba výrazy.</span><span class="sxs-lookup"><span data-stu-id="0fc25-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0fc25-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="0fc25-108">Result Types</span></span>  
 <span data-ttu-id="0fc25-109">`true` Pokud levý výraz rovná pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="0fc25-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fc25-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0fc25-110">Remarks</span></span>  
 <span data-ttu-id="0fc25-111">== – Operátor je ekvivalentní =.</span><span class="sxs-lookup"><span data-stu-id="0fc25-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fc25-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="0fc25-112">Example</span></span>  
 <span data-ttu-id="0fc25-113">Následující dotaz Entity SQL používá = – operátor porovnání k porovnání rovnosti dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="0fc25-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="0fc25-114">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0fc25-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0fc25-115">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="0fc25-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0fc25-116">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0fc25-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="0fc25-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="0fc25-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="0fc25-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fc25-118">See also</span></span>
- [<span data-ttu-id="0fc25-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0fc25-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
