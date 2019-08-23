---
title: <security> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: a895df027bee7430e51e76c480136a49b6b2a0be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936578"
---
# <a name="security-of-ws2007httpbinding"></a>\<> zabezpečení > \<WS2007HttpBinding
Představuje nastavení zabezpečení používané s [ \<prvkem WS2007HttpBinding >](ws2007httpbinding.md) .  
  
 \<system.serviceModel>  
\<> vazeb  
\<ws2007HttpBinding>  
\<> vazby  
\<> zabezpečení  
  
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
|`mode`|Volitelné. Určuje typ zabezpečení, který se použije. Výchozí hodnota je `Message`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Mode – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|`None`|Zabezpečení je zakázané.|  
|`Transport`|Zabezpečení je k dispozici pomocí protokolu HTTPS. Služba musí být nakonfigurovaná s certifikáty SSL (Secure Sockets Layer) (SSL). Zpráva je zcela zabezpečená pomocí protokolu HTTPS a služba je ověřena klientem pomocí certifikátu protokolu SSL služby. Ověřování klienta je řízeno pomocí `ClientCredentials` atributu [ \<> elementu transportu](transport-of-ws2007httpbinding.md) .|  
|`Message`|Zabezpečení je k dispozici pomocí protokolu SOAP Message Security. Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané. Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici v klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy <xref:System.ServiceModel.Security.SecurityMessageProperty>prostřednictvím. Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.|  
|`TransportWithMessageCredential`|V tomto režimu poskytuje protokol HTTPS ověření identity, důvěrnosti a ověřování serveru a zabezpečení zpráv SOAP zajišťuje ověřování klientů. Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> přenosu](transport-of-ws2007httpbinding.md)|Definuje nastavení zabezpečení přenosu. Tento prvek odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu. Tato nastavení se aplikují jenom v případě, že je režim nastavený na přenos.|  
|[\<> zprávy](message-of-ws2007httpbinding.md)|Definuje nastavení zabezpečení zprávy. Tento prvek odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu. Tato nastavení se neaplikují, pokud je režim nastavený na přenos.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|Zabezpečená vazba pro aplikace přenosu HTTP.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek je navržen pro zajištění spolupráce se službami, které implementují specifikace WS-*. Zabezpečení přenosu této vazby je SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP nebo HTTPS.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
