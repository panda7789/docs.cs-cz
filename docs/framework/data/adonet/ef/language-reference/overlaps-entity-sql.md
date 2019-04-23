---
title: PŘEKRYTÍ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: 9d909fb7efbb29619351cfc866b0f84381d0b80b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319635"
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="3f758-102">PŘEKRYTÍ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3f758-102">OVERLAPS (Entity SQL)</span></span>
<span data-ttu-id="3f758-103">Určuje, jestli dvě kolekce mají společné prvky.</span><span class="sxs-lookup"><span data-stu-id="3f758-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f758-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f758-104">Syntax</span></span>  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3f758-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3f758-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3f758-106">Libovolný výraz platný dotaz, který vrátí kolekce k porovnání s kolekci vrácené z jiného výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="3f758-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="3f758-107">Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="3f758-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f758-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3f758-108">Return Value</span></span>  
 <span data-ttu-id="3f758-109">`true` Pokud se dvě kolekce mají společné prvky; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="3f758-109">`true` if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f758-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f758-110">Remarks</span></span>  
 <span data-ttu-id="3f758-111">PŘEKRYTÍ nabízí funkčně ekvivalentní následujícímu:</span><span class="sxs-lookup"><span data-stu-id="3f758-111">OVERLAPS provides functionally equivalent to the following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="3f758-112">PŘEKRYTÍ je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="3f758-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="3f758-113">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="3f758-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="3f758-114">Priorita informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory, naleznete v tématu [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3f758-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f758-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f758-115">Example</span></span>  
 <span data-ttu-id="3f758-116">Následující dotaz Entity SQL pomocí operátoru PŘEKRÝVÁ se určuje, zda mají dvě kolekce společné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3f758-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="3f758-117">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3f758-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3f758-118">Chcete-li zkompilovat a spustit, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="3f758-118">To compile and run this, follow these steps:</span></span>  
  
1. <span data-ttu-id="3f758-119">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3f758-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3f758-120">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="3f758-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="3f758-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f758-121">See also</span></span>

- [<span data-ttu-id="3f758-122">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3f758-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
