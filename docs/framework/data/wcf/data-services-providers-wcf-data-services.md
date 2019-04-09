---
title: Data Services – zprostředkovatelé (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: 7a870eb0c85fa6ed208341a3ac10dce8bb0724bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164421"
---
# <a name="data-services-providers-wcf-data-services"></a>Data Services – zprostředkovatelé (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporuje několik modelů zprostředkovatele pro vystavení dat jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu. Toto téma obsahuje informace, které vám umožní vybrat nejlepší [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pro zdroj dat poskytovatele.  
  
## <a name="data-source-providers"></a>Zprostředkovatele zdroje dat  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporuje následující zprostředkovatele pro definování datového modelu z datové služby.  
  
|Poskytovatel|Popis|  
|--------------|-----------------|  
|Zprostředkovatele Entity Framework|Tento poskytovatel používá rozhraní ADO.NET Entity Framework umožňuje použití relačních dat se službou data tak, že definujete datový model, který se mapuje na relační data. Zdroj dat může být SQL Server nebo kterýkoli jiný zdroj dat s podporou zprostředkovatele třetí strany pro Entity Framework. Poskytovateli rozhraní Entity Framework by měl použít, pokud máte zdroje relačních dat, jako je například databáze SQL serveru. Další informace najdete v tématu [zprostředkovatele Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).|  
|Zprostředkovatel reflexe|Tento poskytovatel používá reflexi k vám umožňují definovat datový model založený na stávajících datových tříd, které mohou být vystaveny jako instance <xref:System.Linq.IQueryable%601> rozhraní. Aktualizace jsou povolené implementací <xref:System.Data.Services.IUpdatable> rozhraní. Tento poskytovatel by měl použít, pokud máte statických datových tříd, které jsou definovány v době běhu, jako jsou vygenerované pomocí LINQ to SQL nebo určené typové datové sady. Další informace najdete v tématu [zprostředkovatel reflexe](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).|  
|Vlastní zprostředkovatelé datových služeb|[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zahrnuje sadu zprostředkovatelů, které vám umožní dynamicky tak definovat datový model na základě typu dat s pozdní vazbou. Při vystavení dat není znám, když je aplikace navržena, nebo když zprostředkovatele Entity Framework nebo reflexe nejsou dostatečné, měli byste implementovat těchto rozhraní. Další informace najdete v tématu [Vlastní zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Ostatní zprostředkovatelé datových služeb  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] má následujícího poskytovatele služby další data, která vylepšuje výkon zdroj dat definované pomocí jednoho z těchto poskytovatelů.  
  
|Poskytovatel|Popis|  
|--------------|-----------------|  
|Zprostředkovatel streamování|Tento zprostředkovatel umožňuje vystavit binární rozsáhlý objekt datové typy s použitím [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Zprostředkovatel streamování je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServiceStreamProvider> rozhraní. Spolu s jakékoli Zprostředkovatel zdroje dat je možné implementovat tohoto zprostředkovatele. Další informace najdete v tématu [streamování poskytovatele](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Viz také:

- [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
- [Hostování datové služby](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
