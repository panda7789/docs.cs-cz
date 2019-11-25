---
title: Generování klientské knihovny datové služby (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: f73ea93fe76f31c81935dbfb29183c247e41d8cd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975276"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Generování klientské knihovny datové služby (WCF Data Services)
Datová služba, která implementuje protokol OData (Open Data Protocol), může vrátit dokument metadat služby, který popisuje datový model vystavený datovým kanálem OData. Další informace najdete v [dokumentu metadata služby OData:](https://go.microsoft.com/fwlink/?LinkId=186070). Pomocí dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio můžete přidat odkaz na službu OData. Při použití tohoto nástroje k přidání odkazu na metadata vrácená kanálem OData v klientském projektu provede následující akce:  
  
- Požádá o dokument metadat služby z datové služby a interpretuje vrácená metadata.  
  
    > [!NOTE]
    > Vrácená metadata jsou uložena v projektu klienta jako soubor. edmx. Tento soubor. edmx nejde otevřít pomocí návrháře model EDM (Entity Data Model), protože nemá stejný formát jako soubor. edmx, který používá Entity Framework. Tento soubor metadat můžete zobrazit pomocí editoru XML nebo libovolného textového editoru. Další informace najdete v tématu [\[MC-EDMX\]: model EDM (Entity Data Model) pro specifikaci formátu balíčku Data Services.](https://go.microsoft.com/fwlink/?LinkID=178833)  
  
- Generuje reprezentace služby jako třídu kontejneru entity, která dědí z <xref:System.Data.Services.Client.DataServiceContext>. Tato generovaná třída kontejneru entity se podobá kontejneru entit, který generují nástroje model EDM (Entity Data Model). Další informace najdete v tématu [Přehled služby Object Services (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
- Generuje datové třídy pro typy datových modelů, které zjišťuje v metadatech služby.  
  
- Přidá do projektu odkaz na `System.Data.Services.Client` sestavení.  
  
 Další informace najdete v tématu [Postup: Přidání odkazu na datovou službu](how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Třídy klientské datové služby je také možné vygenerovat pomocí nástroje [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) v příkazovém řádku. Další informace najdete v tématu [Postup: ruční generování tříd klientských datových služeb](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>Mapování datových typů klienta  
 Při použití dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio nebo nástroje `DataSvcUtil.exe` k vygenerování tříd dat klienta, které jsou založeny na datovém kanálu OData, jsou .NET Framework datové typy mapovány na primitivní typy z datového modelu následujícím způsobem:  
  
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
  
 Další informace najdete v tématu [datové typy OData: primitiv](https://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Rychlý start](quickstart-wcf-data-services.md)
