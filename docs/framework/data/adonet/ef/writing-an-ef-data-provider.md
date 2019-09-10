---
title: Zápis zprostředkovatele dat Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 29aa8cb1c6b31d9ada6b01860d76bcf03d37416c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854160"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="de7f6-102">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="de7f6-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="de7f6-103">Tato část popisuje, jak napsat poskytovatele Entity Framework pro podporu jiného zdroje dat než SQL Server.</span><span class="sxs-lookup"><span data-stu-id="de7f6-103">This section discusses how to write an Entity Framework provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="de7f6-104">Entity Framework obsahuje poskytovatele, který podporuje SQL Server.</span><span class="sxs-lookup"><span data-stu-id="de7f6-104">The Entity Framework includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="de7f6-105">Představení modelu poskytovatele Entity Framework</span><span class="sxs-lookup"><span data-stu-id="de7f6-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="de7f6-106">Entity Framework je nezávislá na databázi a můžete napsat poskytovatele pomocí modelu poskytovatele ADO.NET pro připojení k různorodé sadě zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="de7f6-106">The Entity Framework is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="de7f6-107">Poskytovatel dat Entity Framework (sestavený pomocí modelu Zprostředkovatel dat ADO.NET) provádí následující funkce:</span><span class="sxs-lookup"><span data-stu-id="de7f6-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
- <span data-ttu-id="de7f6-108">Mapuje primitivní typy model EDM (Entity Data Model) (EDM) na typy poskytovatelů.</span><span class="sxs-lookup"><span data-stu-id="de7f6-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
- <span data-ttu-id="de7f6-109">Zpřístupňuje funkce specifické pro poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="de7f6-109">Exposes provider-specific functions.</span></span>  
  
- <span data-ttu-id="de7f6-110">Vygeneruje pro určitý DbQueryCommandTree příkazy specifické pro zprostředkovatele, aby podporovaly Entity Framework dotazy.</span><span class="sxs-lookup"><span data-stu-id="de7f6-110">Generates provider-specific commands for a given DbQueryCommandTree to support Entity Framework queries.</span></span>  
  
- <span data-ttu-id="de7f6-111">Vygeneruje příkazy aktualizace specifické pro konkrétního poskytovatele pro daný DbModificationCommandTree pro podporu aktualizací prostřednictvím Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="de7f6-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the Entity Framework.</span></span>  
  
- <span data-ttu-id="de7f6-112">Zpřístupňuje soubory mapování pro definici schématu úložiště, aby bylo možné podporovat generaci modelu založeného na databázi.</span><span class="sxs-lookup"><span data-stu-id="de7f6-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
- <span data-ttu-id="de7f6-113">Zpřístupňuje metadata (například tabulky a zobrazení) prostřednictvím koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="de7f6-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="de7f6-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="de7f6-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="de7f6-115">Ukázka</span><span class="sxs-lookup"><span data-stu-id="de7f6-115">Sample</span></span>  
 <span data-ttu-id="de7f6-116">Ukázku poskytovatele Entity Framework, který podporuje jiný zdroj dat než SQL Server, najdete v tématu [poskytovatel ukázkového Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) .</span><span class="sxs-lookup"><span data-stu-id="de7f6-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an Entity Framework provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de7f6-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="de7f6-117">In This Section</span></span>  
 [<span data-ttu-id="de7f6-118">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="de7f6-118">SQL Generation</span></span>](sql-generation.md)  
  
 [<span data-ttu-id="de7f6-119">Úpravy generování SQL</span><span class="sxs-lookup"><span data-stu-id="de7f6-119">Modification SQL Generation</span></span>](modification-sql-generation.md)  
  
 [<span data-ttu-id="de7f6-120">Specifikace manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="de7f6-120">Provider Manifest Specification</span></span>](provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="de7f6-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de7f6-121">See also</span></span>

- [<span data-ttu-id="de7f6-122">Práce se zprostředkovateli dat</span><span class="sxs-lookup"><span data-stu-id="de7f6-122">Working with Data Providers</span></span>](working-with-data-providers.md)
