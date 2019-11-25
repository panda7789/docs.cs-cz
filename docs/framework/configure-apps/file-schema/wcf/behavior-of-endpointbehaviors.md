---
title: <behavior> z <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: 489678a5adeae3965acae90a847c4b087478354d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140808"
---
# <a name="behavior-of-endpointbehaviors"></a>> \<chování \<endpointBehaviors >
Element `behavior` obsahuje kolekci nastavení chování koncového bodu. Každý chování je indexované podle jeho `name`. Koncové body se můžou propojit s každým chováním prostřednictvím tohoto názvu. Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[**chování**](behaviors.md)\<
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<chování** >  
  
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
|name|Jedinečný řetězec, který obsahuje název konfigurace chování. Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element. Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials >](clientcredentials.md)|Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.|  
|[\<callbackDebug >](callbackdebug.md)|Určuje ladění služby pro objekt zpětného volání služby Windows Communication Foundation (WCF).|  
|[\<callbackTimeouts >](callbacktimeouts.md)|Určuje časový limit zpětného volání klienta.|  
|[\<clientVia >](clientvia.md)|Určuje trasu, kterou by měla zpráva trvat.|  
|[\<dataContractSerializer >](datacontractserializer.md)|Obsahuje konfigurační data pro DataContractSerializer.|  
|[\<dispatcherSynchronization >](dispatchersynchronization.md)|Určuje chování koncového bodu, které umožňuje službě odesílat odpovědi asynchronně.|  
|[\<enableWebScript >](enablewebscript.md)|Umožňuje chování koncového bodu, které umožňuje využívat službu z webových stránek ASP.NET AJAX. Chování by mělo být použito pouze ve spojení s \<webHttpBinding > standardní vazbou nebo prvkem vazby \<webMessageEncoding >.|  
|[\<endpointDiscovery >](endpointdiscovery.md)|Určuje různá nastavení zjišťování pro koncový bod, například jeho zjistitelnost, obory a jakákoli vlastní rozšíření pro jeho metadata.|  
|[\<soapProcessing >](soapprocessing.md)|Definuje chování koncového bodu klienta používaného k zařazování zpráv mezi různými typy vazeb a verzemi zpráv.|  
|[\<synchronousReceive >](synchronousreceive-element.md)|Určuje chování za běhu pro příjem zpráv v klientské aplikaci nebo službě. Neobsahuje žádné atributy ani podřízené elementy.|  
|[\<transactedBatching >](transactedbatching.md)|Určuje, zda je pro operace Receive podporována dávkování transakcí.|  
|[\<> protokolu WebHttp](webhttp.md)|Určuje WebHttpBehavior na koncovém bodu prostřednictvím konfigurace. Toto chování, při použití ve spojení s \<webHttpBinding > standardní vazbou, povoluje webový programovací model pro službu WCF.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpointBehaviors >](endpointbehaviors.md)|Kolekce elementů chování koncového bodu.|
