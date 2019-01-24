---
title: Generování klientské knihovny datové služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: b550af85bcd4bec30707721c6549c7b9094bfd1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630902"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Generování klientské knihovny datové služby (WCF Data Services)
Datové služby, který implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] může vrátit metadata dokumentu služby, které popisují datový model vystavené [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu. Další informace najdete v tématu [OData: Dokument metadat služby](https://go.microsoft.com/fwlink/?LinkId=186070). Můžete použít **přidat odkaz na službu** dialogového okna v sadě Visual Studio se přidat odkaz na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby. Při použití tohoto nástroje se přidat odkaz na metadata vrácený [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu klientský projekt, provede následující akce:  
  
-   Požadavky služby dokument metadat z datové služby a interpretuje vrácených metadat.  
  
    > [!NOTE]
    >  Vrácené metadata jsou uložena v klientském projektu jako soubor .edmx. Nelze otevřít tento soubor .edmx s použitím modelu Entity Data Model designer, protože nemá stejný formát souboru .edmx používá Entity Framework. Zobrazí se tento soubor metadat pomocí editoru XML nebo libovolného textového editoru. Další informace najdete v tématu [ \[MC EDMX\]: Model Entity Data Model pro formát dat služby balení](https://go.microsoft.com/fwlink/?LinkID=178833) specifikace  
  
-   Generuje reprezentaci služby jako třídu kontejneru entity, která dědí z <xref:System.Data.Services.Client.DataServiceContext>. Tato třída kontejneru generované entity se podobá kontejneru entity, které generují nástroje modelu Entity Data Model. Další informace najdete v tématu [Přehled služby objektů (Entity Framework)](https://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
-   Vygeneruje třídy dat pro datové typy modelů, které zjistí v metadata služby.  
  
-   Přidá odkaz na `System.Data.Services.Client` sestavení do projektu.  
  
 Další informace najdete v tématu [jak: Přidání odkazu na datovou službu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Tříd klientské datové služby může být také generovány pomocí [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) nástroj příkazového řádku. Další informace najdete v tématu [jak: Ruční generování tříd klientské datové služby](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>Mapování datového typu klienta  
 Při použití **přidat odkaz na službu** dialogového okna v sadě Visual Studio nebo `DataSvcUtil.exe` nástroj pro generování klienta datových tříd, které jsou založeny na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu, datové typy rozhraní .NET Framework, které jsou mapovány na primitivní typy z datový model následujícím způsobem:  
  
|Typ datového modelu|Datový typ rozhraní .NET framework|  
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
  
 Další informace najdete v tématu [OData: Primitivní datové typy](https://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Viz také:
- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Rychlý start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
