---
title: <transport> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3dbeda5d418c30f378515fa83979eaca289370f9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284008"
---
# <a name="transport-of-peertransport"></a>\<přenos > z \<peerTransport >
Určuje typ spojení na zabezpečené zprávy odeslané partnerské uzly, které jsou konfigurovány pomocí této vazby.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<peerTransport >  
\<security>  
\<přenos >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|credentialType|Volitelné. Určuje typ pověření použitá k ověření zprávy odeslané s rovnocenný přenos. Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.|  
  
## <a name="credentialtype-attribute"></a>credentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Certifikát|Ověřování rovnocenný kanál přenos vyžaduje x X509 certifikátu.|  
|Heslo|Ověřování rovnocenný kanál přenos vyžaduje správné heslo.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|Definuje rovnocenný přenos nastavení zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element je nastavena, jen pokud atribut režimu [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) je nastavena na `Transport` nebo `TransportWithMessageCredential`.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Zabezpečení přenosu](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
