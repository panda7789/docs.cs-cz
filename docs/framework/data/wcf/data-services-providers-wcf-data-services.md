---
title: "Data služby zprostředkovatele (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f794088f2494157e22b8551c6241786c7a73398
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="data-services-providers-wcf-data-services"></a>Data služby zprostředkovatele (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]podporuje více modelů zprostředkovatele pro vystavení dat jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu. Toto téma obsahuje informace, které vám umožní vybrat nejlepší [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zprostředkovatele pro zdroj dat.  
  
## <a name="data-source-providers"></a>Zprostředkovatelé zdroje dat  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]podporuje následující zprostředkovatele pro definování datového modelu dat služby.  
  
|Zprostředkovatel|Popis|  
|--------------|-----------------|  
|Zprostředkovatel Entity Framework|Tento zprostředkovatel používá ADO.NET Entity Framework k vám umožní používat relačních dat s datové služby tak, že definujete datového modelu, který se mapuje na relační data. Váš zdroj dat může být SQL Server nebo jakýkoli jiný zdroj dat s podporou zprostředkovatele třetí strany rozhraní Entity Framework. Pokud máte relační datové zdroje, například do databáze systému SQL Server, měli byste použít zprostředkovatele Entity Framework. Další informace najdete v tématu [zprostředkovatele Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).|  
|Reflexe zprostředkovatele|Tento zprostředkovatel používá reflexi k umožňují definovat datový model na základě na existující datových tříd, které mohou být zpřístupněny jako instance <xref:System.Linq.IQueryable%601> rozhraní. Implementací jsou povoleny aktualizace <xref:System.Data.Services.IUpdatable> rozhraní. Tento zprostředkovatel měli použít, když máte statické datových tříd, které jsou definované za běhu, jako jsou ty generované technologie LINQ to SQL nebo definované typové datové sady. Další informace najdete v tématu [reflexe zprostředkovatele](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).|  
|Poskytovatelé služeb vlastních dat|[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zahrnuje sadu poskytovatelů, které vám umožní dynamicky definovat datový model na základě typu dat pozdní vazbu. Pokud se data vystavení není znám, když je navržen aplikace nebo pokud zprostředkovatele Entity Framework nebo reflexe nestačí, měli byste implementovat tato rozhraní. Další informace najdete v tématu [vlastní Data poskytovatelé](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Ostatní poskytovatele dat služeb  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]má následující poskytovatele služeb další data, která vylepšuje výkon zdroje dat, který je definován pomocí jedné z dalších zprostředkovatelů.  
  
|Zprostředkovatel|Popis|  
|--------------|-----------------|  
|Streamování zprostředkovatele|Tento zprostředkovatel umožňuje vystavit binární rozsáhlý objekt datové typy pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Streamování zprostředkovatele je vytvořen pomocí implementace <xref:System.Data.Services.Providers.IDataServiceStreamProvider> rozhraní. Společně s žádné Zprostředkovatel zdroje dat se dá implementovat tohoto zprostředkovatele. Další informace najdete v tématu [streamování zprostředkovatele](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Viz také  
 [Definování datových služeb WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)  
 [Hostující službu Data](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
