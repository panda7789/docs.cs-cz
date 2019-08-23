---
title: <security> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: bdd3b236c9bae198f8027c4ca0c0fa5b70d30342
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936642"
---
# <a name="security-of-peertransport"></a>\<> zabezpečení > \<peerTransport
Obsahuje nastavení zabezpečení související s rovnocenným kanálem, včetně typu použitého ověřování a zabezpečení používaného pro přenos zpráv.  
  
 \<system.serviceModel>  
\<> vazeb  
\<customBinding >  
\<> vazby  
\<peerTransport >  
\<> zabezpečení  
  
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
|`mode`|Určuje typ zabezpečení, který má být použit. Výchozí hodnota je zpráva. Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>mode – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|`None`|Zabezpečení je zakázané.|  
|`Transport`|Zabezpečení je k dispozici pomocí protokolu HTTPS.|  
|`Message`|Zabezpečení SOAP zajišťuje ověřování, integritu a důvěrnost.|  
|`TransportWithMessageCredential`|Protokol HTTPS zajišťuje ověřování a důvěrnost. Zprávy SOAP poskytují bohatě typy přihlašovacích údajů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> přenosu](transport-of-peertransport.md)|Definuje partnerský přenos pro vlastní vazbu. Tento prvek má `clientCredentialType` atribut, který určuje pověření, která mají být použita při interakci se službou. Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.<br /><br /> Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<peerTransport >](peertransport.md)|Definuje partnerský přenos pro vlastní vazbu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Zabezpečení přenosu](../../../wcf/feature-details/transport-security.md)
- [Přenosy](../../../wcf/feature-details/transports.md)
- [Volba přenosu](../../../wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
