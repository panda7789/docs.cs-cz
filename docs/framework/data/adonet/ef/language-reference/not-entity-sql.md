---
title: '! (NOT) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 51d3bdbc4adb0b5fd6275629219698dd9b42fa86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306765"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="26631-103">!</span><span class="sxs-lookup"><span data-stu-id="26631-103">!</span></span> <span data-ttu-id="26631-104">(NOT) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="26631-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="26631-105">Neguje `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="26631-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26631-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26631-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="26631-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="26631-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="26631-108">Libovolný platný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="26631-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26631-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26631-109">Remarks</span></span>  
 <span data-ttu-id="26631-110">Vykřičník (!) obsahuje stejné funkce jako operátor NOT.</span><span class="sxs-lookup"><span data-stu-id="26631-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26631-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="26631-111">Example</span></span>  
 <span data-ttu-id="26631-112">Následující dotaz Entity SQL Neguje pomocí operátoru NOT `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="26631-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="26631-113">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="26631-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="26631-114">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="26631-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="26631-115">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="26631-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="26631-116">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="26631-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="26631-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26631-117">See also</span></span>

- [<span data-ttu-id="26631-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="26631-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
