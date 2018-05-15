---
title: Zápis poskytovatele dat Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 578de94aa191d7302b762f1cdc87d4a6810037e3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="d9398-102">Zápis poskytovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d9398-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="d9398-103">Tato část popisuje, jak napsat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele pro podporu zdroje dat než systémy SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9398-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="d9398-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zahrnuje zprostředkovatele, který podporuje SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9398-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="d9398-105">Představení zprostředkovatele modelu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d9398-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="d9398-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Databáze je nezávislá a pomocí modelu zprostředkovatele ADO.NET pro připojení k různého typu zdroje dat můžete napsat zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d9398-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="d9398-107">Zprostředkovatel dat Entity Framework (vytvořen pomocí modelu zprostředkovatel ADO.NET Data Provider) provádí následující funkce:</span><span class="sxs-lookup"><span data-stu-id="d9398-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="d9398-108">Mapuje typy zprostředkovatele Entity Data Model (EDM) primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="d9398-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="d9398-109">Zpřístupní funkce specifické pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d9398-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="d9398-110">Generuje příkazy specifický pro zprostředkovatele pro danou DbQueryCommandTree pro podporu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="d9398-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="d9398-111">Vytvoří příkazy aktualizace specifický pro zprostředkovatele pro danou DbModificationCommandTree pro podporu aktualizací prostřednictvím [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9398-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="d9398-112">Zpřístupňuje mapování soubory pro definici schématu úložiště pro podporu generování modelu na základě databáze.</span><span class="sxs-lookup"><span data-stu-id="d9398-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="d9398-113">Zveřejňuje metadata (tabulek a zobrazení, například) prostřednictvím konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="d9398-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="d9398-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="d9398-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="d9398-115">Ukázka</span><span class="sxs-lookup"><span data-stu-id="d9398-115">Sample</span></span>  
 <span data-ttu-id="d9398-116">Najdete v článku [zprostředkovatele Entity Framework ukázka](http://go.microsoft.com/fwlink/?LinkId=180616) ukázkové [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele, který podporuje zdroje dat než systémy SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9398-116">See the [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9398-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d9398-117">In This Section</span></span>  
 [<span data-ttu-id="d9398-118">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="d9398-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="d9398-119">Úpravy generování SQL</span><span class="sxs-lookup"><span data-stu-id="d9398-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="d9398-120">Specifikace manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="d9398-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="d9398-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9398-121">See Also</span></span>  
 [<span data-ttu-id="d9398-122">Práce se zprostředkovateli dat</span><span class="sxs-lookup"><span data-stu-id="d9398-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
