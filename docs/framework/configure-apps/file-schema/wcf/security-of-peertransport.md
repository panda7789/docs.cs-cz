---
title: '&lt;security&gt; – &lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 8b0b8c5f230e8e93c07e13212201896010429af0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585377"
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a>&lt;security&gt; – &lt;peerTransport&gt;
Obsahuje nastavení zabezpečení související s rovnocenným kanálem, zahrnující typ použitého ověřování a zabezpečení pro přenos zpráv.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<peerTransport >  
\<security>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`mode`|Určuje typ zabezpečení má být použita. Výchozí hodnota je zpráva. Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>režim atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`None`|Zabezpečení je zakázaná.|  
|`Transport`|Zabezpečení je k dispozici pomocí protokolu HTTPS.|  
|`Message`|Zabezpečení protokolu SOAP poskytuje ověřování, integritu a důvěrnost.|  
|`TransportWithMessageCredential`|HTTPS zajišťuje ověřování a zachováním důvěrnosti. Zprávy protokolu SOAP poskytuje typy bohaté přihlašovacích údajů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|Definuje rovnocenný přenos pro vlastní vazbu. Tento element nemá `clientCredentialType` atribut, který určuje přihlašovací údaje, které se použije při komunikaci se službou. Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.<br /><br /> Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<peerTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|Definuje rovnocenný přenos pro vlastní vazbu.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Zabezpečení přenosu](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
