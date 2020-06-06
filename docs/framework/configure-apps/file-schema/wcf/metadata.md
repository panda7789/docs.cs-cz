---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855225"
---
# \<metadata>
Určuje, jak se můžou zpracovávat metadata služby.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|Určuje všechny zásady pro import, které řídí import vlastních výrazů zásad o vazbách. Importér zásad slouží k hledání vlastních kontrolních výrazů zásad o funkcích vazby a také k připojení vlastního elementu vazby, který implementuje funkce vyžadované kontrolním výrazem.|  
|[\<wsdlImporters>](wsdlimporters.md)|Určuje všechny nástroje pro Import WSDL, které importují metadata Web Services Description Language (WSDL) 1,1 s přílohami WS-Policy. Import WSDL slouží k importu metadat a také k převedení těchto informací do různých tříd, které reprezentují informace o kontraktech a koncových bodech. Může selektivně importovat informace o kontraktech a koncových bodech a vlastnosti, které zveřejňují chyby importu a přijímají informace o typu relevantní pro proces importu a převodu. Podporuje také import informací o vazbách a vlastností, které poskytují přístup k jakýmkoli dokumentům zásad, dokumentům WSDL, rozšířením WSDL a dokumentům XML schématu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<client>](client.md)|Oddíl Client definuje seznam koncových bodů, ke kterým se klient může připojit.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [Konfigurace klienta WCF](../../../wcf/feature-details/client-configuration.md)
- [Klienti](../../../wcf/feature-details/clients.md)
