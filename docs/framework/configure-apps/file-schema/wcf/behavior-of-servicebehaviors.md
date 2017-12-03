---
title: "&lt;behavior&gt; – &lt;serviceBehaviors&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78c912886b5a39fad361994a0aaa302491e71f2d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt"></a>&lt;behavior&gt; – &lt;serviceBehaviors&gt;
`behavior` Element obsahuje nastavení pro chování služby kolekce. Každý chování je indexované podle jeho `name`. Služby můžete propojit každý chování pomocí této konfigurace pomocí názvu `behaviorConfiguration` atribut [ \<endpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element. To umožňuje koncové body sdílení obvyklé chování konfigurace bez předefinování nastavení. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!NOTE]
>  Chování elementy, které jsou specifické pro aktivity pracovního postupu systému Windows, například [ \<sendMessageChannelCache >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md) elementu, jsou dokumentovány v článku [ \<chování > z \< serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) stránky.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
  
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
|name|Jedinečný řetězec, který obsahuje název konfigurace chování. Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)|Obsahuje konfigurační data pro objektu DataContractSerializer.|  
|[\<persistenceProvider >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistenceprovider.md)|Určuje typ implementace trvalost zprostředkovatele použít, jakož i časový limit používat pro operace trvalost.|  
|[\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|Poskytuje běhové přístup ke službě Směrování a povolit dynamické změnu konfigurace směrování.|  
|[\<serviceAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthenticationmanager.md)|Poskytuje prvek konfigurace pracovního postupu, který stanoví platnosti přenosu, původce nebo zpráv na úrovni služby...|  
|[\<serviceAuthorization >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)|Určuje nastavení, které zajistí autorizaci přístupu k operacím služby.|  
|[\<– serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Určuje pověření, která se použije v ověřování služby a nastavení související s ověření pověření klienta.|  
|[\<serviceDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)|Určuje funkce informace o ladění a nápovědu pro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby.|  
|[\<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)|Určuje možnosti rozpoznání koncových bodů služby.|  
|[\<serviceMetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)|Určuje publikování metadat služby a související informace.|  
|[\<serviceSecurityAudit >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)|Určuje nastavení, které povolení auditování událostí zabezpečení během operací služby.|  
|[\<serviceThrottling >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)|Určuje omezení mechanismus [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby.|  
|[\<serviceTimeouts >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicetimeouts.md)|Určuje časový limit pro službu.|  
|[\<modul runtime pracovního postupu >](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|Určuje nastavení pro instanci modul runtime pracovního postupu pro hostování založené na pracovním postupu [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby.|  
|[\<useRequestHeadersForMetadataAddress >](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|Umožňuje načítání informací o adresu metadat ze záhlaví zprávy požadavku.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Kolekce elementů chování služby.|
