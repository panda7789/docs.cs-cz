---
title: <peer> z <clientCredentials> – Element
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 8970100b1ad3019ff4a639d835d1db1430968008
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275138"
---
# <a name="peer-of-clientcredentials-element"></a>\<sdílené > z \<clientCredentials > – Element
Určuje pověření používaný při ověřování klientů peer-to-peer.  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
\<clientCredentials>  
\<peer>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|Určuje certifikát X.509, který chcete použít pro podepisování a šifrování zpráv klientů peer-to-peer. .|  
|[\<peerAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|Určuje možnosti ověřování pro klienty sdílené.|  
|[\<messageSenderAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|Určuje možnosti ověřování pro odesílatele zpráv.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření pro ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace určuje přihlašovací údaje, které partnerský uzel používá ke svému ověření do jiných uzlů v mřížce, jakož i nastavení ověřování, které partnerský uzel používá k ověřování další partnerské uzly. Další informace najdete v tématu [ověřování zpráv Peer Channel](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) a [zabezpečení aplikace Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [Síť rovnocenných počítačů](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)
- [Ověřování zpráv protokolu peer Channel](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)
- [Vlastní ověřování protokolu peer Channel](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)
- [Zabezpečení aplikací protokolu Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
