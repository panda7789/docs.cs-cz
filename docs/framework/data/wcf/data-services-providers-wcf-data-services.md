---
title: Poskytovatelé Data Services (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: eb7d92b1605c6ced8319e0372c8471cd4e388cb8
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569231"
---
# <a name="data-services-providers-wcf-data-services"></a>Poskytovatelé Data Services (WCF Data Services)
WCF Data Services podporuje více modelů poskytovatele pro vystavení dat jako informační kanál OData (Open Data Protocol). Toto téma poskytuje informace, které vám umožní vybrat nejlepšího poskytovatele WCF Data Services pro zdroj dat.  
  
## <a name="data-source-providers"></a>Zprostředkovatelé zdroje dat  
 WCF Data Services podporuje následující poskytovatele pro definování datového modelu datové služby.  
  
|Zprostředkovatel|Popis|  
|--------------|-----------------|  
|Poskytovatel Entity Framework|Tento zprostředkovatel používá Entity Framework ADO.NET k tomu, aby bylo možné používat relační data s datovou službou, a to tak, že definuje datový model, který se mapuje na relační data. Zdroj dat může být SQL Server nebo jakýkoli jiný zdroj dat s podporou poskytovatele třetích stran pro Entity Framework. Poskytovatele Entity Framework byste měli použít, pokud máte relační zdroj dat, jako je například databáze SQL Server. Další informace najdete v tématu [poskytovatel Entity Framework](entity-framework-provider-wcf-data-services.md).|  
|Poskytovatel reflexe|Tento zprostředkovatel používá reflexi k tomu, abyste mohli definovat datový model na základě existujících datových tříd, které mohou být vystaveny jako instance <xref:System.Linq.IQueryable%601>ho rozhraní. Aktualizace jsou povoleny implementací rozhraní <xref:System.Data.Services.IUpdatable>. Tohoto poskytovatele byste měli použít, pokud máte statické datové třídy, které jsou definovány za běhu, jako jsou generovány LINQ to SQL nebo definovány typovou datovou sadou. Další informace najdete v tématu [Zprostředkovatel reflexe](reflection-provider-wcf-data-services.md).|  
|Vlastní zprostředkovatelé datových služeb|WCF Data Services obsahuje sadu zprostředkovatelů, které vám umožní dynamicky definovat datový model na základě datových typů s pozdní vazbou. Tato rozhraní byste měli implementovat, pokud se Vystavovaná data neznají, když je aplikace navržená, nebo když Entity Framework nebo poskytovatelé reflexe nejsou dostačující. Další informace najdete v tématu [Vlastní poskytovatelé datových služeb](custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Další poskytovatelé datových služeb  
 WCF Data Services má následujícího poskytovatele datových služeb, který vylepšuje výkon zdroje dat definovaného jedním z jiných poskytovatelů.  
  
|Zprostředkovatel|Popis|  
|--------------|-----------------|  
|Zprostředkovatel streamování|Tento poskytovatel vám umožňuje vystavit binární datové typy rozsáhlých objektů pomocí WCF Data Services. Zprostředkovatel streamování se vytvoří implementací rozhraní <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Tento zprostředkovatel se dá implementovat spolu s jakýmkoli poskytovatelem zdrojů dat. Další informace najdete v tématu [poskytovatel streamování](streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Konfigurace datové služby](configuring-the-data-service-wcf-data-services.md)
- [Hostování datové služby](hosting-the-data-service-wcf-data-services.md)
