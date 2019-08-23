---
title: Generování klientské knihovny datové služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 14ea550715c1b224945137f123eed3b53e56cead
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918640"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Generování klientské knihovny datové služby (WCF Data Services)
Datová služba, která implementuje rozhraní [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] , může vracet dokument metadat služby, který popisuje datový model vystavený [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačním kanálem. Další informace najdete v tématu [OData: Dokument](https://go.microsoft.com/fwlink/?LinkId=186070)metadat služby Pomocí dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio můžete přidat odkaz na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]službu založenou na službě. Při použití tohoto nástroje k přidání odkazu na metadata vrácená [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačním kanálem v klientském projektu provede následující akce:  
  
- Požádá o dokument metadat služby z datové služby a interpretuje vrácená metadata.  
  
    > [!NOTE]
    > Vrácená metadata jsou uložena v projektu klienta jako soubor. edmx. Tento soubor. edmx nejde otevřít pomocí návrháře model EDM (Entity Data Model), protože nemá stejný formát jako soubor. edmx, který používá Entity Framework. Tento soubor metadat můžete zobrazit pomocí editoru XML nebo libovolného textového editoru. Další informace najdete v tématu [ \[MC-EDMX\]: Specifikace formátu](https://go.microsoft.com/fwlink/?LinkID=178833) balíčku pro Data Services model EDM (Entity Data Model)  
  
- Generuje reprezentace služby jako třídu kontejneru entity, ze <xref:System.Data.Services.Client.DataServiceContext>které dědí. Tato generovaná třída kontejneru entity se podobá kontejneru entit, který generují nástroje model EDM (Entity Data Model). Další informace najdete v tématu [Přehled služby Object Services (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
- Generuje datové třídy pro typy datových modelů, které zjišťuje v metadatech služby.  
  
- Přidá do projektu odkaz na `System.Data.Services.Client` sestavení.  
  
 Další informace najdete v tématu [jak: Přidejte odkaz](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)na datovou službu.  
  
 Třídy klientské datové služby je také možné vygenerovat pomocí nástroje [DataSvcUtil. exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) v příkazovém řádku. Další informace najdete v tématu [jak: Ručně vygenerujte třídy](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)datové služby klienta.  
  
## <a name="client-data-type-mapping"></a>Mapování datových typů klienta  
 Při použití dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio nebo `DataSvcUtil.exe` v nástroji ke generování datových tříd klienta, které [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jsou založeny na informačním kanálu, jsou .NET Framework datové typy mapovány na primitivní typy z datového modelu následujícím způsobem:  
  
|Typ datového modelu|.NET Framework datový typ|  
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
