---
title: Vlastní zprostředkovatelé datových služeb (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: c5f6bd001a5198f14bf05c0730f3988d54142eae
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569252"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Vlastní zprostředkovatelé datových služeb (WCF Data Services)
WCF Data Services obsahuje sadu zprostředkovatelů, které vám umožní definovat datový model na základě datových typů s pozdní vazbou.  
  
|Zprostředkovatel|Popis|  
|--------------|-----------------|  
|Poskytovatel metadat|Toto je základní poskytovatel vlastní datové služby, který umožňuje definovat vlastní datový model za běhu implementací rozhraní <xref:System.Data.Services.Providers.IDataServiceMetadataProvider>.|  
|Poskytovatel dotazů|Tento poskytovatel vám umožní spouštět dotazy proti vlastnímu datovému modelu definovanému pomocí rozhraní <xref:System.Data.Services.Providers.IDataServiceMetadataProvider>. Poskytovatel dotazu je vytvořen implementací rozhraní <xref:System.Data.Services.Providers.IDataServiceQueryProvider>.|  
|Aktualizovat poskytovatele|Tento poskytovatel vám umožní provádět aktualizace typů, které jsou zpřístupněny ve vlastním poskytovateli datové služby a spravovat souběžnost. Poskytovatel aktualizací je vytvořený implementací rozhraní <xref:System.Data.Services.Providers.IDataServiceUpdateProvider>.|  
|Poskytovatel stránkování|Tento zprostředkovatel se používá u poskytovatele vlastní datové služby k povolení podpory stránkování na základě serveru. Poskytovatel stránkování pro vlastní datovou službu je vytvořen implementací rozhraní <xref:System.Data.Services.Providers.IDataServicePagingProvider>.|  
|Zprostředkovatel streamování|Tento poskytovatel umožňuje vystavit binární datové typy rozsáhlých objektů jako datový proud. Zprostředkovatel streamování se vytvoří implementací rozhraní <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Zprostředkovatele streamování se dá také použít u zprostředkovatelů zdrojů dat Entity Framework a reflexe. Další informace najdete v tématu [poskytovatel streamování](streaming-provider-wcf-data-services.md).|  
  
 Další informace najdete v článku [Vlastní zprostředkovatelé datových služeb](https://go.microsoft.com/fwlink/?LinkID=186850) a sada nástrojů pro zprostředkovatele rozhraní OData (Open Data Protocol) v [sadě OData SDK](https://go.microsoft.com/fwlink/?LinkId=186069).  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé datových služeb](data-services-providers-wcf-data-services.md)
- [Zprostředkovatel Entity Framework](entity-framework-provider-wcf-data-services.md)
- [Zprostředkovatel reflexe](reflection-provider-wcf-data-services.md)
