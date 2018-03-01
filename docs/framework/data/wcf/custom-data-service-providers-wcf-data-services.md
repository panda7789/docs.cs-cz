---
title: "Poskytovatelé služeb vlastních dat (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d7db780b97c1a7eadffbfa71f60be4afe590ccb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-data-service-providers-wcf-data-services"></a><span data-ttu-id="99c64-102">Poskytovatelé služeb vlastních dat (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="99c64-102">Custom Data Service Providers (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="99c64-103">zahrnuje sadu poskytovatelů, která umožňuje definovat datový model na základě typu dat pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="99c64-103"> includes a set of providers that enables you to define a data model based on late-bound data types.</span></span>  
  
|<span data-ttu-id="99c64-104">Zprostředkovatel</span><span class="sxs-lookup"><span data-stu-id="99c64-104">Provider</span></span>|<span data-ttu-id="99c64-105">Popis</span><span class="sxs-lookup"><span data-stu-id="99c64-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="99c64-106">Zprostředkovatel metadat</span><span class="sxs-lookup"><span data-stu-id="99c64-106">Metadata provider</span></span>|<span data-ttu-id="99c64-107">Toto je základní poskytovatele služeb vlastních dat, který umožňuje definovat vlastní datový model v době běhu implementací <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="99c64-107">This is the core custom data service provider that enables you to define a custom data model at runtime by implementing the <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.</span></span>|  
|<span data-ttu-id="99c64-108">Dotaz na zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="99c64-108">Query provider</span></span>|<span data-ttu-id="99c64-109">Tento zprostředkovatel umožňuje spouštět dotazy na vlastní datový model, který je definován pomocí <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="99c64-109">This provider enables you to execute queries against a custom data model that is defined by using the <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.</span></span> <span data-ttu-id="99c64-110">Dotaz na zprostředkovatele je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServiceQueryProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="99c64-110">The query provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceQueryProvider> interface.</span></span>|  
|<span data-ttu-id="99c64-111">Aktualizujte zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="99c64-111">Update provider</span></span>|<span data-ttu-id="99c64-112">Tento zprostředkovatel můžete provést aktualizace typy, které jsou zveřejněné v vlastních dat poskytovatele služeb a ke správě souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="99c64-112">This provider enables you to make updates to types that are exposed in a custom data service provider and to manage concurrency.</span></span> <span data-ttu-id="99c64-113">Poskytovatele aktualizaci je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> rozhraní</span><span class="sxs-lookup"><span data-stu-id="99c64-113">An update provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> interface</span></span>|  
|<span data-ttu-id="99c64-114">Zprostředkovatel stránkování</span><span class="sxs-lookup"><span data-stu-id="99c64-114">Paging provider</span></span>|<span data-ttu-id="99c64-115">Tento zprostředkovatel se používá u poskytovatele služby vlastních dat k povolení podpory stránkování řízené serverem.</span><span class="sxs-lookup"><span data-stu-id="99c64-115">This provider is used with the custom data service provider to enable server-driven paging support.</span></span> <span data-ttu-id="99c64-116">Stránkování poskytovatele pro vlastní datové služby je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServicePagingProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="99c64-116">A paging provider for a custom data service is created by implementing the <xref:System.Data.Services.Providers.IDataServicePagingProvider> interface.</span></span>|  
|<span data-ttu-id="99c64-117">Streamování zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="99c64-117">Streaming provider</span></span>|<span data-ttu-id="99c64-118">Tento zprostředkovatel umožňuje vystavit binární rozsáhlý objekt datové typy jako datový proud.</span><span class="sxs-lookup"><span data-stu-id="99c64-118">This provider enables you to expose binary large object data types as a stream.</span></span> <span data-ttu-id="99c64-119">Streamování zprostředkovatele je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServiceStreamProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="99c64-119">A streaming provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interface.</span></span> <span data-ttu-id="99c64-120">Streamování zprostředkovatele můžete použít taky s zprostředkovatele zdrojů dat Entity Framework a reflexe.</span><span class="sxs-lookup"><span data-stu-id="99c64-120">The streaming provider can also be used with Entity Framework and reflection data source providers.</span></span> <span data-ttu-id="99c64-121">Další informace najdete v tématu [streamování zprostředkovatele](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="99c64-121">For more information, see [Streaming Provider](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).</span></span>|  
  
 <span data-ttu-id="99c64-122">Další informace najdete v článku [vlastní Data poskytovatelé](http://go.microsoft.com/fwlink/?LinkID=186850) a [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Toolkit zprostředkovatele v [OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069).</span><span class="sxs-lookup"><span data-stu-id="99c64-122">For more information, see the article [Custom Data Service Providers](http://go.microsoft.com/fwlink/?LinkID=186850) and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Provider Toolkit in the [OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c64-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="99c64-123">See Also</span></span>  
 [<span data-ttu-id="99c64-124">Zprostředkovatelé datových služeb</span><span class="sxs-lookup"><span data-stu-id="99c64-124">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="99c64-125">Zprostředkovatel Entity Framework</span><span class="sxs-lookup"><span data-stu-id="99c64-125">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
 [<span data-ttu-id="99c64-126">Zprostředkovatel reflexe</span><span class="sxs-lookup"><span data-stu-id="99c64-126">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
