---
title: <security> z <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: f84f6c0f9988dd2d07377bf694286922db9d8364
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936806"
---
# <a name="security-of-basichttpbinding"></a>\<> zabezpečení > \<BasicHttpBinding
Definuje možnosti [ \<zabezpečení BasicHttpBinding >](basichttpbinding.md).  
  
 \<system.ServiceModel>  
\<> vazeb  
\<basicHttpBinding>  
\<> vazby  
\<> zabezpečení  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Volitelný parametr. Určuje typ zabezpečení, který se použije. Výchozí hodnota je `None`. Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>mode – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Žádné|– Zprávy nejsou během přenosu zabezpečeny.|  
|Přepravu|Zabezpečení je zajištěno pomocí přenosu HTTPS. Zprávy SOAP jsou zabezpečeny pomocí protokolu HTTPS. Služba se ověřuje pro klienta pomocí certifikátu X. 509 služby. Klient se ověřuje pomocí dodaného ClientCredentialType. Přečtěte si [> přenosů.\<](transport-of-basichttpbinding.md)|  
|Message|Zabezpečení je k dispozici pomocí protokolu SOAP Message Security. Ve výchozím nastavení je text zašifrovaný a podepsaný. Pro tuto vazbu systému vyžaduje, aby byl certifikát serveru poskytnutý klientovi mimo IP síť. Tato vazba je `ClientCredentialType` `Certificate`platná pouze pro tuto vazbu.|  
|TransportWithMessageCredential|Zabezpečení přenosu zajišťuje integrita, důvěrnost a ověřování serveru. Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP. Tento režim je vhodný v případě, že se uživatel ověřuje pomocí uživatelského jména a hesla a existuje stávající nasazení HTTP pro zabezpečení přenosu zpráv.|  
|TransportCredentialOnly|Tento režim neposkytuje integritu a důvěrnost zpráv. Poskytuje ověřování klientů založené na protokolu HTTP. Tento režim by se měl používat opatrně. Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> přenosu](transport-of-basichttpbinding.md)|Definuje nastavení zabezpečení přenosu pro základní službu HTTP. Tento prvek odpovídá <xref:System.ServiceModel.HttpTransportSecurity>.|  
|[\<> zprávy](message-of-basichttpbinding.md)|Definuje nastavení zabezpečení zpráv pro základní službu HTTP. Tento prvek odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|vazba|[ Prvek\<vazby > BasicHttpBinding](basichttpbinding.md).|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení není zpráva SOAP zabezpečená a klient není ověřen. Tento prvek umožňuje nakonfigurovat další nastavení zabezpečení pro `basicHttpBinding` element.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Výběr typu přihlašovacích údajů](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
