---
title: SET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: dab124e139f3491c4a7a42eb90c4ffb3b3a92258
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158558"
---
# <a name="set-entity-sql"></a><span data-ttu-id="83f25-102">SET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="83f25-102">SET (Entity SQL)</span></span>
<span data-ttu-id="83f25-103">Pro převedení na kolekci objektů sady pomocí získávání novou kolekci s odstraněnými všechny duplicitní prvky je použit výraz sady.</span><span class="sxs-lookup"><span data-stu-id="83f25-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83f25-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="83f25-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="83f25-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="83f25-106">Libovolný výraz platný dotaz, který vrátí kolekci.</span><span class="sxs-lookup"><span data-stu-id="83f25-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83f25-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83f25-107">Remarks</span></span>  
 <span data-ttu-id="83f25-108">Výraz sady `SET(c)` je logicky ekvivalentní následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="83f25-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` <span data-ttu-id="83f25-109">je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="83f25-109">is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="83f25-110">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="83f25-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="83f25-111">Zobrazit [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) prioritu informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="83f25-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f25-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="83f25-112">Example</span></span>  
 <span data-ttu-id="83f25-113">Následující dotaz Entity SQL používá pro převod na kolekci objektů do sady výraz sady.</span><span class="sxs-lookup"><span data-stu-id="83f25-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="83f25-114">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="83f25-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="83f25-115">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="83f25-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="83f25-116">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="83f25-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="83f25-117">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="83f25-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="83f25-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83f25-118">See also</span></span>

- [<span data-ttu-id="83f25-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="83f25-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
