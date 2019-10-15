---
title: PŘEKRYVy (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: bdee9281fd406a3d029d3a10536cbdd48d2f7a58
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319418"
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="135e6-102">PŘEKRYVy (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="135e6-102">OVERLAPS (Entity SQL)</span></span>
<span data-ttu-id="135e6-103">Určuje, zda dvě kolekce mají společné prvky.</span><span class="sxs-lookup"><span data-stu-id="135e6-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="135e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="135e6-104">Syntax</span></span>  
  
```sql  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="135e6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="135e6-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="135e6-106">Libovolný platný výraz dotazu, který vrátí kolekci pro porovnání s kolekcí vrácenou z jiného výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="135e6-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="135e6-107">Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="135e6-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="135e6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="135e6-108">Return Value</span></span>  
 <span data-ttu-id="135e6-109">`true`, pokud mají dvě kolekce společné prvky; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="135e6-109">`true` if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="135e6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="135e6-110">Remarks</span></span>  
 <span data-ttu-id="135e6-111">PŘEKRYVy poskytují funkčně ekvivalentní následujícímu:</span><span class="sxs-lookup"><span data-stu-id="135e6-111">OVERLAPS provides functionally equivalent to the following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="135e6-112">Překrytí je jedním z operátorů množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="135e6-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="135e6-113">Všechny operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="135e6-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="135e6-114">Informace o prioritách pro operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] naleznete v tématu [Except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="135e6-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="135e6-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="135e6-115">Example</span></span>  
 <span data-ttu-id="135e6-116">Následující Entity SQL dotaz používá operátor překrytí k určení, zda dvě kolekce mají společnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="135e6-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="135e6-117">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="135e6-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="135e6-118">Pro zkompilování a spuštění použijte následující postup:</span><span class="sxs-lookup"><span data-stu-id="135e6-118">To compile and run this, follow these steps:</span></span>  
  
1. <span data-ttu-id="135e6-119">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="135e6-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="135e6-120">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="135e6-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#OVERLAPS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="135e6-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="135e6-121">See also</span></span>

- [<span data-ttu-id="135e6-122">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="135e6-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
