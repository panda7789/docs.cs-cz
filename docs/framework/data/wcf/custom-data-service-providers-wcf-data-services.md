---
title: Vlastní zprostředkovatelé datových služeb (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: 4a6079db5e969154c4a9bb6451dd7c698c6d2088
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780382"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Vlastní zprostředkovatelé datových služeb (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsahuje sadu zprostředkovatelů, které vám umožní definovat datový model na základě datových typů s pozdní vazbou.  
  
|Poskytovatel|Popis|  
|--------------|-----------------|  
|Poskytovatel metadat|Toto je základní poskytovatel vlastní datové služby, který umožňuje definovat vlastní datový model za běhu implementací <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> rozhraní.|  
|Poskytovatel dotazů|Tento zprostředkovatel vám umožní spouštět dotazy na základě vlastního datového modelu, který je definován pomocí <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> rozhraní. Poskytovatel dotazu je vytvořen implementací <xref:System.Data.Services.Providers.IDataServiceQueryProvider> rozhraní.|  
|Aktualizovat poskytovatele|Tento poskytovatel vám umožní provádět aktualizace typů, které jsou zpřístupněny ve vlastním poskytovateli datové služby a spravovat souběžnost. Poskytovatel aktualizací je vytvořený implementací <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> rozhraní.|  
|Poskytovatel stránkování|Tento zprostředkovatel se používá u poskytovatele vlastní datové služby k povolení podpory stránkování na základě serveru. Poskytovatel stránkování pro vlastní datovou službu je vytvořen implementací <xref:System.Data.Services.Providers.IDataServicePagingProvider> rozhraní.|  
|Zprostředkovatel streamování|Tento poskytovatel umožňuje vystavit binární datové typy rozsáhlých objektů jako datový proud. Zprostředkovatel streamování se vytvoří implementací <xref:System.Data.Services.Providers.IDataServiceStreamProvider> rozhraní. Zprostředkovatele streamování se dá také použít u zprostředkovatelů zdrojů dat Entity Framework a reflexe. Další informace najdete v tématu [poskytovatel streamování](streaming-provider-wcf-data-services.md).|  
  
 Další informace najdete v článku [Vlastní zprostředkovatelé datových služeb](https://go.microsoft.com/fwlink/?LinkID=186850) a [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] sada Provider Toolkit v sadě [OData SDK](https://go.microsoft.com/fwlink/?LinkId=186069).  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé datových služeb](data-services-providers-wcf-data-services.md)
- [Zprostředkovatel Entity Framework](entity-framework-provider-wcf-data-services.md)
- [Zprostředkovatel reflexe](reflection-provider-wcf-data-services.md)
