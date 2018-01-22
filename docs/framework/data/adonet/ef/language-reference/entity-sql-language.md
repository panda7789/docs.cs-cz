---
title: Jazyk SQL entity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a0caf2670a90db0e44ad1f51689b6086313de274
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="entity-sql-language"></a><span data-ttu-id="086da-102">Jazyk SQL entity</span><span class="sxs-lookup"><span data-stu-id="086da-102">Entity SQL Language</span></span>
<span data-ttu-id="086da-103">Entita SQL je nezávislé na úložiště dotazovací jazyk, který je podobný SQL.</span><span class="sxs-lookup"><span data-stu-id="086da-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="086da-104">Entity SQL vám umožní zadat dotaz na data entity, jako objekty nebo ve formě tabulky.</span><span class="sxs-lookup"><span data-stu-id="086da-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="086da-105">Měli byste zvážit použití Entity SQL v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="086da-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="086da-106">Pokud dotaz musí dynamicky zkonstruovat za běhu.</span><span class="sxs-lookup"><span data-stu-id="086da-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="086da-107">V takovém případě měli byste také zvážit použití metody Tvůrce dotazů z <xref:System.Data.Objects.ObjectQuery%601> místo vytváření Entity SQL řetězec za běhu dotazu.</span><span class="sxs-lookup"><span data-stu-id="086da-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="086da-108">Pokud chcete definovat dotaz jako součást definice modelu.</span><span class="sxs-lookup"><span data-stu-id="086da-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="086da-109">Pouze Entity SQL je podporována v datovém modelu.</span><span class="sxs-lookup"><span data-stu-id="086da-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="086da-110">Další informace najdete v tématu [Element QueryView (MSL)](http://msdn.microsoft.com/library/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span><span class="sxs-lookup"><span data-stu-id="086da-110">For more information, see [QueryView Element (MSL)](http://msdn.microsoft.com/library/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span></span>  
  
-   <span data-ttu-id="086da-111">Při použití EntityClient vrátit data jen pro čtení entity jako pomocí sady řádků <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="086da-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="086da-112">Další informace najdete v tématu [zprostředkovatel EntityClient rozhraní Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="086da-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="086da-113">Pokud už jste odborník v jazycích dotazů SQL, se může zdát nejvíce přirozené vám Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="086da-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="086da-114">Pomocí Entity SQL se zprostředkovatelem EntityClient</span><span class="sxs-lookup"><span data-stu-id="086da-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="086da-115">Pokud chcete použít entitu SQL se zprostředkovatelem EntityClient, najdete další informace v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="086da-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="086da-116">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="086da-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="086da-117">Postupy: Sestavení připojovacího řetězce EntityConnection</span><span class="sxs-lookup"><span data-stu-id="086da-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="086da-118">Postup: Provedení dotazu, který vrátí výsledky typu PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="086da-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="086da-119">Postup: Provedení dotazu, který vrátí výsledky typu StructuralType</span><span class="sxs-lookup"><span data-stu-id="086da-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="086da-120">Postup: Provedení dotazu, který vrátí výsledky typu RefType</span><span class="sxs-lookup"><span data-stu-id="086da-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="086da-121">Postup: Provedení dotazu, který vrátí komplexní typy</span><span class="sxs-lookup"><span data-stu-id="086da-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="086da-122">Postup: Provedení dotazu, který vrátí vnořené kolekce</span><span class="sxs-lookup"><span data-stu-id="086da-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="086da-123">Postupy: Spuštění parametrizovaného dotazu Entity SQL pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="086da-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="086da-124">Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="086da-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="086da-125">Postup: Spuštění polymorfního dotazu</span><span class="sxs-lookup"><span data-stu-id="086da-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="086da-126">Postupy: Procházení relací pomocí navigačního operátoru</span><span class="sxs-lookup"><span data-stu-id="086da-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="086da-127">Pomocí objektu dotazy Entity SQL</span><span class="sxs-lookup"><span data-stu-id="086da-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="086da-128">Pokud chcete použít s dotazy na objekt Entity SQL, najdete další informace v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="086da-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="086da-129">Postup: provedení dotazu, který vrátí objekty typu Entity</span><span class="sxs-lookup"><span data-stu-id="086da-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](http://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [<span data-ttu-id="086da-130">Postup: provedení parametrizovaného dotazu</span><span class="sxs-lookup"><span data-stu-id="086da-130">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [<span data-ttu-id="086da-131">Postupy: procházení vztahů pomocí navigační vlastnosti</span><span class="sxs-lookup"><span data-stu-id="086da-131">How to: Navigate Relationships Using Navigation Properties</span></span>](http://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [<span data-ttu-id="086da-132">Postupy: volání funkce uživatelem definované</span><span class="sxs-lookup"><span data-stu-id="086da-132">How to: Call a User-Defined Function</span></span>](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [<span data-ttu-id="086da-133">Postupy: filtrování dat</span><span class="sxs-lookup"><span data-stu-id="086da-133">How to: Filter Data</span></span>](http://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [<span data-ttu-id="086da-134">Postupy: řazení dat</span><span class="sxs-lookup"><span data-stu-id="086da-134">How to: Sort Data</span></span>](http://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [<span data-ttu-id="086da-135">Postupy: seskupení dat</span><span class="sxs-lookup"><span data-stu-id="086da-135">How to: Group Data</span></span>](http://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [<span data-ttu-id="086da-136">Postupy: agregace dat</span><span class="sxs-lookup"><span data-stu-id="086da-136">How to: Aggregate Data</span></span>](http://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [<span data-ttu-id="086da-137">Postup: provedení dotazu, který vrátí objekty anonymního typu</span><span class="sxs-lookup"><span data-stu-id="086da-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](http://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [<span data-ttu-id="086da-138">Postup: provedení dotazu, který vrátí kolekce primitivní typy</span><span class="sxs-lookup"><span data-stu-id="086da-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](http://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [<span data-ttu-id="086da-139">Postupy: dotazování související objekty v EntityCollection</span><span class="sxs-lookup"><span data-stu-id="086da-139">How to: Query Related Objects in an EntityCollection</span></span>](http://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [<span data-ttu-id="086da-140">Postupy: řazení sjednocení dva dotazy</span><span class="sxs-lookup"><span data-stu-id="086da-140">How to: Order the Union of Two Queries</span></span>](http://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [<span data-ttu-id="086da-141">Postupy: výsledky stránky prostřednictvím dotazu</span><span class="sxs-lookup"><span data-stu-id="086da-141">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a><span data-ttu-id="086da-142">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="086da-142">In This Section</span></span>  
 [<span data-ttu-id="086da-143">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="086da-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="086da-144">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="086da-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="086da-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="086da-145">See Also</span></span>  
 [<span data-ttu-id="086da-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="086da-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="086da-147">Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="086da-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
