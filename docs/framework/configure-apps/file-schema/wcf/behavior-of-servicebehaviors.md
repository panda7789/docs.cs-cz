---
title: <behavior> z <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 115f94fc3f17dc5b4dd1ee3a090f2c9d121f810b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139729"
---
# <a name="behavior-of-servicebehaviors"></a>> \<chování \<serviceBehaviors >
`behavior` Element obsahuje nastavení pro chování služby kolekce. Každý chování je indexované podle jeho `name`. Služby mohou pomocí tohoto názvu propojit s každým chováním pomocí atributu `behaviorConfiguration`\<elementu [koncového bodu >](endpoint-element.md) . To umožňuje koncové body sdílení obvyklé chování konfigurace bez předefinování nastavení. Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!NOTE]
> Prvky chování specifické pro aktivity pracovních postupů systému Windows, jako je například [\<sendMessageChannelCache >](../windows-workflow-foundation/sendmessagechannelcache.md) element, jsou popsány v [\<chování > \<](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) stránky > serviceBehaviors.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[**chování**](behaviors.md)\<
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<chování** >  
  
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
|name|Jedinečný řetězec, který obsahuje název konfigurace chování. Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element. Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<dataContractSerializer >](datacontractserializer-element.md)|Obsahuje konfigurační data pro DataContractSerializer.|  
|[\<persistenceProvider >](persistenceprovider.md)|Určuje typ používané implementace poskytovatele trvalosti a také časový limit pro operace trvalého uložení.|  
|[\<směrování >](routing-of-servicebehavior.md)|Poskytuje přístup ke směrovací službě za běhu, aby umožňoval dynamickou úpravu konfigurace směrování.|  
|[\<serviceAuthenticationManager >](serviceauthenticationmanager.md)|Poskytuje prvek konfigurace pracovního postupu, který na úrovni služby zřídí platnost přenosu, zprávy nebo původce.|  
|[\<serviceAuthorization >](serviceauthorization-element.md)|Určuje nastavení, které autorizují přístup k operacím služby.|  
|[\<serviceCredentials >](servicecredentials.md)|Určuje přihlašovací údaje, které se mají použít při ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.|  
|[\<serviceDebug >](servicedebug.md)|Určuje funkce ladění a informací o nápovědě pro službu Windows Communication Foundation (WCF).|  
|[\<serviceDiscovery >](servicediscovery.md)|Určuje zjistitelnost koncových bodů služby.|  
|[\<oddílu serviceMetadata >](servicemetadata.md)|Určuje publikování metadat služby a přidružených informací.|  
|[\<serviceSecurityAudit >](servicesecurityaudit.md)|Určuje nastavení, které povoluje auditování událostí zabezpečení během operací služby.|  
|[\<serviceThrottling >](servicethrottling.md)|Určuje mechanismus omezování služby WCF.|  
|[\<serviceTimeouts >](servicetimeouts.md)|Určuje časový limit služby.|  
|[\<aktivity typu workflowRuntime >](workflowruntime.md)|Určuje nastavení pro instanci aktivity typu WorkflowRuntime pro hostování služeb WCF založených na pracovních postupech.|  
|[\<useRequestHeadersForMetadataAddress >](userequestheadersformetadataaddress.md)|Umožňuje načtení informací o adrese metadat ze záhlaví zpráv požadavku.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceBehaviors >](servicebehaviors.md)|Kolekce elementů chování služby.|
