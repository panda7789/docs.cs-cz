---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: c0f7686f7ff3f6458637b51e29ecafe0c0ccfbc4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040323"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="796e7-102">ANYELEMENT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="796e7-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="796e7-103">Extrahuje prvek z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="796e7-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="796e7-104">Syntax</span></span>  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="796e7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="796e7-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="796e7-106">Libovolný platný výraz dotazu, který vrací kolekci pro extrakci prvku z.</span><span class="sxs-lookup"><span data-stu-id="796e7-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="796e7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="796e7-107">Return Value</span></span>  
 <span data-ttu-id="796e7-108">Jeden prvek v kolekci nebo libovolný element, pokud má kolekce více než jeden prvek; Pokud je kolekce prázdná, vrátí `null`.</span><span class="sxs-lookup"><span data-stu-id="796e7-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="796e7-109">Pokud je `collection` kolekce typu `Collection<T>`, pak `ANYELEMENT(collection)` je platný výraz, který poskytuje instanci typu `T`.</span><span class="sxs-lookup"><span data-stu-id="796e7-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="796e7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="796e7-110">Remarks</span></span>  
 <span data-ttu-id="796e7-111">ANYELEMENT extrahuje libovolný prvek z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="796e7-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="796e7-112">Například následující příklad se pokusí extrahovat element singleton ze sady `Customers`.</span><span class="sxs-lookup"><span data-stu-id="796e7-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="796e7-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="796e7-113">Example</span></span>  
 <span data-ttu-id="796e7-114">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor ANYELEMENT k extrakci prvku z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="796e7-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="796e7-115">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="796e7-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="796e7-116">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="796e7-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="796e7-117">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="796e7-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="796e7-118">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="796e7-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="796e7-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="796e7-119">See also</span></span>

- [<span data-ttu-id="796e7-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="796e7-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="796e7-121">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="796e7-121">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
