---
title: Zápis zprostředkovatele dat Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 50c0555d84c5b5f180c8c49a8419e8a414a4befe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401458"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="05145-102">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="05145-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="05145-103">Tato část popisuje, jak psát [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele pro podporu zdroje dat než SQL Server.</span><span class="sxs-lookup"><span data-stu-id="05145-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="05145-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zahrnuje poskytovatele, který podporuje SQL Server.</span><span class="sxs-lookup"><span data-stu-id="05145-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="05145-105">Představení zprostředkovatele modelu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="05145-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="05145-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nezávisí databáze a zprostředkovatele můžete napsat s využitím podle modelu poskytovatele ADO.NET pro připojení k různorodých zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="05145-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="05145-107">Zprostředkovatel dat Entity Framework (vytvořené pomocí modelu zprostředkovatele dat ADO.NET) provádí následující funkce:</span><span class="sxs-lookup"><span data-stu-id="05145-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="05145-108">Primitivní typy Entity Data Model (EDM) se mapuje na poskytovatele typů.</span><span class="sxs-lookup"><span data-stu-id="05145-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="05145-109">Zpřístupňuje funkce specifické pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="05145-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="05145-110">Generuje příkazy specifickým pro zprostředkovatele pro daného DbQueryCommandTree pro podporu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="05145-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="05145-111">Generuje příkazy specifickým pro zprostředkovatele aktualizace pro danou DbModificationCommandTree podporovat aktualizace prostřednictvím [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05145-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="05145-112">Zpřístupňuje mapování souborů pro definici schématu úložiště pro podporu generování model založený na databázi.</span><span class="sxs-lookup"><span data-stu-id="05145-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="05145-113">Poskytuje metadata (tabulek a zobrazení, například) prostřednictvím konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="05145-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="05145-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="05145-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="05145-115">Ukázka</span><span class="sxs-lookup"><span data-stu-id="05145-115">Sample</span></span>  
 <span data-ttu-id="05145-116">Najdete v článku [ukázka zprostředkovatele Entity Framework](https://go.microsoft.com/fwlink/?LinkId=180616) ukázku [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele, který podporuje zdroje dat než SQL Server.</span><span class="sxs-lookup"><span data-stu-id="05145-116">See the [Entity Framework Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05145-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="05145-117">In This Section</span></span>  
 [<span data-ttu-id="05145-118">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="05145-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="05145-119">Úpravy generování SQL</span><span class="sxs-lookup"><span data-stu-id="05145-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="05145-120">Specifikace manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="05145-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="05145-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="05145-121">See Also</span></span>  
 [<span data-ttu-id="05145-122">Práce se zprostředkovateli dat</span><span class="sxs-lookup"><span data-stu-id="05145-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
