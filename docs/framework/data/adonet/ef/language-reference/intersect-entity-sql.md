---
title: Průsečík (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: dc7338d176302b8683d541ab0dc715dd8d149c6f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319769"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="4a513-102">Průsečík (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4a513-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="4a513-103">Vrátí kolekci všech jedinečných hodnot, které jsou vráceny výrazy dotazu na levé a pravé straně operandu INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="4a513-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="4a513-104">Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="4a513-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a513-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a513-105">Syntax</span></span>  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a513-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a513-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4a513-107">Libovolný platný výraz dotazu, který vrátí kolekci pro porovnání s kolekcí vrácenou z jiného výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="4a513-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a513-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4a513-108">Return Value</span></span>  
 <span data-ttu-id="4a513-109">Kolekce stejného typu nebo společného základního nebo odvozeného typu jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="4a513-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a513-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a513-110">Remarks</span></span>  
 <span data-ttu-id="4a513-111">Průsečík je jednou z operátorů množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4a513-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="4a513-112">Všechny operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="4a513-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="4a513-113">Informace o prioritách pro operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] naleznete v tématu [Except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4a513-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a513-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a513-114">Example</span></span>  
 <span data-ttu-id="4a513-115">Následující Entity SQL dotaz pomocí operátoru INTERSECT vrátí kolekci všech jedinečných hodnot, které jsou vráceny výrazy dotazu na levé a pravé straně operandu INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="4a513-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="4a513-116">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4a513-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4a513-117">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="4a513-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4a513-118">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4a513-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4a513-119">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="4a513-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="4a513-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a513-120">See also</span></span>

- [<span data-ttu-id="4a513-121">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4a513-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
