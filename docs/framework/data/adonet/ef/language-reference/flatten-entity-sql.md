---
title: SHRNOUT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 84b846e3db86c664bc42363f3d983a1001f5c318
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833810"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="8044b-102">SHRNOUT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8044b-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="8044b-103">Převede kolekci kolekcí do ploché kolekce.</span><span class="sxs-lookup"><span data-stu-id="8044b-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="8044b-104">Nová kolekce obsahuje všechny stejné prvky jako starou kolekci, ale bez vnořené struktury.</span><span class="sxs-lookup"><span data-stu-id="8044b-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8044b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8044b-105">Syntax</span></span>  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="8044b-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="8044b-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="8044b-107">Libovolný platný výraz, který vrátí kolekci hodnot kolekcí, které mají být shrnuty do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="8044b-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8044b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8044b-108">Remarks</span></span>  
 <span data-ttu-id="8044b-109">`FLATTEN` je jedním z operátorů sady [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8044b-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="8044b-110">Všechny operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="8044b-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="8044b-111">Viz téma [s výjimkou](except-entity-sql.md) informací o prioritách pro operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8044b-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8044b-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="8044b-112">Example</span></span>  
 <span data-ttu-id="8044b-113">Následující Entity SQL dotaz používá operátor `FLATTEN` k převodu kolekce kolekcí do ploché kolekce.</span><span class="sxs-lookup"><span data-stu-id="8044b-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="8044b-114">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="8044b-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8044b-115">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8044b-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8044b-116">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="8044b-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="8044b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8044b-117">See also</span></span>

- [<span data-ttu-id="8044b-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8044b-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
