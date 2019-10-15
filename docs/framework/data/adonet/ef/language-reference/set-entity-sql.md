---
title: NASTAVIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 9d4cdeac317509fd61741a19276a6764a1c2bfce
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319355"
---
# <a name="set-entity-sql"></a><span data-ttu-id="e5922-102">NASTAVIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e5922-102">SET (Entity SQL)</span></span>
<span data-ttu-id="e5922-103">Výraz MNOŽINy se používá k převodu kolekce objektů na sadu pomocí získání nové kolekce s odebranými duplicitními prvky.</span><span class="sxs-lookup"><span data-stu-id="e5922-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5922-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5922-104">Syntax</span></span>  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="e5922-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e5922-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e5922-106">Libovolný platný výraz dotazu, který vrací kolekci.</span><span class="sxs-lookup"><span data-stu-id="e5922-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5922-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5922-107">Remarks</span></span>  
 <span data-ttu-id="e5922-108">Výraz množiny `SET(c)` je logicky ekvivalentní následujícímu příkazu SELECT:</span><span class="sxs-lookup"><span data-stu-id="e5922-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="e5922-109">`SET` je jedním z operátorů sady [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5922-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="e5922-110">Všechny operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="e5922-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="e5922-111">Viz téma [s výjimkou](except-entity-sql.md) informací o prioritách pro operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5922-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5922-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5922-112">Example</span></span>  
 <span data-ttu-id="e5922-113">Následující Entity SQL dotaz používá výraz SET pro převod kolekce objektů do sady.</span><span class="sxs-lookup"><span data-stu-id="e5922-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="e5922-114">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e5922-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e5922-115">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="e5922-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e5922-116">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e5922-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="e5922-117">Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="e5922-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a><span data-ttu-id="e5922-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5922-118">See also</span></span>

- [<span data-ttu-id="e5922-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e5922-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
