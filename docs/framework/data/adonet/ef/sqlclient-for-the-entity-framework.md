---
title: SqlClient rozhraní Entity Framework
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 2801ad445be073f2cd4725d04a0c731e8bfcdd1b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="5e162-102">SqlClient rozhraní Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5e162-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="5e162-103">Tato část popisuje zprostředkovatele dat .NET Framework pro SQL Server (SqlClient), která umožňuje rozhraní Entity Framework pracovat prostřednictvím systému Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5e162-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="5e162-104">Atribut schématu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="5e162-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="5e162-105">`Provider` je atributem `Schema` element v store schema definition language (SSDL).</span><span class="sxs-lookup"><span data-stu-id="5e162-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="5e162-106">Chcete-li použít SqlClient, přiřadit řetězec "System.Data.SqlClient" `Provider` atribut `Schema` elementu.</span><span class="sxs-lookup"><span data-stu-id="5e162-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="5e162-107">Atribut ProviderManifestToken schématu</span><span class="sxs-lookup"><span data-stu-id="5e162-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="5e162-108">`ProviderManifestToken` je požadovaný atribut `Schema` element v SSDL.</span><span class="sxs-lookup"><span data-stu-id="5e162-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="5e162-109">Tento token slouží k načtení manifestu zprostředkovatele pro scénáře v režimu offline.</span><span class="sxs-lookup"><span data-stu-id="5e162-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="5e162-110">Další informace o `ProviderManifestToken` atributů najdete v tématu [Element schématu (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222).</span><span class="sxs-lookup"><span data-stu-id="5e162-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222).</span></span>  
  
 <span data-ttu-id="5e162-111">SqlClient můžete použít jako zprostředkovatele dat pro různé verze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5e162-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="5e162-112">Tyto verze mají různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="5e162-112">These versions have different capabilities.</span></span> <span data-ttu-id="5e162-113">Například [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] nepodporuje `varchar(max)` a `nvarchar(max)` typy, které byly zavedeny v [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e162-113">For example, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] does not support `varchar(max)` and `nvarchar(max)` types that were introduced with [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="5e162-114">SqlClient vytváří a přijímá následující tokeny manifestu zprostředkovatele pro různé verze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5e162-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="5e162-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="5e162-115">SQL Server 2000</span></span>|<span data-ttu-id="5e162-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="5e162-116">SQL Server 2005</span></span>|<span data-ttu-id="5e162-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="5e162-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="5e162-118">2000</span><span class="sxs-lookup"><span data-stu-id="5e162-118">2000</span></span>|<span data-ttu-id="5e162-119">2005</span><span class="sxs-lookup"><span data-stu-id="5e162-119">2005</span></span>|<span data-ttu-id="5e162-120">2008</span><span class="sxs-lookup"><span data-stu-id="5e162-120">2008</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="5e162-121">Počínaje [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 2010, [nástrojů modelu ADO.NET Entity Data Model](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) nepodporují systém SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="5e162-121">Starting with [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 2010, the [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="5e162-122">Název zprostředkovatele Namespace</span><span class="sxs-lookup"><span data-stu-id="5e162-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="5e162-123">Všichni poskytovatelé musí specifikovat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="5e162-123">All providers must specify a namespace.</span></span> <span data-ttu-id="5e162-124">Tato vlastnost určuje Entity Framework, která předpona je používána poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="5e162-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="5e162-125">Obor názvů pro manifesty SqlClient zprostředkovatele je `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="5e162-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="5e162-126">Další informace o oborech názvů najdete v tématu [obory názvů](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5e162-126">For more information about namespaces, see [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="5e162-127">Typy</span><span class="sxs-lookup"><span data-stu-id="5e162-127">Types</span></span>  
 <span data-ttu-id="5e162-128">Poskytovatel Sqlclienta rozhraní Entity Framework poskytuje informace o mapování mezi konceptuálního modelu typy a typy systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5e162-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="5e162-129">Další informace najdete v tématu [SqlClient pro Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="5e162-129">For more information, see [SqlClient for Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="5e162-130">Funkce</span><span class="sxs-lookup"><span data-stu-id="5e162-130">Functions</span></span>  
 <span data-ttu-id="5e162-131">Poskytovatel Sqlclienta rozhraní Entity Framework definuje seznam funkcí, které jsou podporována zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="5e162-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="5e162-132">Seznam podporovaných funkcí najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="5e162-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5e162-133">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5e162-133">In This Section</span></span>  
 [<span data-ttu-id="5e162-134">SqlClient pro funkce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5e162-134">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="5e162-135">SqlClient pro typy Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5e162-135">SqlClient for Entity FrameworkTypes</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="5e162-136">Známé problémy v SqlClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5e162-136">Known Issues in SqlClient for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="5e162-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e162-137">See Also</span></span>  
 [<span data-ttu-id="5e162-138">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5e162-138">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [<span data-ttu-id="5e162-139">Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="5e162-139">Language Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)  
 [<span data-ttu-id="5e162-140">Známé problémy v SqlClient zprostředkovatele Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5e162-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
