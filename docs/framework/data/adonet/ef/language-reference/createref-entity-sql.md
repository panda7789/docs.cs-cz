---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: cbaea82108dd3debcca972ca15dea248227330ac
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251104"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="29f46-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="29f46-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="29f46-103">Naprefabrikované odkazy na entitu v objektu EntitySet.</span><span class="sxs-lookup"><span data-stu-id="29f46-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29f46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29f46-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="29f46-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="29f46-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="29f46-106">Identifikátor EntitySet, nikoli řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="29f46-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="29f46-107">Výraz typu řádek, který odpovídá klíčovým vlastnostem typu entity.</span><span class="sxs-lookup"><span data-stu-id="29f46-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29f46-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29f46-108">Remarks</span></span>  
 <span data-ttu-id="29f46-109">`row_typed_expression`musí být strukturálně stejné jako typ klíče pro entitu.</span><span class="sxs-lookup"><span data-stu-id="29f46-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="29f46-110">To znamená, že musí mít stejný počet a typy polí ve stejném pořadí jako klíče entit.</span><span class="sxs-lookup"><span data-stu-id="29f46-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="29f46-111">V následujícím příkladu jsou Orders a BadOrders oba objekty EntitySet typu Order a ID se považuje za klíčovou vlastnost Order.</span><span class="sxs-lookup"><span data-stu-id="29f46-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="29f46-112">Příklad ukazuje, jak můžeme vytvořit odkaz na entitu v BadOrders.</span><span class="sxs-lookup"><span data-stu-id="29f46-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="29f46-113">Všimněte si, že odkaz může být dangling.</span><span class="sxs-lookup"><span data-stu-id="29f46-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="29f46-114">To znamená, že odkaz nemusí skutečně identifikovat konkrétní entitu.</span><span class="sxs-lookup"><span data-stu-id="29f46-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="29f46-115">V těchto případech `DEREF` operace s tímto odkazem vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="29f46-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="29f46-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="29f46-116">Example</span></span>  
 <span data-ttu-id="29f46-117">Následující Entity SQL dotaz používá operátor CREATEREF k vytvoření odkazu na entitu v sadě entit.</span><span class="sxs-lookup"><span data-stu-id="29f46-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="29f46-118">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="29f46-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="29f46-119">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="29f46-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="29f46-120">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="29f46-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="29f46-121">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="29f46-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="29f46-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29f46-122">See also</span></span>

- [<span data-ttu-id="29f46-123">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="29f46-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="29f46-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="29f46-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="29f46-125">KEY</span><span class="sxs-lookup"><span data-stu-id="29f46-125">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="29f46-126">REF</span><span class="sxs-lookup"><span data-stu-id="29f46-126">REF</span></span>](ref-entity-sql.md)
