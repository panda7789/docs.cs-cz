---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 4eea3d43ef6ae9ea91432ea277326526e5e91fbc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251332"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="5a8ea-102">ANYELEMENT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5a8ea-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="5a8ea-103">Extrahuje prvek z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="5a8ea-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a8ea-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="5a8ea-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5a8ea-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5a8ea-106">Libovolný platný výraz dotazu, který vrací kolekci pro extrakci prvku z.</span><span class="sxs-lookup"><span data-stu-id="5a8ea-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a8ea-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5a8ea-107">Return Value</span></span>  
 <span data-ttu-id="5a8ea-108">Jeden prvek v kolekci nebo libovolný element, pokud má kolekce více než jeden prvek; Pokud je kolekce prázdná, vrátí `null`.</span><span class="sxs-lookup"><span data-stu-id="5a8ea-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="5a8ea-109">Pokud `collection` je kolekce typu `Collection<T>`, pak `ANYELEMENT(collection)` je platný výraz, který je výsledkem instance typu `T`.</span><span class="sxs-lookup"><span data-stu-id="5a8ea-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a8ea-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a8ea-110">Remarks</span></span>  
 <span data-ttu-id="5a8ea-111">ANYELEMENT extrahuje libovolný prvek z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="5a8ea-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="5a8ea-112">Například následující příklad se pokusí extrahovat prvek singleton ze sady `Customers`.</span><span class="sxs-lookup"><span data-stu-id="5a8ea-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="5a8ea-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a8ea-113">Example</span></span>  
 <span data-ttu-id="5a8ea-114">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor AnyElement k extrakci prvku z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="5a8ea-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="5a8ea-115">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5a8ea-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5a8ea-116">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="5a8ea-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5a8ea-117">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="5a8ea-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5a8ea-118">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="5a8ea-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="5a8ea-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a8ea-119">See also</span></span>

- [<span data-ttu-id="5a8ea-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5a8ea-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5a8ea-121">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="5a8ea-121">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
