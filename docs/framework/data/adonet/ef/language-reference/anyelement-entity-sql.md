---
title: ANYELEMENT (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 518ac4bc1ba6842a4b5e5f3b1f0771495752859c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="0b228-102">ANYELEMENT (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="0b228-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="0b228-103">Extrahuje element z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="0b228-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b228-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b228-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b228-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0b228-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0b228-106">Libovolný platný dotaz výraz, který vrátí kolekce k extrakci element z.</span><span class="sxs-lookup"><span data-stu-id="0b228-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b228-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0b228-107">Return Value</span></span>  
 <span data-ttu-id="0b228-108">Jednotlivých elementů v kolekci nebo libovolný element, pokud kolekce obsahuje více než jednu; Pokud je kolekce prázdná, vrátí `null`.</span><span class="sxs-lookup"><span data-stu-id="0b228-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="0b228-109">Pokud `collection` je kolekce typu `Collection<T>`, pak `ANYELEMENT(collection)` je platný výraz, který poskytne instanci typu `T`.</span><span class="sxs-lookup"><span data-stu-id="0b228-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b228-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b228-110">Remarks</span></span>  
 <span data-ttu-id="0b228-111">ANYELEMENT extrahuje libovolně zvolený element z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="0b228-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="0b228-112">Například v následujícím příkladu pokusí extrahovat singleton element ze sady `Customers`.</span><span class="sxs-lookup"><span data-stu-id="0b228-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="0b228-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b228-113">Example</span></span>  
 <span data-ttu-id="0b228-114">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor ANYELEMENT extrahovat element z kolekce s více hodnotami.</span><span class="sxs-lookup"><span data-stu-id="0b228-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="0b228-115">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0b228-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0b228-116">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="0b228-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0b228-117">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0b228-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="0b228-118">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="0b228-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="0b228-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b228-119">See Also</span></span>  
 [<span data-ttu-id="0b228-120">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="0b228-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="0b228-121">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="0b228-121">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
