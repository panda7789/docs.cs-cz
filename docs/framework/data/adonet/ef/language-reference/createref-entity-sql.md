---
title: CREATEREF (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8de4266277be31fd51411d4b994f1b5de45f13df
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="createref-entity-sql"></a><span data-ttu-id="5df38-102">CREATEREF (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="5df38-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="5df38-103">Fabricates odkazy na entity v element entityset.</span><span class="sxs-lookup"><span data-stu-id="5df38-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5df38-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5df38-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="5df38-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5df38-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="5df38-106">Identifikátor objektu entityset není řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="5df38-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="5df38-107">Výraz typu řádek, který odpovídá na klíčové vlastnosti typu entity.</span><span class="sxs-lookup"><span data-stu-id="5df38-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5df38-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5df38-108">Remarks</span></span>  
 <span data-ttu-id="5df38-109">`row_typed_expression`musí být strukturálně ekvivalentní typ klíče pro entitu.</span><span class="sxs-lookup"><span data-stu-id="5df38-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="5df38-110">To znamená musí mít stejný počet a typy polí ve stejném pořadí jako klíče entit.</span><span class="sxs-lookup"><span data-stu-id="5df38-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="5df38-111">V následujícím příkladu objednávek a BadOrders jsou oba objekty entitysets typu pořadí a Id se považuje za jednu klíčovou vlastnost pořadí.</span><span class="sxs-lookup"><span data-stu-id="5df38-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="5df38-112">Příklad ukazuje, jak jsme může vytvořit odkaz na entitu v BadOrders.</span><span class="sxs-lookup"><span data-stu-id="5df38-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="5df38-113">Všimněte si, že může být dangling odkaz.</span><span class="sxs-lookup"><span data-stu-id="5df38-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="5df38-114">Odkaz na tedy nemusí ve skutečnosti identifikovat konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="5df38-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="5df38-115">V takových případech `DEREF` operace na tento odkaz, vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5df38-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="5df38-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="5df38-116">Example</span></span>  
 <span data-ttu-id="5df38-117">Následující dotaz Entity SQL pomocí operátoru CREATEREF vyrobit odkazy na entity v sadu entit.</span><span class="sxs-lookup"><span data-stu-id="5df38-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="5df38-118">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5df38-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5df38-119">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="5df38-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="5df38-120">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5df38-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="5df38-121">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="5df38-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="5df38-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="5df38-122">See Also</span></span>  
 [<span data-ttu-id="5df38-123">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5df38-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="5df38-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="5df38-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="5df38-125">KEY</span><span class="sxs-lookup"><span data-stu-id="5df38-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="5df38-126">REF</span><span class="sxs-lookup"><span data-stu-id="5df38-126">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
