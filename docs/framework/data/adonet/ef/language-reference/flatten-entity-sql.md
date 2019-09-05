---
title: SHRNOUT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 327a20bbc53566846e7d828f511bcd1d25cc5504
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250959"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="f2853-102">SHRNOUT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f2853-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="f2853-103">Převede kolekci kolekcí do ploché kolekce.</span><span class="sxs-lookup"><span data-stu-id="f2853-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="f2853-104">Nová kolekce obsahuje všechny stejné prvky jako starou kolekci, ale bez vnořené struktury.</span><span class="sxs-lookup"><span data-stu-id="f2853-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2853-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2853-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="f2853-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="f2853-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="f2853-107">Libovolný platný výraz, který vrátí kolekci hodnot kolekcí, které mají být shrnuty do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="f2853-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2853-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2853-108">Remarks</span></span>  
 <span data-ttu-id="f2853-109">`FLATTEN`je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množin operátorů.</span><span class="sxs-lookup"><span data-stu-id="f2853-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="f2853-110">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="f2853-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="f2853-111">Viz [s výjimkou](except-entity-sql.md) pro informace o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prioritách pro množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="f2853-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2853-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2853-112">Example</span></span>  
 <span data-ttu-id="f2853-113">Následující Entity SQL dotaz používá `FLATTEN` operátor k převodu kolekce kolekcí do ploché kolekce.</span><span class="sxs-lookup"><span data-stu-id="f2853-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="f2853-114">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="f2853-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f2853-115">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="f2853-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f2853-116">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="f2853-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="f2853-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2853-117">See also</span></span>

- [<span data-ttu-id="f2853-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f2853-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
