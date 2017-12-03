---
title: "&lt;chování&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f543742ee4d70f64d3bef64be295a7f353c680d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbehaviorsgt"></a>&lt;chování&gt;
Tento element definuje dva podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.  Každá kolekce definuje chování elementy spotřebovávají koncové body a služby. Každý prvek chování je identifikován jeho jedinečné `name` atributu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 \<systém. ServiceModel >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
   </serviceBehaviors>  
   <endpointBehaviors>  
   </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpointBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|Tento konfigurační oddíl představuje všechny chování definované pro konkrétní koncový bod.|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Tento oddíl konfigurace představuje všechny chování, které jsou definovány pro konkrétní službu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Kořenový element všechny konfigurační prvky Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `<remove>` elementu, který chcete odstranit konkrétní chování z kolekce. Uděláte to tak, jednoduše zadejte název požadované chování, odeberte v `name` atribut `<remove>` elementu.  Můžete také `<clear>` element zajistit, že začne kolekci chování prázdný zrušením se veškerý obsah kolekce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [Konfigurace a rozšíření modulu Runtime s chováním](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 [Konfigurace chování klientů](../../../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [Určení chování klienta](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [Určení chování služby](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
