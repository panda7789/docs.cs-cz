---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: 3659f2c0690b00e728630c6e77308ba9d424bb1b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833924"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="b0817-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b0817-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="b0817-103">Naprefabrikované odkazy na entitu v objektu EntitySet.</span><span class="sxs-lookup"><span data-stu-id="b0817-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0817-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0817-104">Syntax</span></span>  
  
```sql  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="b0817-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b0817-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="b0817-106">Identifikátor EntitySet, nikoli řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="b0817-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="b0817-107">Výraz typu řádek, který odpovídá klíčovým vlastnostem typu entity.</span><span class="sxs-lookup"><span data-stu-id="b0817-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0817-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0817-108">Remarks</span></span>  
 <span data-ttu-id="b0817-109">`row_typed_expression` musí být strukturálně ekvivalentní typu klíče pro entitu.</span><span class="sxs-lookup"><span data-stu-id="b0817-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="b0817-110">To znamená, že musí mít stejný počet a typy polí ve stejném pořadí jako klíče entit.</span><span class="sxs-lookup"><span data-stu-id="b0817-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="b0817-111">V následujícím příkladu jsou Orders a BadOrders oba objekty EntitySet typu Order a ID se považuje za klíčovou vlastnost Order.</span><span class="sxs-lookup"><span data-stu-id="b0817-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="b0817-112">Příklad ukazuje, jak můžeme vytvořit odkaz na entitu v BadOrders.</span><span class="sxs-lookup"><span data-stu-id="b0817-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="b0817-113">Všimněte si, že odkaz může být dangling.</span><span class="sxs-lookup"><span data-stu-id="b0817-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="b0817-114">To znamená, že odkaz nemusí skutečně identifikovat konkrétní entitu.</span><span class="sxs-lookup"><span data-stu-id="b0817-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="b0817-115">V těchto případech operace `DEREF` na tomto odkazu vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b0817-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```sql  
SELECT CreateRef(LOB.BadOrders, row(o.Id))
FROM LOB.Orders AS o
```  
  
## <a name="example"></a><span data-ttu-id="b0817-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0817-116">Example</span></span>  
 <span data-ttu-id="b0817-117">Následující Entity SQL dotaz používá operátor CREATEREF k vytvoření odkazu na entitu v sadě entit.</span><span class="sxs-lookup"><span data-stu-id="b0817-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="b0817-118">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b0817-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b0817-119">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="b0817-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b0817-120">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b0817-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b0817-121">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="b0817-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CREATEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="b0817-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0817-122">See also</span></span>

- [<span data-ttu-id="b0817-123">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b0817-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="b0817-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="b0817-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="b0817-125">KEY</span><span class="sxs-lookup"><span data-stu-id="b0817-125">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="b0817-126">REF</span><span class="sxs-lookup"><span data-stu-id="b0817-126">REF</span></span>](ref-entity-sql.md)
