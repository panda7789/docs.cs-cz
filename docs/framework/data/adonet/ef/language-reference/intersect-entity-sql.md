---
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 85b0abb03161b2df0cfc4ddf6cafc92fb7de9d95
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296976"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="4da34-102">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4da34-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="4da34-103">Vrátí kolekci všech jedinečných hodnot, které jsou vráceny ve výrazech dotazů na levé straně a pravé straně INTERSECT operandu.</span><span class="sxs-lookup"><span data-stu-id="4da34-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="4da34-104">Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="4da34-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da34-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4da34-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4da34-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4da34-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4da34-107">Libovolný výraz platný dotaz, který vrátí kolekce k porovnání s kolekci vrácené z jiného výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="4da34-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4da34-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4da34-108">Return Value</span></span>  
 <span data-ttu-id="4da34-109">Kolekce stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="4da34-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4da34-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4da34-110">Remarks</span></span>  
 <span data-ttu-id="4da34-111">INTERSECT je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="4da34-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="4da34-112">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="4da34-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="4da34-113">Priorita informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory, naleznete v tématu [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4da34-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4da34-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4da34-114">Example</span></span>  
 <span data-ttu-id="4da34-115">Následující dotaz Entity SQL používá operátor INTERSECT vrátí kolekci všech jedinečných hodnot, které jsou vráceny ve výrazech dotazů na levé straně a pravé straně INTERSECT operandu.</span><span class="sxs-lookup"><span data-stu-id="4da34-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="4da34-116">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4da34-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4da34-117">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="4da34-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4da34-118">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4da34-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4da34-119">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="4da34-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="4da34-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4da34-120">See also</span></span>

- [<span data-ttu-id="4da34-121">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4da34-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
