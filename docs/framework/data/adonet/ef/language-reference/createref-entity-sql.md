---
title: CREATEREF (entita SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: 44954dcc1f3407a768ba23fe87ac4b4abcf1bac5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="createref-entity-sql"></a><span data-ttu-id="869f7-102">CREATEREF (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="869f7-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="869f7-103">Fabricates odkazy na entity v element entityset.</span><span class="sxs-lookup"><span data-stu-id="869f7-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="869f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="869f7-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="869f7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="869f7-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="869f7-106">Identifikátor objektu entityset není řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="869f7-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="869f7-107">Výraz typu řádek, který odpovídá na klíčové vlastnosti typu entity.</span><span class="sxs-lookup"><span data-stu-id="869f7-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="869f7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="869f7-108">Remarks</span></span>  
 <span data-ttu-id="869f7-109">`row_typed_expression` musí být strukturálně ekvivalentní typ klíče pro entitu.</span><span class="sxs-lookup"><span data-stu-id="869f7-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="869f7-110">To znamená musí mít stejný počet a typy polí ve stejném pořadí jako klíče entit.</span><span class="sxs-lookup"><span data-stu-id="869f7-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="869f7-111">V následujícím příkladu objednávek a BadOrders jsou oba objekty entitysets typu pořadí a Id se považuje za jednu klíčovou vlastnost pořadí.</span><span class="sxs-lookup"><span data-stu-id="869f7-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="869f7-112">Příklad ukazuje, jak jsme může vytvořit odkaz na entitu v BadOrders.</span><span class="sxs-lookup"><span data-stu-id="869f7-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="869f7-113">Všimněte si, že může být dangling odkaz.</span><span class="sxs-lookup"><span data-stu-id="869f7-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="869f7-114">Odkaz na tedy nemusí ve skutečnosti identifikovat konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="869f7-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="869f7-115">V takových případech `DEREF` operace na tento odkaz, vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="869f7-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="869f7-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="869f7-116">Example</span></span>  
 <span data-ttu-id="869f7-117">Následující dotaz Entity SQL pomocí operátoru CREATEREF vyrobit odkazy na entity v sadu entit.</span><span class="sxs-lookup"><span data-stu-id="869f7-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="869f7-118">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="869f7-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="869f7-119">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="869f7-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="869f7-120">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="869f7-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="869f7-121">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="869f7-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="869f7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="869f7-122">See Also</span></span>  
 [<span data-ttu-id="869f7-123">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="869f7-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="869f7-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="869f7-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="869f7-125">KEY</span><span class="sxs-lookup"><span data-stu-id="869f7-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="869f7-126">REF</span><span class="sxs-lookup"><span data-stu-id="869f7-126">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
