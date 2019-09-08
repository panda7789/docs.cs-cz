---
title: Poskytovatelé Data Services (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: 7623c2b743d6a61362c8cf0e1228b4663c9e7d48
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780386"
---
# <a name="data-services-providers-wcf-data-services"></a>Poskytovatelé Data Services (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]podporuje více modelů poskytovatele pro vystavení dat jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informační kanál. Toto téma poskytuje informace, které vám umožní vybrat nejlepšího [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] poskytovatele pro zdroj dat.  
  
## <a name="data-source-providers"></a>Zprostředkovatelé zdroje dat  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]podporuje následující poskytovatele pro definování datového modelu datové služby.  
  
|Poskytovatel|Popis|  
|--------------|-----------------|  
|Poskytovatel Entity Framework|Tento zprostředkovatel používá Entity Framework ADO.NET k tomu, aby bylo možné používat relační data s datovou službou, a to tak, že definuje datový model, který se mapuje na relační data. Zdroj dat může být SQL Server nebo jakýkoli jiný zdroj dat s podporou poskytovatele třetích stran pro Entity Framework. Poskytovatele Entity Framework byste měli použít, pokud máte relační zdroj dat, jako je například databáze SQL Server. Další informace najdete v tématu [poskytovatel Entity Framework](entity-framework-provider-wcf-data-services.md).|  
|Poskytovatel reflexe|Tento zprostředkovatel používá reflexi k tomu, abyste mohli definovat datový model na základě existujících datových tříd, které mohou být zveřejněny jako <xref:System.Linq.IQueryable%601> instance rozhraní. Aktualizace jsou povoleny implementací <xref:System.Data.Services.IUpdatable> rozhraní. Tohoto poskytovatele byste měli použít, pokud máte statické datové třídy, které jsou definovány za běhu, jako jsou generovány LINQ to SQL nebo definovány typovou datovou sadou. Další informace najdete v tématu [Zprostředkovatel reflexe](reflection-provider-wcf-data-services.md).|  
|Vlastní zprostředkovatelé datových služeb|[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsahuje sadu zprostředkovatelů, které umožňují dynamicky definovat datový model na základě datových typů s pozdní vazbou. Tato rozhraní byste měli implementovat, pokud se Vystavovaná data neznají, když je aplikace navržená, nebo když Entity Framework nebo poskytovatelé reflexe nejsou dostačující. Další informace najdete v tématu [Vlastní poskytovatelé datových služeb](custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Další poskytovatelé datových služeb  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]má následujícího poskytovatele služby Data Service, který vylepšuje výkon zdroje dat definovaného jedním z jiných poskytovatelů.  
  
|Poskytovatel|Popis|  
|--------------|-----------------|  
|Zprostředkovatel streamování|Tento poskytovatel umožňuje vystavit binární datové typy rozsáhlých objektů pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Zprostředkovatel streamování se vytvoří implementací <xref:System.Data.Services.Providers.IDataServiceStreamProvider> rozhraní. Tento zprostředkovatel se dá implementovat spolu s jakýmkoli poskytovatelem zdrojů dat. Další informace najdete v tématu [poskytovatel streamování](streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Konfigurace datové služby](configuring-the-data-service-wcf-data-services.md)
- [Hostování datové služby](hosting-the-data-service-wcf-data-services.md)
