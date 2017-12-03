---
title: "&lt;behavior&gt; – &lt;endpointBehaviors&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bf292c88fa98e4e36127f766bdd4edb693137e59
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbehaviorgt-of-ltendpointbehaviorsgt"></a>&lt;behavior&gt; – &lt;endpointBehaviors&gt;
`behavior` Element obsahuje kolekce nastavení pro chování koncový bod. Každý chování je indexované podle jeho `name`. Koncové body můžete propojit každý chování prostřednictvím tento název. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 \<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <endpointBehaviors>  
       <behavior name="String" />  
    </endpointBehaviors>  
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
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření, která používá k ověření klienta ke službě.|  
|[\<callbackDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/callbackdebug.md)|Určuje služby ladění pro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] objekt zpětného volání.|  
|[\<callbackTimeouts >](../../../../../docs/framework/configure-apps/file-schema/wcf/callbacktimeouts.md)|Určuje časový limit pro zpětné volání klienta.|  
|[\<clientVia >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientvia.md)|Určuje, že by neměl zabrat trasy zprávu.|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer.md)|Obsahuje konfigurační data pro objektu DataContractSerializer.|  
|[\<dispatcherSynchronization >](../../../../../docs/framework/configure-apps/file-schema/wcf/dispatchersynchronization.md)|Určuje chování koncového bodu, umožňující službu pro odeslání odpovědi asynchronně.|  
|[\<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)|Umožňuje chování koncového bodu, který vám umožní využívat službu z webových stránek ASP.NET AJAX. Chování musí být použit pouze ve spojení s buď \<webHttpBinding > standardní vazba, nebo \<webMessageEncoding > prvku vazby.|  
|[\<endpointDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|Určuje různé zjišťování nastavení pro koncový bod, například jeho možnosti rozpoznání, obory a vlastní rozšíření jeho metadata.|  
|[\<soapProcessing >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)|Definuje chování klienta endpoint použitý k zařazování zprávy mezi jinou vazbou typy a verze zprávy.|  
|[\<synchronousReceive >](../../../../../docs/framework/configure-apps/file-schema/wcf/synchronousreceive-element.md)|Určuje chování pro příjem zpráv v aplikaci služby nebo klienta. Nástroj nemá žádné atributy nebo podřízené elementy.|  
|[\<transactedBatching >](../../../../../docs/framework/configure-apps/file-schema/wcf/transactedbatching.md)|Určuje, zda je podporováno dávkové zpracování transakcí, pro operace příjmu.|  
|[\<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)|Určuje WebHttpBehavior v koncovém bodě prostřednictvím konfigurace. Toto chování, pokud se používá ve spojení s \<webHttpBinding > standardní vazby umožňuje programovací model webových pro [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpointBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|Kolekci elementů chování koncový bod.|
