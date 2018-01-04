---
title: "Poskytovatelé služeb vlastních dat (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7db780b97c1a7eadffbfa71f60be4afe590ccb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Poskytovatelé služeb vlastních dat (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zahrnuje sadu poskytovatelů, která umožňuje definovat datový model na základě typu dat pozdní vazbu.  
  
|Zprostředkovatel|Popis|  
|--------------|-----------------|  
|Zprostředkovatel metadat|Toto je základní poskytovatele služeb vlastních dat, který umožňuje definovat vlastní datový model v době běhu implementací <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> rozhraní.|  
|Dotaz na zprostředkovatele|Tento zprostředkovatel umožňuje spouštět dotazy na vlastní datový model, který je definován pomocí <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> rozhraní. Dotaz na zprostředkovatele je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServiceQueryProvider> rozhraní.|  
|Aktualizujte zprostředkovatele|Tento zprostředkovatel můžete provést aktualizace typy, které jsou zveřejněné v vlastních dat poskytovatele služeb a ke správě souběžnosti. Poskytovatele aktualizaci je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> rozhraní|  
|Zprostředkovatel stránkování|Tento zprostředkovatel se používá u poskytovatele služby vlastních dat k povolení podpory stránkování řízené serverem. Stránkování poskytovatele pro vlastní datové služby je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServicePagingProvider> rozhraní.|  
|Streamování zprostředkovatele|Tento zprostředkovatel umožňuje vystavit binární rozsáhlý objekt datové typy jako datový proud. Streamování zprostředkovatele je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServiceStreamProvider> rozhraní. Streamování zprostředkovatele můžete použít taky s zprostředkovatele zdrojů dat Entity Framework a reflexe. Další informace najdete v tématu [streamování zprostředkovatele](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
 Další informace najdete v článku [vlastní Data poskytovatelé](http://go.microsoft.com/fwlink/?LinkID=186850) a [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Toolkit zprostředkovatele v [OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069).  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Zprostředkovatel Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
 [Zprostředkovatel reflexe](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
