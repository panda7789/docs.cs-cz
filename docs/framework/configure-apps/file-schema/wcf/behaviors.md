---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: a87966f643fe46d0ef69f843dc306151ca7c18bb
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400593"
---
# <a name="behaviors"></a>\<> chování
Tento prvek definuje dvě podřízené kolekce s `endpointBehaviors` názvem `serviceBehaviors`a.  Každá kolekce definuje prvky chování spotřebované koncovými body a službami v uvedeném pořadí. Každý prvek chování je identifikován jeho jedinečné `name` atributu. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<> chování**  
  
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
|[\<endpointBehaviors>](endpointbehaviors.md)|Tento oddíl konfigurace představuje všechna chování definovaná pro konkrétní koncový bod.|  
|[\<serviceBehaviors>](servicebehaviors.md)|Tento oddíl konfigurace představuje všechny chování, které jsou definovány pro konkrétní službu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `<remove>` elementu můžete z kolekce odebrat konkrétní chování. Uděláte to tak, že jednoduše dodáte název chování, které se má odebrat `name` , v atributu `<remove>` elementu.  Můžete také použít `<clear>` element k ujištění, že kolekce chování začne být prázdná vymazáním veškerého obsahu kolekce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Konfigurace a rozšíření modulu runtime pomocí chování](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [Konfigurace chování klienta](../../../wcf/configuring-client-behaviors.md)
- [Nastavení chování klienta za běhu](../../../wcf/specifying-client-run-time-behavior.md)
- [Určování chování služby za běhu](../../../wcf/specifying-service-run-time-behavior.md)
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
