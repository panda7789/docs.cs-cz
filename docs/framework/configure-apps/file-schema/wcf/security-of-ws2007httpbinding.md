---
title: <security> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: e88f55f3651d1ccd55631dce13a0349ac2772624
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736386"
---
# <a name="security-of-ws2007httpbinding"></a>\<security> z \<ws2007HttpBinding>
Představuje nastavení zabezpečení používané s [\<ws2007HttpBinding>](ws2007httpbinding.md) prvkem.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`mode`|Volitelné. Určuje typ zabezpečení, který se použije. Výchozí formát je `Message`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.SecurityMode> .|  
  
## <a name="mode-attribute"></a>Mode – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|`None`|Zabezpečení je zakázané.|  
|`Transport`|Zabezpečení je k dispozici pomocí protokolu HTTPS. Služba musí být nakonfigurovaná s certifikáty SSL (Secure Sockets Layer) (SSL). Zpráva je zcela zabezpečená pomocí protokolu HTTPS a služba je ověřena klientem pomocí certifikátu protokolu SSL služby. Ověřování klienta je řízeno `ClientCredentials` atributem [\<transport>](transport-of-ws2007httpbinding.md) elementu.|  
|`Message`|Zabezpečení je k dispozici pomocí protokolu SOAP Message Security. Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané. Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici v klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy prostřednictvím <xref:System.ServiceModel.Security.SecurityMessageProperty> . Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.|  
|`TransportWithMessageCredential`|V tomto režimu poskytuje protokol HTTPS ověření identity, důvěrnosti a ověřování serveru a zabezpečení zpráv SOAP zajišťuje ověřování klientů. Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|Definuje nastavení zabezpečení přenosu. Tento prvek odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu. Tato nastavení se aplikují jenom v případě, že je režim nastavený na přenos.|  
|[\<message>](message-of-ws2007httpbinding.md)|Definuje nastavení zabezpečení zprávy. Tento prvek odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu. Tato nastavení se neaplikují, pokud je režim nastavený na přenos.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|Zabezpečená vazba pro aplikace přenosu HTTP.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek je navržen pro zajištění spolupráce se službami, které implementují specifikace WS-*. Zabezpečení přenosu této vazby je SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP nebo HTTPS.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
