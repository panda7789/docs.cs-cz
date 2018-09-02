---
title: Vlastní zprostředkovatelé datových služeb (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: 9c4b3fa3a706f8dc0ff072520dd91a74bc9d0a2c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43457224"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Vlastní zprostředkovatelé datových služeb (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zahrnuje sadu poskytovatele, který vám umožní definovat datový model na základě typu dat s pozdní vazbou.  
  
|Zprostředkovatel|Popis|  
|--------------|-----------------|  
|Zprostředkovatel metadat|To je poskytovatel služby vlastních dat core, která vám umožní definovat vlastní datový model v době běhu implementací <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> rozhraní.|  
|Poskytovatele dotazů|Tento zprostředkovatel umožňuje spouštění dotazů na vlastní datový model, který je definován pomocí <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> rozhraní. Zprostředkovateli dotazu je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServiceQueryProvider> rozhraní.|  
|Aktualizovat zprostředkovatele|Tento zprostředkovatel vám umožní provádět aktualizace na typy, které jsou přístupné na vlastní data poskytovatele služeb a ke správě souběžnosti. Aktualizace poskytovatele se vytvoří pomocí implementace <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> rozhraní|  
|Zprostředkovatel stránkování|Tento zprostředkovatel se používá u poskytovatele služeb vlastních dat k povolení podpory stránkování řízené serverem. Stránkování zprostředkovatele pro vlastní datové služby je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServicePagingProvider> rozhraní.|  
|Zprostředkovatel streamování|Tento zprostředkovatel umožňuje vystavit binární rozsáhlý objekt datové typy jako datový proud. Zprostředkovatel streamování je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServiceStreamProvider> rozhraní. Zprostředkovatel streamování lze také pomocí zprostředkovatele zdroje dat Entity Framework a reflexe. Další informace najdete v tématu [streamování poskytovatele](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
 Další informace najdete v článku [Vlastní zprostředkovatelé datových služeb](https://go.microsoft.com/fwlink/?LinkID=186850) a [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] sada nástrojů pro poskytovatele v [OData SDK](https://go.microsoft.com/fwlink/?LinkId=186069).  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Zprostředkovatel Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
 [Zprostředkovatel reflexe](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
