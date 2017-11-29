---
title: '&lt;klienta&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 67f91f4462fc8c11b1769d5805a4ad1407385a50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientgt"></a>&lt;klienta&gt;
`client` Element definuje seznam koncových bodů, které klient může připojit k.  
  
 \<systém. ServiceModel >  
\<klient >  
  
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
|[\<koncový bod >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Obsahuje kolekci elementů koncový bod, které určují koncové body, které tento klient může připojit k.|  
|[\<metadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|Obsahuje nastavení pro zpracování metadat.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Kořenový element všechny konfigurační prvky Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Poznámky  
 `client` Oddíl definuje seznam koncových bodů, které klient může připojit k. Každý koncový bod uvedený v oddílu klienta definuje vlastní vazby, chování a kontrakt. Je jedinečně identifikovaný kombinací `name` a `contract` atributy. Určuje kód klienta `name` pro připojení k koncový bod služby, který implementuje klienta. Pokud `name` atribut vynechán, koncový bod funguje jako výchozí koncový bod pro daný kontrakt se implementuje.  
  
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
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [Konfigurace klienta WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Klienti](../../../../../docs/framework/wcf/feature-details/clients.md)
