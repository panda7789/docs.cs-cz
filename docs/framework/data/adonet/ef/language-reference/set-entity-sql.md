---
title: SET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: b6adce314e5d4fb1e4077b0efef758d07444e496
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744437"
---
# <a name="set-entity-sql"></a><span data-ttu-id="189f9-102">SET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="189f9-102">SET (Entity SQL)</span></span>
<span data-ttu-id="189f9-103">Pro převedení na kolekci objektů sady pomocí získávání novou kolekci s odstraněnými všechny duplicitní prvky je použit výraz sady.</span><span class="sxs-lookup"><span data-stu-id="189f9-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="189f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="189f9-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="189f9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="189f9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="189f9-106">Libovolný výraz platný dotaz, který vrátí kolekci.</span><span class="sxs-lookup"><span data-stu-id="189f9-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="189f9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="189f9-107">Remarks</span></span>  
 <span data-ttu-id="189f9-108">Výraz sady `SET(c)` je logicky ekvivalentní následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="189f9-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="189f9-109">`SET` je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="189f9-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="189f9-110">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="189f9-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="189f9-111">Zobrazit [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) prioritu informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="189f9-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="189f9-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="189f9-112">Example</span></span>  
 <span data-ttu-id="189f9-113">Následující dotaz Entity SQL používá pro převod na kolekci objektů do sady výraz sady.</span><span class="sxs-lookup"><span data-stu-id="189f9-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="189f9-114">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="189f9-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="189f9-115">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="189f9-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="189f9-116">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="189f9-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="189f9-117">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="189f9-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="189f9-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="189f9-118">See also</span></span>
- [<span data-ttu-id="189f9-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="189f9-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
