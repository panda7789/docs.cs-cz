---
title: Jazyk Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 09ec1a5518ec0847b54394449f32b3068c811577
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140930"
---
# <a name="entity-sql-language"></a><span data-ttu-id="51ae4-102">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="51ae4-102">Entity SQL Language</span></span>
<span data-ttu-id="51ae4-103">Entita SQL je nezávislý na úložišti dotazovací jazyk podobný SQL.</span><span class="sxs-lookup"><span data-stu-id="51ae4-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="51ae4-104">Entita SQL vám umožní provádět dotazy na entity data, jako objekty nebo ve formě tabulky.</span><span class="sxs-lookup"><span data-stu-id="51ae4-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="51ae4-105">Měli byste zvážit použití Entity SQL v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="51ae4-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="51ae4-106">Pokud dotaz musí dynamicky zkonstruovat za běhu.</span><span class="sxs-lookup"><span data-stu-id="51ae4-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="51ae4-107">V takovém případě byste měli také zvážit použití metody Tvůrce dotazů <xref:System.Data.Objects.ObjectQuery%601> místo vytváření Entity SQL řetězec za běhu dotazu.</span><span class="sxs-lookup"><span data-stu-id="51ae4-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="51ae4-108">Pokud chcete definovat dotaz jako součást definice modelu.</span><span class="sxs-lookup"><span data-stu-id="51ae4-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="51ae4-109">V datovém modelu se podporuje jenom Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="51ae4-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="51ae4-110">Další informace najdete v tématu [Element QueryView (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="51ae4-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
-   <span data-ttu-id="51ae4-111">Při použití zprostředkovatel EntityClient pro vrácení dat jen pro čtení entity jako s použitím sady řádků <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="51ae4-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="51ae4-112">Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="51ae4-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="51ae4-113">Pokud jste už jste odborník v jazycích dotazů založených na SQL, se může zdát vám nejvíc fyzické Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="51ae4-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="51ae4-114">Použití se zprostředkovatelem EntityClient Entity SQL</span><span class="sxs-lookup"><span data-stu-id="51ae4-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="51ae4-115">Pokud chcete používat Entity SQL se zprostředkovatelem EntityClient, naleznete v následujících tématech pro další informace:</span><span class="sxs-lookup"><span data-stu-id="51ae4-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="51ae4-116">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="51ae4-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="51ae4-117">Postupy: Sestavení připojovacího řetězce EntityConnection</span><span class="sxs-lookup"><span data-stu-id="51ae4-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="51ae4-118">Postupy: Provedení dotazu, který vrátí výsledky typu PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="51ae4-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="51ae4-119">Postupy: Provedení dotazu, který vrátí výsledky typu StructuralType</span><span class="sxs-lookup"><span data-stu-id="51ae4-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="51ae4-120">Postupy: Provedení dotazu, který vrátí výsledky typu RefType</span><span class="sxs-lookup"><span data-stu-id="51ae4-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="51ae4-121">Postupy: Provedení dotazu, který vrátí komplexní typy</span><span class="sxs-lookup"><span data-stu-id="51ae4-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="51ae4-122">Postupy: Provedení dotazu, který vrátí vnořené kolekce</span><span class="sxs-lookup"><span data-stu-id="51ae4-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="51ae4-123">Postupy: Spuštění parametrizovaného dotazu Entity SQL pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="51ae4-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="51ae4-124">Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="51ae4-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="51ae4-125">Postupy: Spuštění polymorfního dotazu</span><span class="sxs-lookup"><span data-stu-id="51ae4-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="51ae4-126">Postupy: Procházení relací pomocí navigačního operátoru</span><span class="sxs-lookup"><span data-stu-id="51ae4-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="51ae4-127">Pomocí dotazy objektu Entity SQL</span><span class="sxs-lookup"><span data-stu-id="51ae4-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="51ae4-128">Pokud chcete používat Entity SQL pomocí objektu dotazů, naleznete v následujících tématech pro další informace:</span><span class="sxs-lookup"><span data-stu-id="51ae4-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="51ae4-129">Postupy: Provedení dotazu, který vrací objekty typu Entity</span><span class="sxs-lookup"><span data-stu-id="51ae4-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [<span data-ttu-id="51ae4-130">Postupy: Spuštění parametrizovaného dotazu</span><span class="sxs-lookup"><span data-stu-id="51ae4-130">How to: Execute a Parameterized Query</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [<span data-ttu-id="51ae4-131">Postupy: Procházení vztahů pomocí navigačních vlastností</span><span class="sxs-lookup"><span data-stu-id="51ae4-131">How to: Navigate Relationships Using Navigation Properties</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [<span data-ttu-id="51ae4-132">Postupy: Volání uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="51ae4-132">How to: Call a User-Defined Function</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [<span data-ttu-id="51ae4-133">Postupy: Filtrování dat</span><span class="sxs-lookup"><span data-stu-id="51ae4-133">How to: Filter Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [<span data-ttu-id="51ae4-134">Postupy: Řazení dat</span><span class="sxs-lookup"><span data-stu-id="51ae4-134">How to: Sort Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [<span data-ttu-id="51ae4-135">Postupy: Skupiny dat</span><span class="sxs-lookup"><span data-stu-id="51ae4-135">How to: Group Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [<span data-ttu-id="51ae4-136">Postupy: Agregovaná Data</span><span class="sxs-lookup"><span data-stu-id="51ae4-136">How to: Aggregate Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [<span data-ttu-id="51ae4-137">Postupy: Provedení dotazu, který vrací objekty anonymního typu</span><span class="sxs-lookup"><span data-stu-id="51ae4-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [<span data-ttu-id="51ae4-138">Postupy: Provedení dotazu, který vrátí kolekce primitivních typů</span><span class="sxs-lookup"><span data-stu-id="51ae4-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [<span data-ttu-id="51ae4-139">Postupy: Dotaz v objekt EntityCollection související objekty</span><span class="sxs-lookup"><span data-stu-id="51ae4-139">How to: Query Related Objects in an EntityCollection</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [<span data-ttu-id="51ae4-140">Postupy: Pořadí sjednocení dva dotazy</span><span class="sxs-lookup"><span data-stu-id="51ae4-140">How to: Order the Union of Two Queries</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [<span data-ttu-id="51ae4-141">Postupy: Stránkovat výsledky dotazu</span><span class="sxs-lookup"><span data-stu-id="51ae4-141">How to: Page Through Query Results</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a><span data-ttu-id="51ae4-142">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="51ae4-142">In This Section</span></span>  
 [<span data-ttu-id="51ae4-143">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="51ae4-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="51ae4-144">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="51ae4-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="51ae4-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51ae4-145">See also</span></span>

- [<span data-ttu-id="51ae4-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="51ae4-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
- [<span data-ttu-id="51ae4-147">Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="51ae4-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
