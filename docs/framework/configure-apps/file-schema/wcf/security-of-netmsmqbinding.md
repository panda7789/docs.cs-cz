---
title: <security> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1bbc3a460ce707e71b72a469af2e03acd8dc79e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936688"
---
# <a name="security-of-netmsmqbinding"></a>\<> zabezpečení > \<NetMsmqBinding
Definuje nastavení zabezpečení pro vazbu služby MSMQ. Určuje, zda je povoleno přenosu nebo zabezpečení SOAP, a pokud ano, jaký režim ověřování a úrovně ochrany se používají.  
  
 \<system.ServiceModel>  
\<> vazeb  
\<netMsmqBinding>  
\<> vazby  
\<> zabezpečení  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Určuje typ zabezpečení, který řídí integritu, důvěrnost a ověřování. Platné hodnoty jsou následující:<br /><br /> NTato Tím se zakáže zabezpečení.<br />Přepravu Přenos nabízí ochranu a ověřování. To platí pro zabezpečení zpráv mezi dvěma správci fronty. Mezi aplikací a správcem front se nenabízí žádné zabezpečení. Stávající aplikace služby MSMQ jsou funkčně ekvivalentní s tímto typem režimu zabezpečení.<br />Zpráva Určuje zabezpečení aplikací koncového konce. V transportní vrstvě není nabízené žádné zabezpečení. To se podobá zabezpečení nabízené jinými standardními vazbami.<br />Protokoly Nabízí zabezpečení jak na úrovni přenosu, tak i ve vrstvě zpráv SOAP. Stejné přihlašovací údaje se vyžadují na obou úrovních.<br /><br /> Výchozí hodnota je Transport. Tento atribut je typu <xref:System.ServiceModel.NetMsmqSecurityMode>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> zprávy](message-of-netmsmqbinding.md)|Definuje nastavení zabezpečení zprávy protokolu SOAP. Tento prvek je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.|  
|[\<> přenosu](transport-of-netmsmqbinding.md)|Definuje nastavení zabezpečení pro přenos služby MSMQ. Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|vazba|Prvek vazby [> \<NetMsmqBinding](netmsmqbinding.md)|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
- [Fronty ve WCF](../../../wcf/feature-details/queues-in-wcf.md)
