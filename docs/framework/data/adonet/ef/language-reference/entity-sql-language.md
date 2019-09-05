---
title: Jazyk Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: a2e4b7245dbfccf7864481b52a0e868a85efbca6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251017"
---
# <a name="entity-sql-language"></a><span data-ttu-id="8a481-102">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8a481-102">Entity SQL Language</span></span>
<span data-ttu-id="8a481-103">Entity SQL je dotazovací jazyk nezávislý na úložišti, který se podobá jazyku SQL.</span><span class="sxs-lookup"><span data-stu-id="8a481-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="8a481-104">Entity SQL umožňuje dotazovat se na data entity, a to buď jako objekty, nebo v tabulkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="8a481-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="8a481-105">Měli byste zvážit použití Entity SQL v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="8a481-105">You should consider using Entity SQL in the following cases:</span></span>  
  
- <span data-ttu-id="8a481-106">Když je nutné dotaz dynamicky sestavit za běhu.</span><span class="sxs-lookup"><span data-stu-id="8a481-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="8a481-107">V takovém případě byste měli zvážit také použití metod <xref:System.Data.Objects.ObjectQuery%601> Tvůrce dotazů namísto konstrukce řetězce dotazu Entity SQL za běhu.</span><span class="sxs-lookup"><span data-stu-id="8a481-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
- <span data-ttu-id="8a481-108">Pokud chcete zadat dotaz jako součást definice modelu.</span><span class="sxs-lookup"><span data-stu-id="8a481-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="8a481-109">V datovém modelu se podporuje jenom Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="8a481-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="8a481-110">Další informace naleznete v tématu [QueryView element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="8a481-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
- <span data-ttu-id="8a481-111">Při použití EntityClient k vrácení dat entity jen pro čtení jako sad řádků pomocí <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8a481-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="8a481-112">Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="8a481-112">For more information, see [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span></span>  
  
- <span data-ttu-id="8a481-113">Pokud jste již odborník v jazycích dotazů založených na jazyce SQL, Entity SQL se může zdát, že je to pro vás nejpřirozenější.</span><span class="sxs-lookup"><span data-stu-id="8a481-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="8a481-114">Použití Entity SQL u poskytovatele EntityClient</span><span class="sxs-lookup"><span data-stu-id="8a481-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="8a481-115">Pokud chcete použít Entity SQL u poskytovatele EntityClient, přečtěte si následující témata, kde najdete další informace:</span><span class="sxs-lookup"><span data-stu-id="8a481-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="8a481-116">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8a481-116">EntityClient Provider for the Entity Framework</span></span>](../entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="8a481-117">Postupy: Vytvoření připojovacího řetězce EntityConnection</span><span class="sxs-lookup"><span data-stu-id="8a481-117">How to: Build an EntityConnection Connection String</span></span>](../how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="8a481-118">Postupy: Spustí dotaz, který vrátí výsledky PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="8a481-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="8a481-119">Postupy: Provedení dotazu, který vrátí výsledky StructuralType</span><span class="sxs-lookup"><span data-stu-id="8a481-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="8a481-120">Postupy: Provedení dotazu, který vrátí výsledky RefType</span><span class="sxs-lookup"><span data-stu-id="8a481-120">How to: Execute a Query that Returns RefType Results</span></span>](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="8a481-121">Postupy: Spustí dotaz, který vrátí komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="8a481-121">How to: Execute a Query that Returns Complex Types</span></span>](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="8a481-122">Postupy: Spustit dotaz, který vrátí vnořené kolekce</span><span class="sxs-lookup"><span data-stu-id="8a481-122">How to: Execute a Query that Returns Nested Collections</span></span>](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="8a481-123">Postupy: Provedení parametrizovaného Entity SQLového dotazu pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="8a481-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="8a481-124">Postupy: Provedení parametrizované uložené procedury pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="8a481-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="8a481-125">Postupy: Spustit polymorfní dotaz</span><span class="sxs-lookup"><span data-stu-id="8a481-125">How to: Execute a Polymorphic Query</span></span>](../how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="8a481-126">Postupy: Navigace v relacích pomocí operátoru navigace</span><span class="sxs-lookup"><span data-stu-id="8a481-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="8a481-127">Použití Entity SQL s dotazy na objekty</span><span class="sxs-lookup"><span data-stu-id="8a481-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="8a481-128">Pokud chcete použít Entity SQL s dotazy na objekty, přečtěte si následující témata, kde najdete další informace:</span><span class="sxs-lookup"><span data-stu-id="8a481-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="8a481-129">[Postupy: Spustit dotaz, který vrací objekty typu entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-129">[How to: Execute a Query that Returns Entity Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-130">[Postupy: Provedení parametrizovaného dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-130">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-131">[Postupy: Navigace v relacích pomocí vlastností navigace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-131">[How to: Navigate Relationships Using Navigation Properties](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-132">[Postupy: Volání uživatelsky definované funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-132">[How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-133">[Postupy: Filtrovat data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-133">[How to: Filter Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-134">[Postupy: Seřadit data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-134">[How to: Sort Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-135">[Postupy: Seskupit data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-135">[How to: Group Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-136">[Postupy: Agregovaná data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-136">[How to: Aggregate Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-137">[Postupy: Spustit dotaz, který vrací objekty anonymního typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-137">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-138">[Postupy: Spustí dotaz, který vrátí kolekci primitivních typů.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-138">[How to: Execute a Query that Returns a Collection of Primitive Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-139">[Postupy: Dotazování souvisejících objektů v objektu EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-139">[How to: Query Related Objects in an EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-140">[Postupy: Seřazení sjednocení dvou dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-140">[How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="8a481-141">[Postupy: Stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8a481-141">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a481-142">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8a481-142">In This Section</span></span>  
 [<span data-ttu-id="8a481-143">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8a481-143">Entity SQL Overview</span></span>](entity-sql-overview.md)  
  
 [<span data-ttu-id="8a481-144">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8a481-144">Entity SQL Reference</span></span>](entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="8a481-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a481-145">See also</span></span>

- [<span data-ttu-id="8a481-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8a481-146">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="8a481-147">Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="8a481-147">Language Reference</span></span>](index.md)
