---
title: "Zápis poskytovatele dat Entity Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 80f425f6e2a9d583ec221b91ae9bb2cd2604ff54
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="b01a5-102">Zápis poskytovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="b01a5-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="b01a5-103">Tato část popisuje, jak napsat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele pro podporu zdroji dat jinými než [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b01a5-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b01a5-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zahrnuje zprostředkovatele, který podporuje [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b01a5-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="b01a5-105">Představení zprostředkovatele modelu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="b01a5-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="b01a5-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Databáze je nezávislá a pomocí modelu zprostředkovatele ADO.NET pro připojení k různého typu zdroje dat můžete napsat zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="b01a5-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="b01a5-107">Zprostředkovatel dat Entity Framework (vytvořen pomocí modelu zprostředkovatel ADO.NET Data Provider) provádí následující funkce:</span><span class="sxs-lookup"><span data-stu-id="b01a5-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="b01a5-108">Mapuje typy zprostředkovatele Entity Data Model (EDM) primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="b01a5-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="b01a5-109">Zpřístupní funkce specifické pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="b01a5-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="b01a5-110">Generuje příkazy specifický pro zprostředkovatele pro danou DbQueryCommandTree pro podporu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="b01a5-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="b01a5-111">Vytvoří příkazy aktualizace specifický pro zprostředkovatele pro danou DbModificationCommandTree pro podporu aktualizací prostřednictvím [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b01a5-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="b01a5-112">Zpřístupňuje mapování soubory pro definici schématu úložiště pro podporu generování modelu na základě databáze.</span><span class="sxs-lookup"><span data-stu-id="b01a5-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="b01a5-113">Zveřejňuje metadata (tabulek a zobrazení, například) prostřednictvím konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="b01a5-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="b01a5-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="b01a5-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="b01a5-115">Ukázka</span><span class="sxs-lookup"><span data-stu-id="b01a5-115">Sample</span></span>  
 <span data-ttu-id="b01a5-116">Najdete v článku [zprostředkovatele Entity Framework ukázka](http://go.microsoft.com/fwlink/?LinkId=180616) ukázkové [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele, který podporuje zdroji dat jinými než [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b01a5-116">See the [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b01a5-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b01a5-117">In This Section</span></span>  
 [<span data-ttu-id="b01a5-118">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="b01a5-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="b01a5-119">Úpravy generování SQL</span><span class="sxs-lookup"><span data-stu-id="b01a5-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="b01a5-120">Specifikace manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="b01a5-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="b01a5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b01a5-121">See Also</span></span>  
 [<span data-ttu-id="b01a5-122">Práce se zprostředkovateli dat</span><span class="sxs-lookup"><span data-stu-id="b01a5-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
