---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 2e0352efdd5b709984338fe4484b120bddb7d545
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164356"
---
# <a name="client"></a>\<client>
`client` Element definuje seznam koncových bodů, které se klient může připojit k.  
  
 \<system.ServiceModel>  
\<client>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Obsahuje kolekci prvků koncového bodu, které určovat koncové body, které tento klient může připojit k.|  
|[\<metadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|Obsahuje nastavení pro zpracování metadat.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Poznámky  
 `client` Oddíl definuje seznam koncových bodů, které se klient může připojit k. Každý koncový bod uvedený v oddílu klienta definuje vlastní vazby, chování a kontrakt. Je jedinečně identifikovaný kombinací `name` a `contract` atributy. Určuje kód klienta `name` pro připojení na koncový bod služby, který implementuje klienta. Pokud `name` atribut je vynechán, koncový bod chová jako výchozího koncového bodu pro kontrakt jej implementuje.  
  
 Kromě toho tato část také určuje nastavení pro zpracování metadat.  
  
## <a name="example"></a>Příklad  
  
```xml  
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [Konfigurace klienta WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [Klienti](../../../../../docs/framework/wcf/feature-details/clients.md)
