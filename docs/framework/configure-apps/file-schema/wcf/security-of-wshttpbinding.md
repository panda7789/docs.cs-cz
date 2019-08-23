---
title: <security> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: e627a63221d0013c89495d7ff81e02047a03df89
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936510"
---
# <a name="security-of-wshttpbinding"></a>\<> zabezpečení > \<WSHttpBinding
Představuje možnosti [ \<zabezpečení wsHttpBinding >](wshttpbinding.md).  
  
 \<system.ServiceModel>  
\<> vazeb  
\<wsHttpBinding>  
\<> vazby  
\<> zabezpečení  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Volitelné. Určuje typ zabezpečení, který se použije. Výchozí hodnota je `Message`.<br />– Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Mode – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Žádné|Zabezpečení je zakázané.|  
|Přepravu|Zabezpečení je k dispozici pomocí protokolu HTTPS. Služba musí být nakonfigurovaná s certifikáty SSL. Zpráva je zcela zabezpečená pomocí protokolu HTTPS a klient je ověřuje pomocí certifikátu protokolu SSL služby. Ověřování klienta je řízeno pomocí `ClientCredentials` atributu. transportního >. [ \<](transport-of-wshttpbinding.md)|  
|Message|Zabezpečení je k dispozici pomocí protokolu SOAP Message Security. Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané. Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici v klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy prostřednictvím vlastnosti Security. Message. Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.|  
|TransportWithMessageCredential|V tomto režimu poskytuje protokol HTTPS ověření identity, důvěrnosti a ověřování serveru a zabezpečení zpráv SOAP zajišťuje ověřování klientů. Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> přenosu](transport-of-wshttpbinding.md)|Definuje nastavení zabezpečení přenosu. Tento prvek odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.|  
|[\<> zprávy](message-of-wshttpbinding.md)|Definuje nastavení zabezpečení zprávy. Tento prvek odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|Zabezpečená vazba pro aplikace přenosu HTTP.|  
  
## <a name="remarks"></a>Poznámky  
 Třída WSHttpBinding je navržena pro zajištění spolupráce se službami, které implementují specifikace WS-*. Zabezpečení přenosu této vazby je SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP nebo HTTPS.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
