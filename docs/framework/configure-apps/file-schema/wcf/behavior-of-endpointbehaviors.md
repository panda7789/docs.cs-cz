---
title: <behavior> z <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: 34306f99f2343c987700e964aaa9800aa3f488fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673547"
---
# <a name="behavior-of-endpointbehaviors"></a>\<chování > z \<endpointBehaviors >
`behavior` Prvek obsahuje soubor nastavení chování koncového bodu. Každý chování je indexované podle jeho `name`. Koncové body můžete propojit s každou chování prostřednictvím tento název. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
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
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření pro ověření klienta ke službě.|  
|[\<callbackDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/callbackdebug.md)|Určuje ladění služby pro objekt zpětného volání Windows Communication Foundation (WCF).|  
|[\<callbackTimeouts>](../../../../../docs/framework/configure-apps/file-schema/wcf/callbacktimeouts.md)|Určuje časový limit pro zpětné volání klienta.|  
|[\<clientVia>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientvia.md)|Určuje, že by neměl zabrat trasy zprávu.|  
|[\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer.md)|Obsahuje konfigurační data pro objektu DataContractSerializer.|  
|[\<dispatcherSynchronization>](../../../../../docs/framework/configure-apps/file-schema/wcf/dispatchersynchronization.md)|Určuje chování koncového bodu umožňující službě odeslání asynchronních odpovědí.|  
|[\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)|Umožňuje chování koncového bodu, který umožňuje využívat služby z webových stránek ASP.NET AJAX. Chování byste měli použít pouze ve spojení s buď \<webHttpBinding > standardní vazbu, nebo \<webMessageEncoding > element vazby.|  
|[\<endpointDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|Určuje různá nastavení zjišťování pro koncový bod, například jeho rozpoznatelnost, rozsahy a všechny vlastní rozšíření jeho metadat.|  
|[\<soapProcessing>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)|Definuje chování koncového bodu klient použitý k zařazování zpráv mezi jinou vazbou typy a verze zpráv.|  
|[\<synchronousReceive >](../../../../../docs/framework/configure-apps/file-schema/wcf/synchronousreceive-element.md)|Určuje chování za běhu pro příjem zpráv v aplikaci klienta nebo službě. Nemá žádné atributy nebo podřízené prvky.|  
|[\<transactedBatching>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactedbatching.md)|Určuje, zda jsou podporovány dávkové transakce pro operace příjmu.|  
|[\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)|Určuje, WebHttpBehavior koncového bodu prostřednictvím konfigurace. Toto chování při použití ve spojení s \<webHttpBinding > standardní vazbu, umožňuje programovacího modelu webové služby WCF.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpointBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|Kolekce elementů chování koncového bodu.|
