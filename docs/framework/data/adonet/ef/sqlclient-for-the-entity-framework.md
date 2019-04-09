---
title: SqlClient pro Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: d81499961e7e47bba3b2594ddddd192c87a4a936
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195459"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="02259-102">SqlClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="02259-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="02259-103">Tato část popisuje zprostředkovatele dat .NET Framework pro SQL Server (SqlClient), která umožňuje rozhraní Entity Framework pracovat prostřednictvím systému Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="02259-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="02259-104">Atribut schématu poskytovatele</span><span class="sxs-lookup"><span data-stu-id="02259-104">Provider Schema Attribute</span></span>  
 `Provider` <span data-ttu-id="02259-105">je atribut `Schema` prvek store schema definition language (SSDL).</span><span class="sxs-lookup"><span data-stu-id="02259-105">is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="02259-106">Použití SqlClient přiřadit řetězec "System.Data.SqlClient" `Provider` atribut `Schema` elementu.</span><span class="sxs-lookup"><span data-stu-id="02259-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="02259-107">Atribut ProviderManifestToken schématu</span><span class="sxs-lookup"><span data-stu-id="02259-107">ProviderManifestToken Schema Attribute</span></span>  
 `ProviderManifestToken` <span data-ttu-id="02259-108">je povinný atribut `Schema` prvek SSDL.</span><span class="sxs-lookup"><span data-stu-id="02259-108">is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="02259-109">Tento token se používá k načtení manifestu zprostředkovatele pro scénáře v režimu offline.</span><span class="sxs-lookup"><span data-stu-id="02259-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="02259-110">Další informace o `ProviderManifestToken` atributu naleznete v tématu [Element schématu (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="02259-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="02259-111">SqlClient slouží jako zprostředkovatel dat pro různé verze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="02259-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="02259-112">Tyto verze mají různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="02259-112">These versions have different capabilities.</span></span> <span data-ttu-id="02259-113">Například [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] nepodporuje `varchar(max)` a `nvarchar(max)` typy, které byly představeny s nástrojem [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02259-113">For example, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] does not support `varchar(max)` and `nvarchar(max)` types that were introduced with [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="02259-114">SqlClient vytváří a přijímá následující tokeny manifestu zprostředkovatele pro různé verze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="02259-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="02259-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="02259-115">SQL Server 2000</span></span>|<span data-ttu-id="02259-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="02259-116">SQL Server 2005</span></span>|<span data-ttu-id="02259-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="02259-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="02259-118">2000</span><span class="sxs-lookup"><span data-stu-id="02259-118">2000</span></span>|<span data-ttu-id="02259-119">2005</span><span class="sxs-lookup"><span data-stu-id="02259-119">2005</span></span>|<span data-ttu-id="02259-120">2008</span><span class="sxs-lookup"><span data-stu-id="02259-120">2008</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="02259-121">Od verze Visual Studio 2010, [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) nepodporuje SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="02259-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="02259-122">Název zprostředkovatele Namespace</span><span class="sxs-lookup"><span data-stu-id="02259-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="02259-123">Všichni poskytovatelé musí zadat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="02259-123">All providers must specify a namespace.</span></span> <span data-ttu-id="02259-124">Tato vlastnost říká rozhraní Entity Framework, která předpona je používá zprostředkovatel pro konkrétní konstrukce, jako jsou typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="02259-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="02259-125">Obor názvů pro manifesty poskytovatelů SqlClient je `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="02259-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="02259-126">Další informace o oborech názvů najdete v tématu [obory názvů](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="02259-126">For more information about namespaces, see [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="02259-127">Typy</span><span class="sxs-lookup"><span data-stu-id="02259-127">Types</span></span>  
 <span data-ttu-id="02259-128">Zprostředkovatelem SqlClient pro Entity Framework obsahuje informace o mapování mezi typy konceptuálních modelů a typy serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="02259-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="02259-129">Další informace najdete v tématu [SqlClient pro typy Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="02259-129">For more information, see [SqlClient for Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="02259-130">Funkce</span><span class="sxs-lookup"><span data-stu-id="02259-130">Functions</span></span>  
 <span data-ttu-id="02259-131">Zprostředkovatelem SqlClient pro Entity Framework definuje seznam funkcí podporována zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="02259-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="02259-132">Seznam podporovaných funkcí najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="02259-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="02259-133">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="02259-133">In This Section</span></span>  
 [<span data-ttu-id="02259-134">SqlClient pro funkce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="02259-134">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="02259-135">SqlClient pro typy Entity Framework</span><span class="sxs-lookup"><span data-stu-id="02259-135">SqlClient for Entity FrameworkTypes</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="02259-136">Známé problémy v SqlClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="02259-136">Known Issues in SqlClient for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="02259-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02259-137">See also</span></span>

- [<span data-ttu-id="02259-138">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="02259-138">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="02259-139">Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="02259-139">Language Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [<span data-ttu-id="02259-140">Známé problémy v zprostředkovatelem SqlClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="02259-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
