---
title: '&lt;mexHttpsBinding&gt;'
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: ff9ddf8e7486fb8abd174716002575520c546ea4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514352"
---
# <a name="ltmexhttpsbindinggt"></a>&lt;mexHttpsBinding&gt;
Určuje nastavení pro vazby používané k výměně zpráv WS-MetadataExchange (WS-MEX) přes protokol HTTPS.  
  
 \<system.ServiceModel>  
\<vazby >  
\<mexHttpsBinding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<mexHttpsBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexHttpsBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`closeTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`name`|Řetězec, který obsahuje konfigurační název vazby. Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu. Má každá vazba `name` a `namespace` atributů, které dohromady jedinečně identifikovat v metadatech služby. Kromě toho tento název je jedinečný mezi vazby stejného typu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`receiveTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|`sendTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje sadu standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky  
 Tato vazba je v podstatě `WSHttpBinding` vazby, která podporuje zabezpečení na úrovni přenosu pomocí certifikátů. Další informace o konfiguraci a používání těchto koncových bodů metadat najdete v tématu [postupy: Konfigurace vlastního protokolu WS-Metadata Exchange vazby](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [postup: načítání metadat přes vazbu jiného typu než MEX](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)a Ukázka [koncový bod metadat zabezpečení vlastní](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Publikování a načítání metadat prostřednictvím vlastní vazby](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [Postupy: Načítání metadat přes vazbu jiného typu než MEX](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)  
 [Vlastní zabezpečený koncový bod metadat](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 [Metadata](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
