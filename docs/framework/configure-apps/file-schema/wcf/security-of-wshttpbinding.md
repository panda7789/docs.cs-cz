---
title: "&lt;security&gt; – &lt;wsHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 30f44ad6ce7219ddd874108e62111ff947d7aa0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a>&lt;security&gt; – &lt;wsHttpBinding&gt;
Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 \<systém. ServiceModel >  
\<vazby >  
\<wsHttpBinding >  
\<Vazba >  
\<zabezpečení >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">  
   <transport  
         clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string"   
      defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      defaultRealm="string" />  
   <message  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
       establishSecurityContext="Boolean"   
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|-Volitelné. Určuje typ zabezpečení, který se použije. Výchozí hodnota je `Message`.<br />-Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>režim atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Zabezpečení je vypnuté.|  
|Přenos|Zabezpečení je k dispozici pomocí protokolu HTTPS. Službu je potřeba nakonfigurovat s certifikáty protokolu SSL. Zpráva je zcela zabezpečené pomocí protokolu HTTPS a ověření klienta pomocí certifikátu SSL služby. Ověření klienta je řízen pomocí `ClientCredentials` atribut. z [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).|  
|Zpráva|Zabezpečení je k dispozici pomocí zabezpečení zpráv protokolu SOAP. Ve výchozím nastavení těla protokolu SOAP je zašifrovaná a podepsaná. Tento režim nabízí celou řadu funkcí, např. zda jsou k dispozici na straně klienta vzdálené správy, sada algoritmů, které chcete použít, přihlašovací údaje služby a jakou úroveň ochrany, která platí pro tělo zprávy prostřednictvím vlastnosti Security.Message. Ověření klienta se provádí jednou za relace a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.|  
|TransportWithMessageCredential|V tomto režimu HTTPS poskytuje integrity, šifrování a ověřování serveru a zabezpečení zpráv protokolu SOAP poskytuje ověření klienta. Ve výchozím nastavení ověření klienta se provádí jednou za relace a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<přenos >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|Definuje nastavení zabezpečení přenosu. Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.|  
|[\<Zpráva >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|Definuje nastavení zabezpečení pro zprávu. Tento element odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Zabezpečené vazby pro aplikace přenos HTTP.|  
  
## <a name="remarks"></a>Poznámky  
 Třída WSHttpBinding je navržena pro vzájemná spolupráce pomocí služby, které implementují WS-* specifikace. Zabezpečení přenosu pro tuto vazbu Secure Sockets Layer (SSL) je protokol HTTP nebo HTTPS.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
