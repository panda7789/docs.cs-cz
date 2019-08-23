---
title: SqlClient pro Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: ec67637c416f2560c1f5d0a9fd0e856703820a84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954971"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="04edd-102">SqlClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="04edd-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="04edd-103">Tato část popisuje .NET Framework Zprostředkovatel dat pro SQL Server (SqlClient), která umožňuje Entity Framework pracovat na Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04edd-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="04edd-104">Atribut schématu poskytovatele</span><span class="sxs-lookup"><span data-stu-id="04edd-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="04edd-105">`Provider`je atributem `Schema` elementu ve službě Store Schema Definition Language (SSDL).</span><span class="sxs-lookup"><span data-stu-id="04edd-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="04edd-106">Chcete-li použít SqlClient, přiřaďte řetězec "System. data. SqlClient" `Provider` do atributu `Schema` elementu.</span><span class="sxs-lookup"><span data-stu-id="04edd-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="04edd-107">ProviderManifestToken – atribut schématu</span><span class="sxs-lookup"><span data-stu-id="04edd-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="04edd-108">`ProviderManifestToken`je vyžadovaný atribut `Schema` elementu v ssdl.</span><span class="sxs-lookup"><span data-stu-id="04edd-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="04edd-109">Tento token slouží k načtení manifestu poskytovatele pro offline scénáře.</span><span class="sxs-lookup"><span data-stu-id="04edd-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="04edd-110">Další informace o `ProviderManifestToken` atributu naleznete v tématu [Schema element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="04edd-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="04edd-111">SqlClient lze použít jako zprostředkovatele dat pro různé verze SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04edd-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="04edd-112">Tyto verze mají různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="04edd-112">These versions have different capabilities.</span></span> <span data-ttu-id="04edd-113">Například SQL Server 2000 `varchar(max)` nepodporuje a `nvarchar(max)` typy, které byly představeny s SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="04edd-113">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="04edd-114">SqlClient vytváří a přijímá následující tokeny manifestu poskytovatele pro různé verze SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04edd-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="04edd-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="04edd-115">SQL Server 2000</span></span>|<span data-ttu-id="04edd-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="04edd-116">SQL Server 2005</span></span>|<span data-ttu-id="04edd-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="04edd-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="04edd-118">2000</span><span class="sxs-lookup"><span data-stu-id="04edd-118">2000</span></span>|<span data-ttu-id="04edd-119">2005</span><span class="sxs-lookup"><span data-stu-id="04edd-119">2005</span></span>|<span data-ttu-id="04edd-120">2008</span><span class="sxs-lookup"><span data-stu-id="04edd-120">2008</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="04edd-121">Počínaje sadou Visual Studio 2010 [nástroje ADO.NET model EDM (Entity Data Model)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) nepodporují SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="04edd-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="04edd-122">Název oboru názvů poskytovatele</span><span class="sxs-lookup"><span data-stu-id="04edd-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="04edd-123">Všichni poskytovatelé musí specifikovat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="04edd-123">All providers must specify a namespace.</span></span> <span data-ttu-id="04edd-124">Tato vlastnost oznamuje Entity Framework, která předpona je používána poskytovatelem pro konkrétní konstrukce, jako jsou typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="04edd-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="04edd-125">Obor názvů manifestů poskytovatele SqlClient je `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="04edd-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="04edd-126">Další informace o oborech názvů najdete v tématu [obory názvů](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="04edd-126">For more information about namespaces, see [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="04edd-127">Typy</span><span class="sxs-lookup"><span data-stu-id="04edd-127">Types</span></span>  
 <span data-ttu-id="04edd-128">Zprostředkovatel SqlClient pro Entity Framework poskytuje informace o mapování mezi typy konceptuálních modelů a typy SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04edd-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="04edd-129">Další informace najdete v tématu [SqlClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="04edd-129">For more information, see [SqlClient for Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="04edd-130">Funkce</span><span class="sxs-lookup"><span data-stu-id="04edd-130">Functions</span></span>  
 <span data-ttu-id="04edd-131">Zprostředkovatel SqlClient pro Entity Framework definuje seznam funkcí podporovaných zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="04edd-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="04edd-132">Seznam podporovaných funkcí najdete v tématu [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="04edd-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04edd-133">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="04edd-133">In This Section</span></span>  
 [<span data-ttu-id="04edd-134">SqlClient pro funkce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="04edd-134">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="04edd-135">SqlClient pro typy Entity Framework</span><span class="sxs-lookup"><span data-stu-id="04edd-135">SqlClient for Entity FrameworkTypes</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="04edd-136">Známé problémy v SqlClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="04edd-136">Known Issues in SqlClient for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="04edd-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04edd-137">See also</span></span>

- [<span data-ttu-id="04edd-138">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="04edd-138">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="04edd-139">Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="04edd-139">Language Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [<span data-ttu-id="04edd-140">Známé problémy ve zprostředkovateli SqlClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="04edd-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
