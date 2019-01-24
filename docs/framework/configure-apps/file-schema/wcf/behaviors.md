---
title: '&lt;Chování&gt;'
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: a6786efb289ee66da3f0635e1a86e23f9b7302d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528430"
---
# <a name="ltbehaviorsgt"></a>&lt;Chování&gt;
Tento prvek definuje dvě podkolekce s `endpointBehaviors` a `serviceBehaviors`.  Každou kolekci definuje chování elementů používané koncové body a služby. Každý prvek chování je identifikován jeho jedinečné `name` atributu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 \<system.ServiceModel>  
  
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
 Žádná  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpointBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|Tento konfigurační oddíl představuje všechna chování definovaná pro určitý koncový bod.|  
|[\<serviceBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Tento oddíl konfigurace představuje všechny chování, které jsou definovány pro konkrétní službu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `<remove>` prvek, který chcete odebrat konkrétní chování z kolekce. Uděláte to tak, stačí zadat název chování pro odebrání v `name` atribut `<remove>` elementu.  Můžete také použít `<clear>` element – pomáhat zajistit, že kolekce chování začne tím, že zrušíte všechny obsah kolekce prázdný.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Konfigurace a rozšíření modulu runtime pomocí chování](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [Konfigurace chování klienta](../../../../../docs/framework/wcf/configuring-client-behaviors.md)
- [Nastavení chování klienta za běhu](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [Určování chování služby za běhu](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
