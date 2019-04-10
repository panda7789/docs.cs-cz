---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: 6ae4712fb280418ad8cf17cd68a7bbcd9cf3b8a9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335651"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="38749-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="38749-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="38749-103">Fabricates odkazy na entity v element entityset.</span><span class="sxs-lookup"><span data-stu-id="38749-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38749-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38749-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="38749-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="38749-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="38749-106">Identifikátor objektu entityset, není řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="38749-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="38749-107">Výraz zadaný řádek, který odpovídá klíčové vlastnosti typu entity.</span><span class="sxs-lookup"><span data-stu-id="38749-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38749-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38749-108">Remarks</span></span>  
 `row_typed_expression` <span data-ttu-id="38749-109">musí být strukturálně ekvivalentní typ klíče entity.</span><span class="sxs-lookup"><span data-stu-id="38749-109">must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="38749-110">To znamená musí mít stejný počet a typy polí ve stejném pořadí jako klíče entity.</span><span class="sxs-lookup"><span data-stu-id="38749-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="38749-111">V následujícím příkladu objednávky a BadOrders jsou oba objekty EntitySet typu pořadí a Id je považován za jednu klíčovou vlastnost pořadí.</span><span class="sxs-lookup"><span data-stu-id="38749-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="38749-112">Příklad ukazuje, jak jsme může vytvořit odkaz na entitu v BadOrders.</span><span class="sxs-lookup"><span data-stu-id="38749-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="38749-113">Všimněte si, že odkaz může být dangling.</span><span class="sxs-lookup"><span data-stu-id="38749-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="38749-114">Odkaz na tedy nemusí ve skutečnosti identifikovat konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="38749-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="38749-115">V těchto případech se `DEREF` operace na tento odkaz, vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="38749-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="38749-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="38749-116">Example</span></span>  
 <span data-ttu-id="38749-117">Následující dotaz Entity SQL pomocí operátoru CREATEREF vyrobit odkazy na entity v sadě entit.</span><span class="sxs-lookup"><span data-stu-id="38749-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="38749-118">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="38749-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="38749-119">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="38749-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="38749-120">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="38749-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="38749-121">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="38749-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="38749-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38749-122">See also</span></span>

- [<span data-ttu-id="38749-123">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="38749-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="38749-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="38749-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [<span data-ttu-id="38749-125">KEY</span><span class="sxs-lookup"><span data-stu-id="38749-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="38749-126">REF</span><span class="sxs-lookup"><span data-stu-id="38749-126">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
