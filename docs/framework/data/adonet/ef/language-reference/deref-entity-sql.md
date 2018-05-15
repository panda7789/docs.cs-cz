---
title: DEREF (entita SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: ee3877ca256eb3847b0284ac2a7362a4a60aad48
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="deref-entity-sql"></a><span data-ttu-id="9f436-102">DEREF (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="9f436-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="9f436-103">Dereferences hodnota odkazu a vytváří výsledek této dereference.</span><span class="sxs-lookup"><span data-stu-id="9f436-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f436-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f436-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="9f436-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f436-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9f436-106">Jakýkoli platný dotaz výraz, která vrátí kolekci.</span><span class="sxs-lookup"><span data-stu-id="9f436-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f436-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9f436-107">Return Value</span></span>  
 <span data-ttu-id="9f436-108">Hodnota entity, který se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="9f436-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f436-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f436-109">Remarks</span></span>  
 <span data-ttu-id="9f436-110">Operátor DEREF dereferences hodnota odkazu a vytváří výsledek této dereference.</span><span class="sxs-lookup"><span data-stu-id="9f436-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="9f436-111">Například pokud `r` odkaz typu ref\<T >, `Deref``(r)` je výraz typu `T` , vypočítá entita odkazuje `r`.</span><span class="sxs-lookup"><span data-stu-id="9f436-111">For example, if `r` is a reference of type ref\<T>, `Deref``(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="9f436-112">Pokud hodnota odkaz má hodnotu null nebo je nepropojená (který je cílem odkazu neexistuje), výsledkem operátoru DEREF má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="9f436-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f436-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f436-113">Example</span></span>  
 <span data-ttu-id="9f436-114">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu pomocí operátoru DEREF dereference produktu dereference výsledek a hodnota odkazu.</span><span class="sxs-lookup"><span data-stu-id="9f436-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="9f436-115">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9f436-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9f436-116">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="9f436-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9f436-117">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9f436-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="9f436-118">Následující dotaz předejte jako argument metodu ExecutePrimitiveTypeQuery:</span><span class="sxs-lookup"><span data-stu-id="9f436-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="9f436-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f436-119">See Also</span></span>  
 [<span data-ttu-id="9f436-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9f436-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="9f436-121">REF</span><span class="sxs-lookup"><span data-stu-id="9f436-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="9f436-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="9f436-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="9f436-123">KEY</span><span class="sxs-lookup"><span data-stu-id="9f436-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="9f436-124">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="9f436-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
