---
title: Jazyk Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: f12a20f85a0449778614d3098f69d3da90902c95
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50048436"
---
# <a name="entity-sql-language"></a><span data-ttu-id="339c5-102">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="339c5-102">Entity SQL Language</span></span>
<span data-ttu-id="339c5-103">Entita SQL je nezávislý na úložišti dotazovací jazyk podobný SQL.</span><span class="sxs-lookup"><span data-stu-id="339c5-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="339c5-104">Entita SQL vám umožní provádět dotazy na entity data, jako objekty nebo ve formě tabulky.</span><span class="sxs-lookup"><span data-stu-id="339c5-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="339c5-105">Měli byste zvážit použití Entity SQL v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="339c5-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="339c5-106">Pokud dotaz musí dynamicky zkonstruovat za běhu.</span><span class="sxs-lookup"><span data-stu-id="339c5-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="339c5-107">V takovém případě byste měli také zvážit použití metody Tvůrce dotazů <xref:System.Data.Objects.ObjectQuery%601> místo vytváření Entity SQL řetězec za běhu dotazu.</span><span class="sxs-lookup"><span data-stu-id="339c5-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="339c5-108">Pokud chcete definovat dotaz jako součást definice modelu.</span><span class="sxs-lookup"><span data-stu-id="339c5-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="339c5-109">V datovém modelu se podporuje jenom Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="339c5-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="339c5-110">Další informace najdete v tématu [Element QueryView (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="339c5-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
-   <span data-ttu-id="339c5-111">Při použití zprostředkovatel EntityClient pro vrácení dat jen pro čtení entity jako s použitím sady řádků <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="339c5-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="339c5-112">Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="339c5-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="339c5-113">Pokud jste už jste odborník v jazycích dotazů založených na SQL, se může zdát vám nejvíc fyzické Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="339c5-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="339c5-114">Použití se zprostředkovatelem EntityClient Entity SQL</span><span class="sxs-lookup"><span data-stu-id="339c5-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="339c5-115">Pokud chcete používat Entity SQL se zprostředkovatelem EntityClient, naleznete v následujících tématech pro další informace:</span><span class="sxs-lookup"><span data-stu-id="339c5-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="339c5-116">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="339c5-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="339c5-117">Postupy: Sestavení připojovacího řetězce EntityConnection</span><span class="sxs-lookup"><span data-stu-id="339c5-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="339c5-118">Postup: Provedení dotazu, který vrátí výsledky typu PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="339c5-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="339c5-119">Postup: Provedení dotazu, který vrátí výsledky typu StructuralType</span><span class="sxs-lookup"><span data-stu-id="339c5-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="339c5-120">Postup: Provedení dotazu, který vrátí výsledky typu RefType</span><span class="sxs-lookup"><span data-stu-id="339c5-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="339c5-121">Postup: Provedení dotazu, který vrátí komplexní typy</span><span class="sxs-lookup"><span data-stu-id="339c5-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="339c5-122">Postup: Provedení dotazu, který vrátí vnořené kolekce</span><span class="sxs-lookup"><span data-stu-id="339c5-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="339c5-123">Postupy: Spuštění parametrizovaného dotazu Entity SQL pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="339c5-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="339c5-124">Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="339c5-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="339c5-125">Postup: Spuštění polymorfního dotazu</span><span class="sxs-lookup"><span data-stu-id="339c5-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="339c5-126">Postupy: Procházení relací pomocí navigačního operátoru</span><span class="sxs-lookup"><span data-stu-id="339c5-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="339c5-127">Pomocí dotazy objektu Entity SQL</span><span class="sxs-lookup"><span data-stu-id="339c5-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="339c5-128">Pokud chcete používat Entity SQL pomocí objektu dotazů, naleznete v následujících tématech pro další informace:</span><span class="sxs-lookup"><span data-stu-id="339c5-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="339c5-129">Postupy: provedení dotazu, který vrací objekty typu Entity</span><span class="sxs-lookup"><span data-stu-id="339c5-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](https://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [<span data-ttu-id="339c5-130">Postupy: spuštění parametrizovaného dotazu</span><span class="sxs-lookup"><span data-stu-id="339c5-130">How to: Execute a Parameterized Query</span></span>](https://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [<span data-ttu-id="339c5-131">Postupy: procházení vztahů pomocí navigačních vlastností</span><span class="sxs-lookup"><span data-stu-id="339c5-131">How to: Navigate Relationships Using Navigation Properties</span></span>](https://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [<span data-ttu-id="339c5-132">Postupy: volání uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="339c5-132">How to: Call a User-Defined Function</span></span>](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [<span data-ttu-id="339c5-133">Postupy: filtrování dat</span><span class="sxs-lookup"><span data-stu-id="339c5-133">How to: Filter Data</span></span>](https://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [<span data-ttu-id="339c5-134">Postupy: řazení dat</span><span class="sxs-lookup"><span data-stu-id="339c5-134">How to: Sort Data</span></span>](https://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [<span data-ttu-id="339c5-135">Postupy: seskupení dat</span><span class="sxs-lookup"><span data-stu-id="339c5-135">How to: Group Data</span></span>](https://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [<span data-ttu-id="339c5-136">Postupy: agregovaná Data</span><span class="sxs-lookup"><span data-stu-id="339c5-136">How to: Aggregate Data</span></span>](https://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [<span data-ttu-id="339c5-137">Postupy: provedení dotazu, který vrací objekty anonymního typu</span><span class="sxs-lookup"><span data-stu-id="339c5-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](https://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [<span data-ttu-id="339c5-138">Postupy: provedení dotazu, který vrátí kolekce primitivních typů</span><span class="sxs-lookup"><span data-stu-id="339c5-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](https://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [<span data-ttu-id="339c5-139">Postupy: dotaz související objekty v objekt EntityCollection</span><span class="sxs-lookup"><span data-stu-id="339c5-139">How to: Query Related Objects in an EntityCollection</span></span>](https://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [<span data-ttu-id="339c5-140">Postupy: řazení sjednocení dva dotazy</span><span class="sxs-lookup"><span data-stu-id="339c5-140">How to: Order the Union of Two Queries</span></span>](https://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [<span data-ttu-id="339c5-141">Postupy: výsledky stránky pomocí dotazu</span><span class="sxs-lookup"><span data-stu-id="339c5-141">How to: Page Through Query Results</span></span>](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a><span data-ttu-id="339c5-142">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="339c5-142">In This Section</span></span>  
 [<span data-ttu-id="339c5-143">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="339c5-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="339c5-144">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="339c5-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="339c5-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="339c5-145">See Also</span></span>  
 [<span data-ttu-id="339c5-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="339c5-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="339c5-147">Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="339c5-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
