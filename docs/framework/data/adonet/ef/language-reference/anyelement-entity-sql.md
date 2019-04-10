---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: ff79417008b7807fbf206d4bcb65b4e5ea1cc576
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296131"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="b6b5d-102">ANYELEMENT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b6b5d-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="b6b5d-103">Extrahuje element z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="b6b5d-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6b5d-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="b6b5d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b6b5d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b6b5d-106">Libovolný platný dotaz výraz, který vrátí kolekce k extrakci prvek z.</span><span class="sxs-lookup"><span data-stu-id="b6b5d-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6b5d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b6b5d-107">Return Value</span></span>  
 <span data-ttu-id="b6b5d-108">Jeden prvek v kolekci nebo libovolný element, pokud kolekce obsahuje více než jednu; Pokud kolekce je prázdná, vrátí `null`.</span><span class="sxs-lookup"><span data-stu-id="b6b5d-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="b6b5d-109">Pokud `collection` je kolekce typu `Collection<T>`, pak `ANYELEMENT(collection)` je platný výraz, který vrací instanci typu `T`.</span><span class="sxs-lookup"><span data-stu-id="b6b5d-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6b5d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6b5d-110">Remarks</span></span>  
 <span data-ttu-id="b6b5d-111">ANYELEMENT extrahuje libovolný element z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="b6b5d-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="b6b5d-112">Například následující příklad pokusí extrahovat prvek jednotlivý prvek ze sady `Customers`.</span><span class="sxs-lookup"><span data-stu-id="b6b5d-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="b6b5d-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6b5d-113">Example</span></span>  
 <span data-ttu-id="b6b5d-114">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátora ANYELEMENT extrahovat element z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="b6b5d-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="b6b5d-115">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b6b5d-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b6b5d-116">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="b6b5d-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b6b5d-117">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b6b5d-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b6b5d-118">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="b6b5d-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="b6b5d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6b5d-119">See also</span></span>

- [<span data-ttu-id="b6b5d-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b6b5d-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="b6b5d-121">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="b6b5d-121">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
