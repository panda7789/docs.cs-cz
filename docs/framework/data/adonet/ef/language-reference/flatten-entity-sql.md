---
title: VYROVNÁNÍ (entita SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 75463ed622ac969eb2690c4118861823479a2caa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760567"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="bb6c6-102">VYROVNÁNÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="bb6c6-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="bb6c6-103">Převede kolekci plochou kolekce kolekcí.</span><span class="sxs-lookup"><span data-stu-id="bb6c6-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="bb6c6-104">Nová kolekce obsahuje všechny stejné prvky, jako původní kolekce, ale bez vnořené struktury.</span><span class="sxs-lookup"><span data-stu-id="bb6c6-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6c6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb6c6-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="bb6c6-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="bb6c6-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="bb6c6-107">Libovolný platný výraz, který vrátí kolekce hodnota kolekcí k vyrovnání do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="bb6c6-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb6c6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb6c6-108">Remarks</span></span>  
 <span data-ttu-id="bb6c6-109">`FLATTEN` patří mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="bb6c6-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="bb6c6-110">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="bb6c6-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="bb6c6-111">V tématu [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) přednost informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="bb6c6-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb6c6-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb6c6-112">Example</span></span>  
 <span data-ttu-id="bb6c6-113">Následující dotaz Entity SQL používá `FLATTEN` operátor převést na kolekci plochou kolekce kolekcí.</span><span class="sxs-lookup"><span data-stu-id="bb6c6-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="bb6c6-114">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="bb6c6-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="bb6c6-115">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="bb6c6-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="bb6c6-116">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="bb6c6-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="bb6c6-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb6c6-117">See Also</span></span>  
 [<span data-ttu-id="bb6c6-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bb6c6-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
