---
title: "Generování dat služby klientské knihovny (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72b75451d69e107b78152b301027f902ff77a25d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Generování dat služby klientské knihovny (služby WCF Data Services)
Služba data, která implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] může vrátit dokument metadat služby, který popisuje datový model vystavené [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu. Další informace najdete v tématu [OData: dokument metadat služby](http://go.microsoft.com/fwlink/?LinkId=186070). Můžete použít **přidat odkaz na službu** dialogové okno v sadě Visual Studio se přidat odkaz na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby. Při použití tohoto nástroje se přidat odkaz na metadata vrácený [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu v projektu klienta, provede následující akce:  
  
-   Požadavky služby dokument metadat ze služby data a interpretuje Vrácená metadata.  
  
    > [!NOTE]
    >  Vrácená metadata se ukládají do projektu klienta do souboru .edmx. Tento soubor EDMX nelze otevřít pomocí návrháře datového modelu Entity, protože nemá stejný formátu souboru .edmx používá rozhraní Entity Framework. Tento soubor metadat můžete zobrazit pomocí editoru XML nebo libovolného textového editoru. Další informace najdete v tématu [ \[MC EDMX\]: datového modelu Entity pro formát dat služby balení](http://go.microsoft.com/fwlink/?LinkID=178833) specifikace  
  
-   Generuje reprezentaci služby jako třída kontejneru entit, která dědí z <xref:System.Data.Services.Client.DataServiceContext>. Tato třída kontejneru generovaného entity se podobá kontejneru entit, který generovat nástroje modelu Entity Data Model. Další informace najdete v tématu [přehled služeb objektů (rozhraní Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
-   V metadatech service generuje datové třídy pro datové typy modelu, které zjistí.  
  
-   Přidá odkaz na `System.Data.Services.Client` sestavení do projektu.  
  
 Další informace najdete v tématu [postupy: Přidání odkazu na službu Data](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Třídy klienta dat služby také může být generována pomocí [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) nástroje příkazového řádku. Další informace najdete v tématu [postupy: ruční generování dat služby třídy klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>Mapování datového typu klienta  
 Při použití **přidat odkaz na službu** dialogové okno v sadě Visual Studio nebo `DataSvcUtil.exe` nástroj pro generování klienta datových tříd, které jsou založeny na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu, rozhraní .NET Framework datové typy jsou namapované na primitivní typy z datový model následujícím způsobem:  
  
|Typ modelu dat|Datový typ rozhraní .NET framework|  
|---------------------|------------------------------|  
|`Edm.Binary`|<xref:System.Byte>`[]`|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 Další informace najdete v tématu [OData: primitivní datové typy](http://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Rychlý start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
