---
title: Zápis zprostředkovatele dat Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 6c5e6e2859b48db6c982862381d223a4c9deb2c5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248190"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="0c0ce-102">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="0c0ce-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="0c0ce-103">Tato část popisuje, jak napsat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] poskytovatele pro podporu jiného zdroje dat než SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="0c0ce-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsahuje poskytovatele, který podporuje SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="0c0ce-105">Představení modelu poskytovatele Entity Framework</span><span class="sxs-lookup"><span data-stu-id="0c0ce-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="0c0ce-106">Je [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nezávislá na databázi a můžete napsat poskytovatele pomocí modelu poskytovatele ADO.NET pro připojení k různorodé sadě zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="0c0ce-107">Poskytovatel dat Entity Framework (sestavený pomocí modelu Zprostředkovatel dat ADO.NET) provádí následující funkce:</span><span class="sxs-lookup"><span data-stu-id="0c0ce-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
- <span data-ttu-id="0c0ce-108">Mapuje primitivní typy model EDM (Entity Data Model) (EDM) na typy poskytovatelů.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
- <span data-ttu-id="0c0ce-109">Zpřístupňuje funkce specifické pro poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-109">Exposes provider-specific functions.</span></span>  
  
- <span data-ttu-id="0c0ce-110">Vygeneruje pro určitý DbQueryCommandTree příkazy specifické pro konkrétního zprostředkovatele [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pro podporu dotazů.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
- <span data-ttu-id="0c0ce-111">Vygeneruje příkazy aktualizace specifické pro konkrétního poskytovatele pro daný DbModificationCommandTree pro podporu aktualizací [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
- <span data-ttu-id="0c0ce-112">Zpřístupňuje soubory mapování pro definici schématu úložiště, aby bylo možné podporovat generaci modelu založeného na databázi.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
- <span data-ttu-id="0c0ce-113">Zpřístupňuje metadata (například tabulky a zobrazení) prostřednictvím koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="0c0ce-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="0c0ce-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="0c0ce-115">Ukázka</span><span class="sxs-lookup"><span data-stu-id="0c0ce-115">Sample</span></span>  
 <span data-ttu-id="0c0ce-116">Ukázku[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele, který podporuje jiný zdroj dat než SQL Server, najdete v tématu [poskytovatel ukázek Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) .</span><span class="sxs-lookup"><span data-stu-id="0c0ce-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c0ce-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0c0ce-117">In This Section</span></span>  
 [<span data-ttu-id="0c0ce-118">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="0c0ce-118">SQL Generation</span></span>](sql-generation.md)  
  
 [<span data-ttu-id="0c0ce-119">Úpravy generování SQL</span><span class="sxs-lookup"><span data-stu-id="0c0ce-119">Modification SQL Generation</span></span>](modification-sql-generation.md)  
  
 [<span data-ttu-id="0c0ce-120">Specifikace manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="0c0ce-120">Provider Manifest Specification</span></span>](provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c0ce-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c0ce-121">See also</span></span>

- [<span data-ttu-id="0c0ce-122">Práce se zprostředkovateli dat</span><span class="sxs-lookup"><span data-stu-id="0c0ce-122">Working with Data Providers</span></span>](working-with-data-providers.md)
