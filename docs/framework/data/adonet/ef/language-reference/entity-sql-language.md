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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 08e366e8bbd9df31f367496ca5e106b876921896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="entity-sql-language"></a><span data-ttu-id="723ba-102">Jazyk SQL entity</span><span class="sxs-lookup"><span data-stu-id="723ba-102">Entity SQL Language</span></span>
<span data-ttu-id="723ba-103">Entita SQL je nezávislé na úložiště dotazovací jazyk, který je podobný SQL.</span><span class="sxs-lookup"><span data-stu-id="723ba-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="723ba-104">Entity SQL vám umožní zadat dotaz na data entity, jako objekty nebo ve formě tabulky.</span><span class="sxs-lookup"><span data-stu-id="723ba-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="723ba-105">Měli byste zvážit použití Entity SQL v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="723ba-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="723ba-106">Pokud dotaz musí dynamicky zkonstruovat za běhu.</span><span class="sxs-lookup"><span data-stu-id="723ba-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="723ba-107">V takovém případě měli byste také zvážit použití metody Tvůrce dotazů z <xref:System.Data.Objects.ObjectQuery%601> místo vytváření Entity SQL řetězec za běhu dotazu.</span><span class="sxs-lookup"><span data-stu-id="723ba-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="723ba-108">Pokud chcete definovat dotaz jako součást definice modelu.</span><span class="sxs-lookup"><span data-stu-id="723ba-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="723ba-109">Pouze Entity SQL je podporována v datovém modelu.</span><span class="sxs-lookup"><span data-stu-id="723ba-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="723ba-110">Další informace najdete v tématu [Element QueryView (MSL)](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span><span class="sxs-lookup"><span data-stu-id="723ba-110">For more information, see [QueryView Element (MSL)](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span></span>  
  
-   <span data-ttu-id="723ba-111">Při použití EntityClient vrátit data jen pro čtení entity jako pomocí sady řádků <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="723ba-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="723ba-112">Další informace najdete v tématu [zprostředkovatel EntityClient rozhraní Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="723ba-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="723ba-113">Pokud už jste odborník v jazycích dotazů SQL, se může zdát nejvíce přirozené vám Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="723ba-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="723ba-114">Pomocí Entity SQL se zprostředkovatelem EntityClient</span><span class="sxs-lookup"><span data-stu-id="723ba-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="723ba-115">Pokud chcete použít entitu SQL se zprostředkovatelem EntityClient, najdete další informace v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="723ba-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="723ba-116">Zprostředkovatel EntityClient rozhraní Entity Framework</span><span class="sxs-lookup"><span data-stu-id="723ba-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="723ba-117">Postupy: sestavení řetězec připojení EntityConnection</span><span class="sxs-lookup"><span data-stu-id="723ba-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="723ba-118">Postup: provedení dotazu, který vrátí výsledky PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="723ba-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="723ba-119">Postup: provedení dotazu, který vrátí výsledky StructuralType</span><span class="sxs-lookup"><span data-stu-id="723ba-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="723ba-120">Postup: provedení dotazu, který vrátí výsledky RefType</span><span class="sxs-lookup"><span data-stu-id="723ba-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="723ba-121">Postup: provedení dotazu, který vrací komplexní typy</span><span class="sxs-lookup"><span data-stu-id="723ba-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="723ba-122">Postupy: spuštění dotaz, který vrátí vnořené kolekce</span><span class="sxs-lookup"><span data-stu-id="723ba-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="723ba-123">Postupy: spuštění dotazu SQL parametrizované Entity pomocí objekt EntityCommand</span><span class="sxs-lookup"><span data-stu-id="723ba-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="723ba-124">Postup: provedení parametrizované uložené procedury pomocí objekt EntityCommand</span><span class="sxs-lookup"><span data-stu-id="723ba-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="723ba-125">Postup: provedení polymorfní dotazu</span><span class="sxs-lookup"><span data-stu-id="723ba-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="723ba-126">Postupy: procházení vztahů pomocí přejděte – operátor</span><span class="sxs-lookup"><span data-stu-id="723ba-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="723ba-127">Pomocí objektu dotazy Entity SQL</span><span class="sxs-lookup"><span data-stu-id="723ba-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="723ba-128">Pokud chcete použít s dotazy na objekt Entity SQL, najdete další informace v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="723ba-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="723ba-129">Postup: provedení dotazu, který vrátí objekty typu Entity</span><span class="sxs-lookup"><span data-stu-id="723ba-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](http://msdn.microsoft.com/en-us/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [<span data-ttu-id="723ba-130">Postup: provedení parametrizovaného dotazu</span><span class="sxs-lookup"><span data-stu-id="723ba-130">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/en-us/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [<span data-ttu-id="723ba-131">Postupy: procházení vztahů pomocí navigační vlastnosti</span><span class="sxs-lookup"><span data-stu-id="723ba-131">How to: Navigate Relationships Using Navigation Properties</span></span>](http://msdn.microsoft.com/en-us/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [<span data-ttu-id="723ba-132">Postupy: volání funkce uživatelem definované</span><span class="sxs-lookup"><span data-stu-id="723ba-132">How to: Call a User-Defined Function</span></span>](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [<span data-ttu-id="723ba-133">Postupy: filtrování dat</span><span class="sxs-lookup"><span data-stu-id="723ba-133">How to: Filter Data</span></span>](http://msdn.microsoft.com/en-us/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [<span data-ttu-id="723ba-134">Postupy: řazení dat</span><span class="sxs-lookup"><span data-stu-id="723ba-134">How to: Sort Data</span></span>](http://msdn.microsoft.com/en-us/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [<span data-ttu-id="723ba-135">Postupy: seskupení dat</span><span class="sxs-lookup"><span data-stu-id="723ba-135">How to: Group Data</span></span>](http://msdn.microsoft.com/en-us/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [<span data-ttu-id="723ba-136">Postupy: agregace dat</span><span class="sxs-lookup"><span data-stu-id="723ba-136">How to: Aggregate Data</span></span>](http://msdn.microsoft.com/en-us/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [<span data-ttu-id="723ba-137">Postup: provedení dotazu, který vrátí objekty anonymního typu</span><span class="sxs-lookup"><span data-stu-id="723ba-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](http://msdn.microsoft.com/en-us/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [<span data-ttu-id="723ba-138">Postup: provedení dotazu, který vrátí kolekce primitivní typy</span><span class="sxs-lookup"><span data-stu-id="723ba-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](http://msdn.microsoft.com/en-us/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [<span data-ttu-id="723ba-139">Postupy: dotazování související objekty v EntityCollection</span><span class="sxs-lookup"><span data-stu-id="723ba-139">How to: Query Related Objects in an EntityCollection</span></span>](http://msdn.microsoft.com/en-us/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [<span data-ttu-id="723ba-140">Postupy: řazení sjednocení dva dotazy</span><span class="sxs-lookup"><span data-stu-id="723ba-140">How to: Order the Union of Two Queries</span></span>](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313)  
  
 [<span data-ttu-id="723ba-141">Postupy: výsledky stránky prostřednictvím dotazu</span><span class="sxs-lookup"><span data-stu-id="723ba-141">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a><span data-ttu-id="723ba-142">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="723ba-142">In This Section</span></span>  
 [<span data-ttu-id="723ba-143">Přehled SQL entity</span><span class="sxs-lookup"><span data-stu-id="723ba-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="723ba-144">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="723ba-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="723ba-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="723ba-145">See Also</span></span>  
 [<span data-ttu-id="723ba-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="723ba-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="723ba-147">Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="723ba-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
