---
title: '&lt;peer&gt; elementu &lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3479b52c6e06b7b9ebd69d46780e8dca70d2ef7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a>&lt;peer&gt; elementu &lt;clientCredentials&gt;
Určuje pověření použitá při ověřování klientů peer-to-peer.  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<clientCredentials>  
\<sdílené >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<certifikátu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|Určuje certifikát X.509, který chcete použít pro podepisování a šifrování zpráv pro klienty peer-to-peer. .|  
|[\<peerAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|Určuje možnosti ověřování pro klienty sdílené.|  
|[\<messageSenderAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|Určuje možnosti ověřování pro odesílatelé zpráv.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření použitá k ověření klienta pro službu.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element konfigurace Určuje pověření, které používá sdílené uzlu ke svému ověření do dalších uzlů v mřížce, jakož i nastavení ověřování, které uzlem sdílené používá k ověření dalších partnerské uzly. Další informace najdete v tématu [ověřování zpráv kanál sdílené](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) a [zabezpečení aplikací kanálu sdílené](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [Síť rovnocenných počítačů](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)  
 [Ověřování zpráv rovnocenného kanálu](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Vlastní ověřování rovnocenného kanálu](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpečení aplikací protokolu Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
