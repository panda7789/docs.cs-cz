---
title: <security> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399767"
---
# <a name="security-of-peertransport"></a>\<security> z \<peerTransport>
Obsahuje nastavení zabezpečení související s rovnocenným kanálem, včetně typu použitého ověřování a zabezpečení používaného pro přenos zpráv.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
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
|`mode`|Určuje typ zabezpečení, který má být použit. Výchozí hodnota je zpráva. Tento atribut je typu <xref:System.ServiceModel.SecurityMode> .|  
  
## <a name="mode-attribute"></a>mode – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|`None`|Zabezpečení je zakázané.|  
|`Transport`|Zabezpečení je k dispozici pomocí protokolu HTTPS.|  
|`Message`|Zabezpečení SOAP zajišťuje ověřování, integritu a důvěrnost.|  
|`TransportWithMessageCredential`|Protokol HTTPS zajišťuje ověřování a důvěrnost. Zprávy SOAP poskytují bohatě typy přihlašovacích údajů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|Definuje partnerský přenos pro vlastní vazbu. Tento prvek má `clientCredentialType` atribut, který určuje pověření, která mají být použita při interakci se službou. Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType> .<br /><br /> Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|Definuje partnerský přenos pro vlastní vazbu.|  
  
## <a name="see-also"></a>Viz také

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
