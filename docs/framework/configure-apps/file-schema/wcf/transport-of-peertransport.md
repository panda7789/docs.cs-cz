---
title: <transport> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 5dbc55db25c0c49d72ec2cd8dd1041a3f8705d8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940637"
---
# <a name="transport-of-peertransport"></a>\<> přenosu > \<peerTransport
Určuje typ přenosu zabezpečených zpráv odesílaných partnerskými uzly nakonfigurovanými pomocí této vazby.  
  
 \<system.serviceModel>  
\<> vazeb  
\<customBinding >  
\<> vazby  
\<peerTransport >  
\<> zabezpečení  
\<> přenosu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|credentialType|Volitelný parametr. Určuje typ přihlašovacích údajů, které se používají k ověření zpráv odesílaných pomocí partnerského přenosu. Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.|  
  
## <a name="credentialtype-attribute"></a>credentialType – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Certifikát|Ověřování přenosu rovnocenného kanálu vyžaduje certifikát x509.|  
|Heslo|Ověření přenosu rovnocenného kanálu vyžaduje správné heslo.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> zabezpečení](security-of-peertransport.md)|Definuje nastavení zabezpečení pro partnerský přenos.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek je nastaven pouze v případě, že je atribut `Transport` `TransportWithMessageCredential` [ \<Mode > zabezpečení](security-of-peertransport.md) nastaven na nebo.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Zabezpečení přenosu](../../../wcf/feature-details/transport-security.md)
- [Přenosy](../../../wcf/feature-details/transports.md)
- [Volba přenosu](../../../wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
