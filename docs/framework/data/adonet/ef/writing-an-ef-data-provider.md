---
title: Zápis zprostředkovatele dat Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 513af001392ae0b7abe8e6c62dc74f09469b3655
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148441"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="adada-102">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="adada-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="adada-103">Tato část popisuje, jak psát [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele pro podporu zdroje dat než SQL Server.</span><span class="sxs-lookup"><span data-stu-id="adada-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="adada-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zahrnuje poskytovatele, který podporuje SQL Server.</span><span class="sxs-lookup"><span data-stu-id="adada-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="adada-105">Představení zprostředkovatele modelu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="adada-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="adada-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nezávisí databáze a zprostředkovatele můžete napsat s využitím podle modelu poskytovatele ADO.NET pro připojení k různorodých zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="adada-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="adada-107">Zprostředkovatel dat Entity Framework (vytvořené pomocí modelu zprostředkovatele dat ADO.NET) provádí následující funkce:</span><span class="sxs-lookup"><span data-stu-id="adada-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="adada-108">Primitivní typy Entity Data Model (EDM) se mapuje na poskytovatele typů.</span><span class="sxs-lookup"><span data-stu-id="adada-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="adada-109">Zpřístupňuje funkce specifické pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="adada-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="adada-110">Generuje příkazy specifickým pro zprostředkovatele pro daného DbQueryCommandTree pro podporu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="adada-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="adada-111">Generuje příkazy specifickým pro zprostředkovatele aktualizace pro danou DbModificationCommandTree podporovat aktualizace prostřednictvím [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="adada-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="adada-112">Zpřístupňuje mapování souborů pro definici schématu úložiště pro podporu generování model založený na databázi.</span><span class="sxs-lookup"><span data-stu-id="adada-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="adada-113">Poskytuje metadata (tabulek a zobrazení, například) prostřednictvím konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="adada-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="adada-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="adada-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="adada-115">Ukázka</span><span class="sxs-lookup"><span data-stu-id="adada-115">Sample</span></span>  
 <span data-ttu-id="adada-116">Najdete v článku [ukázka zprostředkovatele Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ukázku [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele, který podporuje zdroje dat než SQL Server.</span><span class="sxs-lookup"><span data-stu-id="adada-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="adada-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="adada-117">In This Section</span></span>  
 [<span data-ttu-id="adada-118">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="adada-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="adada-119">Úpravy generování SQL</span><span class="sxs-lookup"><span data-stu-id="adada-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="adada-120">Specifikace manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="adada-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="adada-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="adada-121">See Also</span></span>  
 [<span data-ttu-id="adada-122">Práce se zprostředkovateli dat</span><span class="sxs-lookup"><span data-stu-id="adada-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
