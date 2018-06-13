---
title: '&lt;security&gt; – &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b7644e0cf9148cb489618b352ad09901799ceaa6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751087"
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a>&lt;security&gt; – &lt;ws2007HttpBinding&gt;
Představuje nastavení zabezpečení použité s [ \<– ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.  
  
 \<system.serviceModel>  
\<vazby >  
\<ws2007HttpBinding>  
\<Vazba >  
\<zabezpečení >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <ws2007HttpBinding>  
            <binding name = "string">  
              <security mode="None/Message/Transport/TransportWithMessageCredential">  
                  <transport>  
                  </transport>  
                  <message>  
                  </message>  
              </security  
        </ws2007HttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`mode`|-Volitelné. Určuje typ zabezpečení, který se použije. Výchozí hodnota je `Message`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>režim atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`None`|Zabezpečení je vypnuté.|  
|`Transport`|Zabezpečení je k dispozici pomocí protokolu HTTPS. Služba musí být nakonfigurován pomocí certifikátů Secure Sockets Layer (SSL). Zpráva zcela zabezpečené pomocí protokolu HTTPS a službu ověření klienta pomocí certifikátu SSL služby. Ověření klienta je řízen pomocí `ClientCredentials` atribut [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.|  
|`Message`|Zabezpečení je k dispozici pomocí zabezpečení zpráv protokolu SOAP. Ve výchozím nastavení je SOAP body šifrovaný a podepsaný. Tento režim nabízí celou řadu funkcí, např. zda jsou k dispozici na straně klienta vzdálené správy, sada algoritmů, které chcete použít, přihlašovací údaje služby a jakou úroveň ochrany, která platí pro tělo zprávy prostřednictvím <xref:System.ServiceModel.Security.SecurityMessageProperty>. Ověření klienta se provádí jednou pro každou relaci a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.|  
|`TransportWithMessageCredential`|V tomto režimu HTTPS poskytuje integrity, šifrování a ověřování serveru a zabezpečení zpráv protokolu SOAP poskytuje ověření klienta. Ve výchozím nastavení ověření klienta se provádí jednou pro každou relaci a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<přenos >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|Definuje nastavení zabezpečení přenosu. Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu. Tato nastavení se použijí jenom v případě, že režim je nastaven na přenos.|  
|[\<Zpráva >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|Definuje nastavení zabezpečení pro zprávu. Tento element odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu. Tato nastavení se nepoužívají, pokud režim je nastaven na přenos.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Zabezpečené vazby pro aplikace přenos HTTP.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element je určená pro vzájemná spolupráce pomocí služby, které implementují WS-* specifikace. Zabezpečení přenosu pro tuto vazbu Secure Sockets Layer (SSL) je protokol HTTP nebo HTTPS.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
