---
title: <behavior> z <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: a17fac5c519f41588ef90383f024e645b809b49b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400611"
---
# <a name="behavior-of-servicebehaviors"></a>\<chování > \<serviceBehaviors >
`behavior` Element obsahuje nastavení pro chování služby kolekce. Každý chování je indexované podle jeho `name`. Služby se můžou propojit s každým chováním prostřednictvím tohoto názvu `behaviorConfiguration` pomocí atributu [ \<> elementu koncového bodu](endpoint-element.md) . To umožňuje koncové body sdílení obvyklé chování konfigurace bez předefinování nastavení. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!NOTE]
> Prvky chování specifické pro aktivity pracovních postupů systému Windows, jako [ \<](../windows-workflow-foundation/sendmessagechannelcache.md) je například prvek sendMessageChannelCache >, jsou popsány v [ \< \<části chování > stránky > serviceBehaviors](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) .  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> chování**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Jedinečný řetězec, který obsahuje název konfigurace chování. Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|Obsahuje konfigurační data pro DataContractSerializer.|  
|[\<persistenceProvider >](persistenceprovider.md)|Určuje typ používané implementace poskytovatele trvalosti a také časový limit pro operace trvalého uložení.|  
|[\<> směrování](routing-of-servicebehavior.md)|Poskytuje přístup ke směrovací službě za běhu, aby umožňoval dynamickou úpravu konfigurace směrování.|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|Poskytuje prvek konfigurace pracovního postupu, který na úrovni služby zřídí platnost přenosu, zprávy nebo původce.|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|Určuje nastavení, které autorizují přístup k operacím služby.|  
|[\<serviceCredentials>](servicecredentials.md)|Určuje přihlašovací údaje, které se mají použít při ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.|  
|[\<serviceDebug>](servicedebug.md)|Určuje funkce ladění a informací o nápovědě pro službu Windows Communication Foundation (WCF).|  
|[\<serviceDiscovery>](servicediscovery.md)|Určuje zjistitelnost koncových bodů služby.|  
|[\<serviceMetadata>](servicemetadata.md)|Určuje publikování metadat služby a přidružených informací.|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|Určuje nastavení, které povoluje auditování událostí zabezpečení během operací služby.|  
|[\<serviceThrottling>](servicethrottling.md)|Určuje mechanismus omezování služby WCF.|  
|[\<serviceTimeouts>](servicetimeouts.md)|Určuje časový limit služby.|  
|[\<workflowRuntime>](workflowruntime.md)|Určuje nastavení pro instanci aktivity typu WorkflowRuntime pro hostování služeb WCF založených na pracovních postupech.|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|Umožňuje načtení informací o adrese metadat ze záhlaví zpráv požadavku.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|Kolekce elementů chování služby.|
